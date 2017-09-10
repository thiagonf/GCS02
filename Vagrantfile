Vagrant.configure(2) do |config|

  config.vm.synced_folder ".", "/vagrant"

  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/trusty64"
    db.vm.network "forwarded_port", guest: 5432, host: 5432
    db.vm.network "private_network", ip: "192.168.2.11"
    
    db.vm.provider "virtualbox" do |vb|
      vb.name = "dj-database"
      vb.memory = "512"
      vb.cpus = 1
      vb.gui = false
    end

    db.vm.provision "shell", path: "db.sh"
  
  end

  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/trusty64"
    web.vm.network "forwarded_port", guest: 8000, host: 8000
    web.vm.network "private_network", ip: "192.168.2.10"
    
    web.vm.provider "virtualbox" do |vb1|
      vb1.name = "dj"
      vb1.memory = "512"
      vb1.cpus = 1
      vb1.gui = false
    end

    web.vm.provision "shell", path: "web.sh"
      
  end

end