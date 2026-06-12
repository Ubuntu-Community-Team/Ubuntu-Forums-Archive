---
title: "Is there a way of install BURG without internet?"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by jason15300 on 2017-12-18
Hi Guys,

Firstly, apologies if this is the wrong area for this question but is there a way of installing BURG without internet (like a .deb file) as I want to change the default GRUB2 bootloader to BURG and my machine does not have an internet connrction (its a test enviroment computer). However I do have another machine connected to the internet where I can grab files from.

I am running Ubuntu 17.05

Thanks

Jason

---

### Post by oldfred on 2017-12-18
Burg is so obsolete that we cannot recommend it.
And it does not work with newer (last 5 years) UEFI systems. If UEFI use rEFInd as it is a graphical menu also, but is only for UEFI boot systems.

       As of 2012-03-10 orphaned this package in Arch, switch over to grub2-efi-bzr . 
This burg shows last update Oct 2010
[URL="https://code.google.com/p/burg/downloads/list"]https://code.google.com/p/burg/downloads/list

[/URL] 

     newer burg, not?
[http://askubuntu.com/questions/326580/burg-uefi-win-8-multiboot](http://askubuntu.com/questions/326580/burg-uefi-win-8-multiboot)
[https://bbs.archlinux.org/viewtopic.php?id=135645](https://bbs.archlinux.org/viewtopic.php?id=135645)

---

