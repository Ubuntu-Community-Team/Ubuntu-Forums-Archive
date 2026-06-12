---
title: "Choosing Ubuntu to install"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by scadotte on 2012-01-09
HI there, this will be my first time installing Ubuntu on ANYTHING...I have a 64 bit windows 7 OS and would like to dual boot.  My question is which is the best Ubuntu  version to use for this?

:popcorn::p:D:p;););)

---

### Post by Basher101 on 2012-01-09
before you go for a full install, you should check if Ubuntu runs fine on your machine. Do this via a Live CD session or make a Wubi install to check things out first. 


regards

p.s. without knowing any of your specs, i would suggest the latest version of Ubuntu, 11.10 Oneiric Ocelot.

---

### Post by nothingspecial on 2012-01-09
> **scadotte said:**
> HI there, this will be my first time installing Ubuntu on ANYTHING...I have a 64 bit windows 7 OS and would like to dual boot.  My question is which is the best Ubuntu  version to use for this?

:popcorn::p:D:p;););)

Hi, welcome to the forums :)

The answer to your question depends on how much ram you have.

If you have 1 or more G then you should try Ubuntu 11.10

---

### Post by Lars Noodén on 2012-01-09
Try several of them before deciding.  You can burn them onto CD-RW and re-used the disc.  

Ubunut/Kubuntu/Xubuntu/Lubuntu all have different defaults but underneath they are all the same and any single one of them can be turned into one of the others by adding and subtracting packages.

---

### Post by scadotte on 2012-01-09
> **nothingspecial said:**
> Hi, welcome to the forums :)

The answer to your question depends on how much ram you have.

If you have 1 or more G then you should try Ubuntu 11.10
I have 2gb RAM, but am upgrading to 4 tomorow..so I good there, but I don't good where "Linux assumes you know exactly what you are doing"

I work in IT and have for 20+ years..but always Windows and Microsoft.  All the guys I work with have stressed the enjoyment of Linux,  unfortunately I didn't act upon my wish to explore until now (better late than never!?)  so here I go...

---

### Post by nothingspecial on 2012-01-09
> **scadotte said:**
> I have 2gb RAM, but am upgrading to 4 tomorow..so I good there, but I don't good where "Linux assumes you know exactly what you are doing"



Maybe I ought to change my sig :). It's said that for a long time.

Fortunately Ubuntu does it's best to ensure that you don't have to know what your doing.

---

### Post by Basher101 on 2012-01-09
> **scadotte said:**
> I have 2gb RAM, but am upgrading to 4 tomorow..so I good there, but I don't good where "Linux assumes you know exactly what you are doing"

I work in IT and have for 20+ years..but always Windows and Microsoft.  All the guys I work with have stressed the enjoyment of Linux,  unfortunately I didn't act upon my wish to explore until now (better late than never!?)  so here I go...

it is never too late. You should also check if your motherboard supports USB boot (look in your BIOS if you can select USB HDD in the boot options). If you can, you will save alot of time, since reads from USB are alot faster than CDs and you can reuse the USB countless times. Go here to check how to create a Live USB [www.pendrivelinux.com](www.pendrivelinux.com) i recommend the Universal USB installer

---

### Post by scadotte on 2012-01-09
> **Basher101 said:**
> it is never too late. You should also check if your motherboard supports USB boot (look in your BIOS if you can select USB HDD in the boot options). If you can, you will save alot of time, since reads from USB are alot faster than CDs and you can reuse the USB countless times. Go here to check how to create a Live USB [www.pendrivelinux.com](www.pendrivelinux.com) i recommend the Universal USB installer
Basher,

I am certain it does support usb boot, s that's great.  I will of course seqrch and look for answers when stuck, but any chance I good give you a shout if really stuck?

Sheila

---

### Post by Mark Phelps on 2012-01-09
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Basher101 on 2012-01-09
> **scadotte said:**
> Basher,

I am certain it does support usb boot, s that's great.  I will of course seqrch and look for answers when stuck, but any chance I good give you a shout if really stuck?

Sheila

if you have any questions regarding installs, feel free to PM me. I have alot of expierence on how to do installs (considering im a perfectionist and reinstalled ubuntu 15 times total on my laptop because there was always something bugging me^^)

---

### Post by oldfred on 2012-01-09
Good advice from previous posters.

If you want to see the process to install, these sites have examples with screenshots. Different versions are only slighlty different in how screens look as process is the same.

aysiu's are straight forward, Herman's are very detailed if you wants to know more or just follow screen shots.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

