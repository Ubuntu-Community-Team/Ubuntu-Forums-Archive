---
title: "install ubuntu on a hackintosh netbook"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by sansa dude on 2009-12-20
I have a dell mini 10v with mac os x on it with chameleon v2.0-rc3 boot loader and I want to install ubuntu and use GRUB as my boot loader and still be able to access my hackintosh partition. 

So what I want to know is do I just go with a normal ubuntu installation and resize the partition, and then I should see my hackintosh there and everything is good or will I have to add it afterwards to the boot menu?

---

### Post by raymondh on 2009-12-20
> **sansa dude said:**
> I have a dell mini 10v with mac os x on it with chameleon v2.0-rc3 boot loader and I want to install ubuntu and use GRUB as my boot loader and still be able to access my hackintosh partition. 

So what I want to know is do I just go with a normal ubuntu installation and resize the partition, and then I should see my hackintosh there and everything is good or will I have to add it afterwards to the boot menu?


I am using grub-LEGACY.

I had to chainload mine.  I chainload because I installed Darwin in the OSX partition.  So from grub, selecting OSX, will segue into darwin and boot the OS.  I mention this because I do not know how/where/if you installed darwin nor do I have any experience with chameleon.

Good luck.

---

### Post by sansa dude on 2009-12-20
So I have to install something into the os x partition so GRUB will let me boot into it?

---

### Post by raymondh on 2009-12-20
> **sansa dude said:**
> So I have to install something into the os x partition so GRUB will let me boot into it?

As I mentioned/hinted above, I don't know how you installed your OSX or if, during said install, you included (dd) the boot/0 files in the partition.

Try chainloading first.  This is my entry in my GRUB-legacy menu.lst.  I do not know what or how to configure chameleon.

title              OSX
rootnoverify  (hd[COLOR="Red"]X,Y[/COLOR])  *where [COLOR="Red"]X,Y[/COLOR] is the location of OSX*
makeactive
chainload       +1

See if that works.  If not, post back the error.  

Note ..... again,  **I am using GRUB-LEGACY (9.04) and not GRUB2 (9.10)**.

Google-fu brings up this tutorial on a dell mini 10 and chameleon. You might want to read/research this first

[http://www.mydellmini.com/forum/dual-booting/13903-working-triple-boot-osx-win7-ubuntu-through-chameleon.html](http://www.mydellmini.com/forum/dual-booting/13903-working-triple-boot-osx-win7-ubuntu-through-chameleon.html)

Regards,

---

### Post by DarkAngel88 on 2009-12-21
I'm currently trying to get OSX to boot, after installing Ubuntu 9.10.  

As of now, it is not working.  I'm wondering if there is a way to remove grub2 and get grub legacy on ubuntu 9.10 to get the chainload to work...?

---

### Post by raymondh on 2009-12-21
@ sansa dude .... this may help as well.  Note item 1 in the 'Ubuntu people follow this guide'.

[http://ihackintosh.blogspot.com/2008/09/how-to-add-osx86-to-xp-vista-grub-boot.html](http://ihackintosh.blogspot.com/2008/09/how-to-add-osx86-to-xp-vista-grub-boot.html)

@dark angel88

See the above-link as well.  As for replacing GRUB2 with GRUB-legacy, see this link ....

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Good luck.

---

