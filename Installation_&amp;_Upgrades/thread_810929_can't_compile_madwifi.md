---
title: "can't compile madwifi"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by jobo1313 on 2008-05-28
Last week I installed Ubuntu 8.04 on my Sony vaio VGN-NR220E. But the wireless didn't work:cry:. The driver didn't show up. I read that I needed to install madwifi. I downloaded it and tried to compile it. Then a bunch of errors came up saying that it couldn't find the    c headers. I tried multiple codes such as:
gksudo aptitude install build-essential 
gksudo apt-get install gcc
None of these worked.
HELP!!!!

---

### Post by zvacet on 2008-05-28
```
sudo aptitude install build-essential
```

---

### Post by Pumalite on 2008-05-28
Post:
lshw -C network

---

### Post by jobo1313 on 2008-05-29
Here it is:
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:25:a4:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.0.3 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0




Thanks



PS:
zvacet sudo doesn't work because there is no password so you put gksudo which does the same thing.

---

### Post by zvacet on 2008-05-29
>  sudo doesn't work because there is no password

How do you login without password?When **sudo** ask for password use same one you use for login in Ubuntu.

---

### Post by Pumalite on 2008-05-29
Open up all your repos; including partner, updates, proposed, backports, etc
Then sudo apt-get upgrade
Report back

---

### Post by jobo1313 on 2008-05-29
> **zvacet said:**
> How do you login without password?When **sudo** ask for password use same one you use for login in Ubuntu.

This is for zvacet:
There is noooo password for the root, su, sudo. This is a security measure so someone can't get into it. You just use gksudo in front of the code and there is no need to login or put in a password. Read the ubuntu book dude. I might be a noob, but I'm not stupid.

---

### Post by jobo1313 on 2008-05-29
Thanks Pumalite for responding so quick.
I did what you said, it upgraded my ubuntu installation was that what it was suppose to do.
Thanks

---

### Post by Pumalite on 2008-05-29
How is your wireless now?

---

### Post by zvacet on 2008-05-30
So this is outdated

> In Linux (and Unix in general), there is a superuser named root. The Windows analog of root is Administrator. The superuser can do anything and everything, and thus doing daily work as the superuser can be dangerous. You could type a command incorrectly and destroy the system. Ideally, you run as a user that has only the privileges needed for the task at hand. In some cases, this is necessarily root, but most of the time it is a regular user. 

By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user, however, since the root account physically exists it is still possible to run programs with root-level privileges. This is where sudo comes in; it allows authorized users (normally "Administrative" users; for further information please refer to AddUsersHowto) to run certain programs as root without having to know the root password. 

This means that in the terminal you should use sudo for commands that require root privileges; simply prepend "sudo" to all the commands you would normally run as root. For more extensive usage examples, please see below. Similarly, when you run GUI programs that require root privileges (e.g. the network configuration applet), you will also be prompted for a password. Just remember, when sudo asks for a password, it needs YOUR USER Password, and not the root account password.

---

### Post by daRealScanMan on 2008-05-30
> **zvacet said:**
> So this is outdated
No, they're both means to an end.
>  Root Access with sudo and gksudo
ubuntu unlike many distributions does not normally have a user accessible root account. You are supposed to use one of these two commands when you need root access. sudo is for when you are in the terminal and need root access and gksudo is when you are in the GUI and need root access, for example you can press alt+f2 and type "gksudo appname".

---

### Post by zvacet on 2008-05-30
@** daRealScanMan**

I know that,but if I understood **jobo1313** correctly he is using gksudo in command line without password.I never tried that but if he is right that make me feel less secure.

---

### Post by jobo1313 on 2008-05-30
I still can't compile madwifi even though the c headers were upgraded. I don't get how if the atheros driver is detected and can't be installed.

---

### Post by Pumalite on 2008-05-30
I don't know if this might help you:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843)

---

### Post by jobo1313 on 2008-05-30
No man I tried that ndiswrapper I get the same errors can't find c header files. The headers it is looking for don't exist. If there is some website I can get them from it would be great.

---

### Post by jobo1313 on 2008-05-30
zvacet someone can't login to the computer with your username and password. If they try sudo, root, su, gksudo, or super user they need a password that does not exist. I'm just saying when logged in I use gksudo and it works. When ever I tried just sudo it gives me an error. Just use what ever works for you.

---

### Post by zvacet on 2008-05-31
> When ever I tried just sudo it gives me an error.

What kind of error?Maybe we can help you  solve it.

---

### Post by jobo1313 on 2008-05-31
The whole sudo thing doesn't matter right now. I found a way to compile and install madwifi but I can't load the module.

---

