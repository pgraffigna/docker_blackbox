ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
IMAGEN = "generic/ubuntu2004"
HOSTNAME = "monitor"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", type: "rsync", disabled: false

  config.vm.define :server do |s|
    s.vm.box = IMAGEN
    s.vm.hostname = HOSTNAME
    s.vm.box_check_update = false
    s.vm.provision :docker
    s.vm.provision :docker_compose

    s.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end
end
