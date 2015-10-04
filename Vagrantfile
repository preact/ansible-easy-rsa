# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "fgrehm/trusty64-lxc"

  config.vm.provider "virtualbox" do |virtualbox, override|
    override.vm.box = "ubuntu/trusty64"

    virtualbox.memory = 8096
    virtualbox.cpus = 4
    virtualbox.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.ssh.forward_agent = true

  config.vm.network "private_network", ip: '10.0.3.10', lxc__bridge_name: '10.0.3.10'

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "test/playbook.yml"
  end
end
