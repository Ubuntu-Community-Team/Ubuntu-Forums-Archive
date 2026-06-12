---
title: "A little help needed"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by YBYNTU on 2010-02-16
I need to edit my etc/network/interfaces but it shows as read only and I dont know how to get permission. I'm using Karmic Koala 64 bit and trying to get my network adapters sorted out.
 
I will not give up on Linux just yet, but three days with no net access is getting to be a pain.

---

### Post by Satoru-san on 2010-02-16
> **YBYNTU said:**
> I need to edit my etc/network/interfaces but it shows as read only and I dont know how to get permission. I'm using Karmic Koala 64 bit and trying to get my network adapters sorted out.
 
I will not give up on Linux just yet, but three days with no net access is getting to be a pain.

```
gksudo gedit /etc/network/interfaces
```

Why do you need to edit that file? You shouldn't touch that! (unless a walkthough told you to)

---

### Post by YBYNTU on 2010-02-16
I'm trying the following fix;
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)

---

### Post by Satoru-san on 2010-02-16
according to this you never have to touch that file!!!

do this.

```
##########################################
 Networking Solution for nVIDIA MCP55 Ethernet - Ubuntu 8.10 Interpid
##########################################
 Step 1, open a terminal.
 a) become superuser
$ sudo su
 b) remove forcedeth kernel module (it's the ethernet's driver)
# rmmod forcedeth
 c) load forcedeth kernel module again with new parameters
# modprobe forcedeth msi=0 msix=0
 d) restart networking
# /etc/init.d/networking restart
 You should be able to connect to your network now.
 Step 2, configure the system to do this automatically from now on when it starts
(otherwise you'll need to do the above steps every time you boot).
 Open a terminal and become root with
$ sudo su
 a) go to /etc/modprobe.d/
# cd /etc/modprobe.d/
 b) edit the options file
# gedit options
 c) go to end of file and add the following lines (without the quotes)
"#nVIDIA Corporation MCP55 Ethernet"
"options forcedeth msi=0 msix=0"
 d) save the changes and close gedit
 e) you'll need to rebuild your boot image, in the same terminal type:
# update-initramfs -u
 Reboot and you're done.

```

---

### Post by YBYNTU on 2010-02-16
no joy with that, I dont have /etc/modprobe.d/
 
I dont know if thats because its 8.10 and I have 9.10

---

