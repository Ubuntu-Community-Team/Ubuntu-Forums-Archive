---
title: "installation from windows doesnot work"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by praroh on 2007-02-24
Hi,

I tried to install Ubuntu6.10 from harddisk but in vain. I followed the following steps:

1) I downloaded Ubuntu desktop CD and tested it on my desktop. Worked nicely. 
I wanted to install it on my laptop whose DVD-drive just died. So, I tried the procedure to install from the hardisk with WIndows XP. USB installation does not seem to work as my computer doesnot support booting from the external drive.

2) I followed the instructions on [https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")

3) Created directory c:\ubuntu
4) Installed grub and changed boot.ini file. The grub is working nicely. 
5) Added the following to menu.lst file:

This is my menu.lst file

title Install Ubuntu
kernel   (hd0,0)/ubuntu/install/vmlinuz vga=normal root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/install/initrd.gz

6) When I tried to boot up using grub, everything looked fine. It identifies the kernel and initrd file. I was expecting to see the Ubuntu logo for installation, however I was presented with "initramfs"  prompt. I can type simple commands like "ls"
 I am not sure if this is the way it is supposed to.  

Please advice what went wrong in my installation and how to proceed  

Thanks

Praroh

---

