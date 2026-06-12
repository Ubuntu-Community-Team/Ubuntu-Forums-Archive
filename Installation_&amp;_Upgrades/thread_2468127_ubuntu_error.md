---
title: "ubuntu error"
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by 3lnyn0 on 2021-10-19
**i try to install eve-ng with google cloud, i followed the steps from documentation. After i reboot linux machine, I open a terminal with ssh again and I can't see the setup from eve-ng it returns me to the linux machine.**


    5. Run The Installation Script 
    Once your VM is provisioned it will automatically be started. Use the built-in SSH feature to connect to the VM&#8217;s console.
    Once you&#8217;re SSH&#8217;d into the VM become root, grab the installation script, update the package manager and upgrade current packages.
    sudo -i
    wget -O - [http://www.eve-ng.net/repo/install-eve.sh](http://www.eve-ng.net/repo/install-eve.sh) | bash -i
    apt update
    apt upgrade
    Reboot the VM.

[B]HERE IS MY PROBLEM, at 6th step, this setup does not open, is there any command I can open it from cli? something like "open eve" or other ideas? 
[/B]
    6. Run The Setup Wizard Connect to it again via the built in SSH. You will be presented with a configuration wizard. 
     STOP! When you are greeted with the wizard to enter a root password, don&#8217;t! Hold CTRL and press C, become root sudo -i This will restart the wizard and allow you to change root&#8217;s password. 
     Follow the initial configuration wizard. 
     Enter Root Password: Enter Root Password Again: Hostname: anything you want (I leave default) DNS Domain Name: anything you want (I leave default) DHCP/Static IP: Choose DHCP/Static NTP: (leave empty) Proxy: Choose &#8220;Direct connection&#8221; After hitting enter, the setup wizard will kick you out.[COLOR=#232629][FONT=-apple-system]i try to install eve-ng with google cloud, i followed the steps from documentation. 

**After i reboot linux machine, I open a terminal with ssh again and I can't see the setup from eve-ng it returns me to the linux machine.**[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-10-22
You are trying to do eve-ng on GCP with an Ubuntu VM nested virtualization...

What may help you and be more visual to what you are trying to do is this: [https://www.youtube.com/watch?v=zZKEa1VAM64](https://www.youtube.com/watch?v=zZKEa1VAM64)

The important part for you comes right after timestamp 7:45. Where you set the protocols, ports, and assign your public IP address. You need to know what your IP address "is" for the VM you are creating. If you do not know/remember your IP address of the VM you create, how are you going to address it, whether via shh or anything else?

I think this is the piece you are having troubles with.

---

