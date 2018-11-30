#
#   - creates VM based on bento/ubuntu18 and installs Apache on it
#   - runs VM on the host-based network in a Virtualbox
#   - you should not create any host-based network adapters on Virtualbox
#   - use Guest ip in the default host-based network of Virtualbox: 192.168.50/24
#   - assign name to ip conversion in the Host's /etc/hosts, eg:
#
#           guest   192.168.50.2
#


Vagrant.configure("2") do |config|

  config.vm.define "web", primary: true do |web|
    web.vm.box = "bento/ubuntu-18.04"
    web.vm.box_check_update = false

    web.vm.hostname = "web"
    web.vm.network "private_network", ip: "192.168.50.4"

    web.vm.provider "virtualbox" do |vb|
        vb.name = "web.apache"
        vb.memory = "1024"
        vb.cpus = "2"
    end

    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "provision/site.yml"
      ansible.verbose = true
    end
  end

end
