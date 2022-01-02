# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant_API_Version="2"

Vagrant.configure(Vagrant_API_Version) do |config|
  config.vm.define:"ansible-server" do |cfg|
    cfg.vm.box = "centos/7"
    cfg.vm.provider:virtualbox do |vb|
      vb.name = "Ansible-server(Udemy-Bloter)"
    end
    cfg.vm.host_name = "ansible-server"
    cfg.vm.synced_folder ".", "/vagrant", disabled: true
    cfg.vm.network "public_network", ip: "192.168.35.10"
    cfg.vm.network "forwarded_port", guest: 22, host: 19210, auto_correct: false, id: "ssh"
    cfg.vm.provision "shell", path: "bootstrap.sh"
    cfg.vm.provision "file", source: "Ansible_env_ready.yml", destination: "Ansible_env_ready.yml"
    cfg.vm.provision "shell", inline: "ansible-playbook Ansible_env_ready.yml"
  end

end
