---
title: "Installing Grub"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by Banshee-2007 on 2011-07-31
Hi every body

Since a while I've installed Windows my laptop , with the wishes of installing grub again after Windows erases it . But today I tried to to that , but all my tries failed .

I depended on this thread to see the way of installing grub :
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I checked this also :
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I searched for the way of installing grub before I install Windows , just to make sure about where I was going to .

By the way , I have got Ubuntu 11.04

First I applied the first step , when I applied this command :

```

sudo grub

```And Ubuntu gave me the following message >>    sudo: grub: command not found

Then I tried this :
```

grub

```But it gave me this message >>   The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

So I applied the command and installed grub . But I want to know install grub from the live CD , because I may face some occasions when the computer is off-line !!

Anyway , I installed it , then rebooted , but nothing has changed . I rebooted again , then reinstalled grub , I applied the first command :
```

sudo grub

```That worked , and then I was in grub I think . I check this command below :

```

find /boot/grub/stage1

```But Ubuntu unfortunately gave me this result >>    Error 15: File not found


So where's the problem ??

Please help guys 
and sorry for long thread

---

### Post by dino99 on 2011-07-31
you may pay attention on quality information on the net: for example both links you have given above refer to 2006/2007 and you probably know that actually we are into 2011 dont you.

So all you have followed is outdated and can only break your system

follow this howto:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

but first remove everything about grub & menu.lst before installing grub2 (in fact grub-pc) with the command: sudo grub-install /dev/sda

here is kow i make an install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

