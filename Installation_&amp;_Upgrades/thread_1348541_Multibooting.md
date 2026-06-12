---
title: "Multibooting"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by borg101 on 2009-12-07
I built a pretty nice system and I want to tri multibooting (get the pun?!?! :-p  ).  I've dual booted a few linux distros (slackware, fedora, and ubuntu mostly)  with window xp.  I've heard the bootloader for windows 7 is different though I'm sure I could figure out how to dual boot a linux distro and windows 7.  However, I want to play with snow leopard and I'm not sure how to install a mac OS.  I did it once years ago with OS 8 or 9.....but I completely forget anything and everything with mac software.  

Are there any "how to's" out there or guides?  Forgive me if this isn't an original post.  I searched but only found threads on dual booting.  

Thanks in advance for any assistance!!

---

### Post by raymondh on 2009-12-08
> **borg101 said:**
> I built a pretty nice system and I want to tri multibooting (get the pun?!?! :-p  ).  I've dual booted a few linux distros (slackware, fedora, and ubuntu mostly)  with window xp.  I've heard the bootloader for windows 7 is different though I'm sure I could figure out how to dual boot a linux distro and windows 7.  However, I want to play with snow leopard and I'm not sure how to install a mac OS.  I did it once years ago with OS 8 or 9.....but I completely forget anything and everything with mac software.  

Are there any "how to's" out there or guides?  Forgive me if this isn't an original post.  I searched but only found threads on dual booting.  

Thanks in advance for any assistance!!

Borg101,

Setting up a 3-boot is the same as setting up a 2-boot.  Google "install OSX in PC" for clues/guides/slipstreaming process' and then install win7 and finally Ubuntu.

I 3-boot (OSX - Win7 Pro - Jaunty).  I use GRUB in the MBR as the bootloader which segues to Darwin for OSX boot-up.  You can try CHAMELEON.  

Is the effort worth it?  Yes... as a learning experience and only on a test machine netbook.... as well as to sync my files between my main mac-OSX machines .... but that's about it.  Main challenges are hardware + driver difficulties that had to be addressed (keyboard, wifi, etc).

Good luck.

---

### Post by andrew.46 on 2009-12-08
Hi borg,

> **borg101 said:**
> I've heard the bootloader for windows 7 is different though I'm sure I could figure out how to dual boot a linux distro and windows 7. 

Another thing to consider would be to use a virtual machine with Windows 7, it works well on my sysem.

All the best,

Andrew

---

