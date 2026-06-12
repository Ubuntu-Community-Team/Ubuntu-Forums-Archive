---
title: "new installation memory requirements"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by saud on 2012-08-04
I installed all Debian, Ubuntu and Centos and Debian was the lowest in memory after new installation at 33 MB and Ubuntu was around 100 MB, Why it is that, I just want a basic server without any other things running on the server.

---

### Post by Ubun2to on 2012-08-05
Well, each distro has different background processes running and different features. Ubuntu has Unity, which drives up requirements, but you also have things like KDE and Cinnamon, which can do the same.

---

### Post by Cheesemill on 2012-08-05
If you use the Alternate Install CD and select 'Install a Command Line System' from the first screen (by hitting F4) you end up with a small installation. I've just done this on a VM and end up with the following figures:

Used RAM: 22MB
Used HD:               901MB
# of Packages:    324

---

### Post by saud on 2012-08-06
Where I can find the alternate install CD?

---

### Post by Cheesemill on 2012-08-06
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by mastablasta on 2012-08-07
another option is minimal install iso.
 
server in Ubuntu takes more ram probabyl because it has more features than Debian already included.

---

### Post by Cheesemill on 2012-08-07
> **mastablasta said:**
> another option is minimal install iso.

I did some tests a while back with the alternate and mini CD's, you actually end up with a smaller system with less packages installed when doing a CLI install from the alternate CD.

---

### Post by saud on 2012-08-07
Thats what I wanted to download, Minimal CD but could not find it. I just wanted a basic server installation.

---

### Post by mastablasta on 2012-08-07
it popped out as first result in google to me... but anyway if anyone else is looking for it: [https://help.ubuntu.com/community/Installation/MinimalCD/](https://help.ubuntu.com/community/Installation/MinimalCD/)

---

### Post by Cheesemill on 2012-08-07
I've been doing a bit more research into this issue for a project at work so thought I'd post my results here if anyone else was interested.

I've just installed Ubuntu using a variety of methods using VirtualBox. All VM's had identical specs, only the boot media and installation options (chosen by hitting F4 on the installation screen) were different, no extras were chosen if the taskselect screen was offered. Results were gathered upon second boot using the following 3 commands:
```
free -m
df -h
dpkg --get-selections | wc -l
```[B]

[SIZE=3][COLOR=Red] VM Specifications[/COLOR][/SIZE]
OS[/B] - Ubuntu 12.04 i386
**RAM** - 512MB
**CPU** - 1 x Virtual CPU
**HD** - 8GB (Default options, no LVM, 8053MB ext4 root partition, 535MB swap)


**Mini CD - [COLOR=DarkSlateBlue]*Command-line install*[/COLOR] option**.
Used RAM - 23MB
Used HD - 1.1GB
# of packages - 373

**Alternate CD - [COLOR=DarkSlateBlue]*Install a command-line system*[/COLOR] option**.
Used RAM - 22MB
Used HD - 901MB
# of packages - 324

**Server CD - [COLOR=DarkSlateBlue]*Default installation*[/COLOR] option**.
Used RAM - 24MB
Used HD - 889MB
# of packages - 367

**Server CD - [COLOR=DarkSlateBlue]*Install a minimal system*[/COLOR] option**.
Used RAM - 22MB
Used HD - 801MB
# of packages - 321

**Server CD - [COLOR=DarkSlateBlue]*Install a minimal virtual machine*[/COLOR] option**.
Used RAM - 16MB
Used HD - 622MB
# of packages - 203

> I installed all Debian, Ubuntu and Centos and Debian was the lowest in  memory after new installation at 33 MB and Ubuntu was around 100 MBAfter my above results I have absolutely no idea how you ended up with 100MB used RAM on a fresh server installation.

How did you install and what commands did you use to check your memory usage?

---

