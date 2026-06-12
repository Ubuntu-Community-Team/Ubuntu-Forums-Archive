---
title: "Minimal install for VM"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by Mk32 on 2013-06-11
Hi, 

I'm looking to build a micro-minimal install (command line only) of some flavor of Ubuntu/Debian based distro for VM use. 

The idea is to have it less than 200MB for the .vdi VirtualBox Disk Image. All it would do is run Netatalk to share a folder out to the network using a VM, but the Home Directory and a named share on the host machine's hard drive. 

So no desktop environment, utilities, nothing, except a text editor, sudo apt-get support (have to get four libraries from repositories, namely libdb-dev, libssl-dev, libavahi-client-dev and libcups2-dev, which will obviously have some dependencies) and compile support for Netatalk 2.1.6. 

What is the basic path I go for this project? I already got Netatalk to work with 10.04LTS and Netatalk 2.1.6 is required to work with AFP over AppleTalk which is what I need.

---

### Post by Cheesemill on 2013-06-12
Install from the Server CD. When you reach the first screen after selecting your language hit F4 and select the option 'Install a minimal virtual machine' before continuing with the installation.

You're not going to get anywhere near 200MB disk space with this method, I did some testing a while back ([here]("http://ubuntuforums.org/showthread.php?t=2037561&p=12156448&viewfull=1#post12156448")) and this method will give you the following result...

*** Ubuntu Server 12.04 Minimal VM Installation***
Used RAM - 16MB
Used HD - 622MB
# of packages - 203

---

### Post by Mk32 on 2013-06-12
I was planning on using an older release like 10.04LTS ____________ because my CPU doesn't support PAE. I ran 12.04LTS in a VM with virtual PAE and the results were not amusing. 

Will that still work?

---

### Post by Cheesemill on 2013-06-12
You could use the [12.04 non-PAE mini CD]("http://cdimage.ubuntu.com/netboot/precise/") to do your installation although you end up with a much larger installation than using the server CD (an extra 170 packages and 0.5GB of drive space).

Using the 10.04 server CD to install a minimal VM is another option, but I can't comment on the drive space or installed packages as I haven't tested with the 10.04 release.

---

