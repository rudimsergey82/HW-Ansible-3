# Vagrantfile for Ansible-2
Vagrant.configure("2") do |config|
  vm_box = "bento/ubuntu-18.04"
  
  config.vm.define "app" do |app|
    app.vm.box = vm_box
    app.vm.hostname = 'ubuntu-app'
    app.vm.network "private_network", ip: "192.168.10.121"
    app.vm.synced_folder '.', '/vagrant', disabled: true
    app.vm.provider "virtualbox" do |app|
      app.gui = false
      app.memory = "1000"
    end
  end

  config.vm.define "db" do |db|
    db.vm.box = vm_box
    db.vm.hostname = 'ubuntu-db'
    db.vm.network "private_network", ip: "192.168.10.122"
    db.vm.synced_folder '.', '/vagrant', disabled: true
    db.vm.provider "virtualbox" do |db|
      db.gui = false
      db.memory = "1000"
    end
  end

  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/key.pub"
  config.vm.provision "shell", inline: "cat /home/vagrant/.ssh/key.pub >> /home/vagrant/.ssh/authorized_keys"
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y python
    #apt-get upgrade -y
  SHELL

end
