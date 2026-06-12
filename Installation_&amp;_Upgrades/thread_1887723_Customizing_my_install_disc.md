---
title: "Customizing my install disc?"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Driger on 2011-11-27
alright, i want a install disc to install ubuntu 11.10 (x64) exactly as i want it.

I've read online about remastering, customizing looked into different programs even tried to download reconstructor but it didnt want to install.

_The first time i boot up my comp after installing from the live cd i want to have a customized splash screen, no log in screen, certain programs installed and certain programs not installed as well as my appearance settings the way i like them. How do I do it? _

the reason for this is so that every time i do a fresh install i dont want to have to spend time tweaking appearance settings installing programs and getting rid of the clutter that i dont use.

Reconstructor looked like the simplest way to do it but like i said i wasn't able to install it.

**Any suggestions on how to achieve this are more then welcome. As well as how to install reconstructor would be nice too.**

---

### Post by Driger on 2011-11-28
After a few hours of looking around i discovered Ubuntu customization kit. I thought my problems were solved however UCK wont work for me. I recieved this error when i tried to customize the ubuntu-11.10-desktop-amd64.iso

[PHP]Build (/usr/bin/uck-gui --wait-before-exit) started at 2011-11-28 03:00:15
>> Ubuntu Customization Kit 2.4.4 on Ubuntu 11.10, 3.0.0-12-generic x86_64
Starting CD remastering on  Mon Nov 28 03:00:19 EST 2011
Customization dir=/home/admin/tmp/customization-scripts
Mounting ISO image...
mount: warning: /home/admin/tmp/remaster-iso-mount seems to be mounted read-only.
Unpacking ISO image...
cp: reading `/home/admin/tmp/remaster-iso-mount/casper/filesystem.squashfs': Input/output error
Unmounting /home/admin/tmp/remaster-iso-mount...
Failed to unpack ISO from /home/admin/tmp/remaster-iso-mount to /home/scott/tmp/remaster-iso
Build ended at 2011-11-28 03:04:00[/PHP]**I think the problem is the part that says "mount: warning: /home/admin/tmp/remaster-iso-mount seems to be mounted read-only" Will making it not read only fix it? How do i make it not read only?**

---

### Post by lukeiamyourfather on 2011-11-28
I'm also curious about how to customize an install disc. Before I became a Linux user I used Microsoft's tools and nLite/vLite, similar tools for Linux and Ubuntu could be useful. However there are many other methods to create customized installs that are consistent. For example in small scale deployments scripts can be used to install software and configure the system (shell scripts, Python, Perl, etc.). On a larger scale there are tools like CFEngine that are very robust and flexible. There's also disk cloning if the hardware is consistent between the machines.

---

### Post by WasMeHere on 2011-11-28
Hi

Would an OEM procedure work for you? Read the thread in this link
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1884055_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1884055")

Have fun finding out :-)
Olle

---

