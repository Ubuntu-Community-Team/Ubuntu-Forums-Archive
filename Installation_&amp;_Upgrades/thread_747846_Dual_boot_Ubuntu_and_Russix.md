---
title: "Dual boot Ubuntu and Russix"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by CrimsoniteX on 2008-04-06
Hello everyone,

I am looking to dual boot Ubuntu and Russix together. I have Ubuntu 7.10 already installed, but I am a complete newbie to this. Do I just pop in the Russix CD and do a normal install? Will grub set things up automatically? If not, what do I need to do with Ubuntu to get it ready?

Thanks in Advance!

---

### Post by confused57 on 2008-04-07
> **CrimsoniteX said:**
> Hello everyone,

I am looking to dual boot Ubuntu and Russix together. I have Ubuntu 7.10 already installed, but I am a complete newbie to this. Do I just pop in the Russix CD and do a normal install? Will grub set things up automatically? If not, what do I need to do with Ubuntu to get it ready?

Thanks in Advance!
I had to do a Google search for Russix, which is a Slax-based "distro"...I'm not sure, but Slax probably uses Lilo as the bootloader.  What you might want to do is use Gparted on the Ubuntu live cd to resize a partition(root, /home,other?), then format as ext3(or allow the Russix installer to format as the preferred filesy...Gparted is in System---Administration---Gnome Partition Editor.

You could try going through the Russix install and allow lilo to be installed to the mbr.  If you're not able to boot Ubuntu from lilo, you can use the Ubuntu live cd to reinstall Ubuntu's grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you should be able to add an entry to Ubuntu grub's menu.lst to boot Russix, using symlinking:
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

I've used Slackware before, which uses lilo and is what I'm basing my suggestions on.

---

### Post by CrimsoniteX on 2008-04-07
Alright, thank you for the info, I will let you know how it goes.

---

