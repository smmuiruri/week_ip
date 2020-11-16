# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "geerlingguy/ubuntu2004"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :virtualbox do |v|
    v.memory = 2048
  end

  # Mongodb 
  config.vm.define "mongodb" do |db|
    db.vm.hostname = "mongodb"
    db.vm.network :private_network, ip: "192.168.47.4"
  end

  # Frontend 
  config.vm.define "client" do |app|
    app.vm.hostname = "fontend"
    app.vm.network :private_network, ip: "192.168.47.5"
  end

  # Backend 
  config.vm.define "backend" do |app|
    app.vm.hostname = "backend"
    app.vm.network :private_network, ip: "192.168.47.6"
  end

  # Ansible provisioner.
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
