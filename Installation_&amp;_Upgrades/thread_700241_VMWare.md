---
title: "VMWare"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2008-02-18
I'm a new Ubuntu user.  I have been using CentOS but a machine crash led me to buy a new Dell and I'm now running Ubuntu on it but I hope to salvage some of the VMs from the drive.

On my previous machine I had a licensed copy of VMWare installed.  I notice, too, that Ubuntu lists VMWare as one of its software applications.

I thought it would be a simple manner to access my vmware account, download VMWare again (they let authorized users do that) and have it on Ubuntu.

But the only options are an .rpm or a tarball.  Since Ubuntu lists VMWare as a partner, is there any recommended way to install from the rpm?  I tried with alien but I think this is one of those apps that alien doesn't handle correctly.  

Can anyone point me in the right direction here?

---

### Post by justleen on 2008-02-18
im not sure wether it is in the repositories.
start the package manager, and check if all repositories are enable. reload the list, and search for VMware.

If not, your best option is to build it from source, instead of trying to get the rpm working..

---

### Post by stevecoh1 on 2008-02-18
It won't be in the repositories, it's a proprietary product but it's a proprietary product Ubuntu is proud to list as a partner.  So I'm thinking there must be some way to activate it. 

Unless, the partnership is one-way?  That is Ubuntu can be a client OS running within VMWare but there's no way for Ubuntu to be a host OS for VMWare?  Is that it?  RedHat can be either a host or a client OS of VMWare but Ubuntu might not.  Can someone clarify?

---

### Post by the1417 on 2008-02-19
better install from tarrball. from my experience, its alot easier when install in feisty than gutsy. in gutsy i cant properly install it. yes.. the vmware in ubuntu menu, but just like that. it cant be launch. same problem when i install crossover. it say install succesfull but theres non in the ubuntu menu.

---

### Post by zvacet on 2008-02-19
If you want to install from tar ball read [this.](http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10) if you want to install from synaptic 

```
gsudo gedit /etc/apt/sources.list
```

add this line

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

Save and close file.

```
sudo apt-get update
```

Go to the synaptic and install all packages related to vmware-server.

---

### Post by jatan on 2008-02-19
enable third party repositories through system-software sources.
Reload your synaptic
Type in vmware server as your search term.
Intstall vmware-server (the first three packages)
it is a 80 mb download. After downloading it will ask for your serial.

Please note the server download is of licensed or freware is what you will have to find out.
i was able to run windows and fedora through the freeware itself

---

### Post by stevecoh1 on 2008-02-19
Thanks guys - but wait.

I should have explained I'm interested in VMWare workstation, not VMWare server.  Would that make a difference to the general approaches you're advocating here?

---

### Post by zvacet on 2008-02-20
You can do it both ways(tar ball or synaptic).If you install vmware-server from synaptic and you payed for worstation they will let you upgrade from server to workstation.Second option is download and install from tar ball.

---

### Post by stevecoh1 on 2008-02-20
Guess I need to find out what VMWare server is.  I've always used Workstation and figured that Server must be a more expensive product but it sounds like from what you're saying that this is not the case.

And I'm a newbie to Ubuntu (but a longtime Redhat user).  What's synaptic?

---

