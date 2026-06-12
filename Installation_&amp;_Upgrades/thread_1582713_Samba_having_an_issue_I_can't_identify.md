---
title: "Samba having an issue I can't identify"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by vexoy on 2010-09-26
I am running Ubuntu 10.04

I have installed Samba by using the command:

sudo apt-get install samba

When it get to the end it has a issue:

Setting up samba (2:3.4.7~dfsg-1ubuntu3.2) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 2094
start: Job failed to start

I have been looking between a whole bunch of tutorials to try and install samba and it seems that the install of samba doesn't include the necessary things. Some say to do:

sudo smbpasswd -a USERNAME

Though that doesn't work, the terminal doesn't recognize the command. Some of them say to edit the smb.conf file but I can't find it and the directory /etc/samba/smb.conf doesn't exist.

I have no idea what the problem is, any help would be much appreciated!!!!

---

### Post by Gaffoonie on 2010-10-04
I was having the same issue.

I used an example of a smb.conf file online to build a replacement, put it in the /etc/samba folder, and the service now runs and stays running.

I have not had a chance to mess around with it too much, so if I run into any issues and find fixes, I will let you know. :)

---

### Post by pricetech on 2010-10-04
Have you tried installing Samba in another fashion ??  For example, install using Synaptic Package Manager and include system-config-samba so you'll have the GUI to configure it with.

---

### Post by jayblue18 on 2010-11-22
I had the same problem. The solution is to reinstall samba-common:

```

sudo apt-get remove samba-common
sudo apt-get install samba 

```Also, see:[http://ubuntuforums.org/showthread.php?t=374254](http://ubuntuforums.org/showthread.php?t=374254)
[https://lists.ubuntu.com/archives/ub...ly/118600.html]("https://lists.ubuntu.com/archives/ubuntu-users/2007-July/118600.html")

---

