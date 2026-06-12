---
title: "How  to  install  fluxbuntu from iso"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by enthusiastic.sady on 2008-09-22
Dear guys,

I have downloaded the Fluxbuntu from the internet. I liked it because my system has low specs. In my drive the CD-ROM is not recognized because my drive is faulty.

I want to install Fluxbuntu from its iso. I have searched the internet for 2 days for a solution but cannot find. I have created partitions and everything ready. Please tell me the way how can I do it. 

(:-< - Tired

---

### Post by oilchangeguy on 2008-09-22
> **enthusiastic.sady said:**
> Dear guys,

I have downloaded the Fluxbuntu from the internet. I liked it because my system has low specs. In my drive the CD-ROM is not recognized because my drive is faulty.

I want to install Fluxbuntu from its iso. I have searched the internet for 2 days for a solution but cannot find. I have created partitions and everything ready. Please tell me the way how can I do it. 

(:-< - Tired

at some point you're going to need a working cd drive (now would be one of those times). so why not buy one? some computer shops sell used ones very cheap. and even new ones aren't very expensive.

---

### Post by snowpine on 2008-09-22
You can check out UNetBootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to install various Linux distros without a working CD drive. It does not support Fluxbuntu, but you could for example install Xubuntu and then install Fluxbox on top of it using 'sudo apt-get install fluxbox'. Unetbootin also supports some nice distros for low-spec computers such as Puppy, DSL, and SliTaz. If your heart is set on Fluxbuntu, however, you'll need a working CD drive. Another work around is to put your hard drive into a different computer with a working CD drive, install Fluxbuntu, and then swap the drive back to your computer. There are many options. :)

---

### Post by Rhubarb on 2008-09-22
If you have access to a computer with a CD-ROM drive, you could install fluxbuntu onto your hard drive from the other computer.
This will involve you taking the hard drive out, and putting it inside the other computer with a CD-ROM drive.  But it does work quite well.  - I did this late last year (2007) without any troubles.

---

### Post by enthusiastic.sady on 2008-09-22
I used aero studio 2008 to modify my boot.ini and put 

C:\Avldr.bin="Avlgo - fluxinstaller.iso" 

So, when I choose the 2nd option to install linux, everything goes very fine. From loading the kernel to many modules. But it suddendly check for hardware, when it finds a CD-ROM drive, the setup says this needs to be mounted and asks for continue to me. I cannot continue without mounting and setup stops.

But how can a drive be mounted which cannot recognize data itself. So, is'nt there any way to just skip this ? Can I choose "more options" and do sth so that I can go on.

---

