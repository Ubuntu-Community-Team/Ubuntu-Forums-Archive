---
title: "Linux in general will not install"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by sourkraut on 2007-06-28
I am trying to install KUbuntu on a 
Medion laptop
pentium III 851 Mhz
128 MB of RAM
and it will install up to a certain point and then just stop.
I will see a command line promt
Ubuntu@ubuntu: ~$

After trying to install several times with the same result I tried  the standard Ubuntu and alternate Ubuntu and got to the same point with the same result.  Other Linux versions, ie. Kantotix, SUSE,.... are not willing to install as well.  But I am really only interested in KUbuntu to work or Ubuntu.
The laptop is running XP Pro at the moment.  I have tried to use a disk erase tool but I can not find one built for a cd and the 3.5 drive is not in the bios as a boot option.  Not even sure if erasing the disk will help (other than getting ride of Microsoft).
got the time to try all kinds of things so let me know what you think.
thanks ;)

---

### Post by logos34 on 2007-06-28
> **sourkraut said:**
> I am trying to install KUbuntu on a 
Medion laptop
pentium III 851 Mhz
**128 MB of RAM**
and it will install up to a certain point and then just stop.
I will see a command line promt
Ubuntu@ubuntu: ~$

After trying to install several times with the same result I tried  the standard Ubuntu and **alternate Ubuntu **and got to the same point with the same result.  Other Linux versions, ie. Kantotix, SUSE,.... are not willing to install as well.  But I am really only interested in KUbuntu to work or Ubuntu.
The laptop is running XP Pro at the moment.  I have tried to use a disk erase tool but I can not find one built for a cd and t**he 3.5 drive is not in the bios as a boot option**.  Not even sure if erasing the disk will help (other than getting ride of Microsoft).
got the time to try all kinds of things so let me know what you think.
thanks ;)

You were right to try the alternate install cd because you're never going to get it to run the live cd on that little ram.  But you can't properly run gnome, let alone kde desktop on that memory.  Add another stick if possible.  Or try Xubuntu --uses lighter Xfce desktop and Thunar file manager.  

I doubt erasing the hard disk will help...sounds like you need to pass some boot options to the kernel so you can get the installer going.  Hit F1 help

So there's no option to boot from floppy/removable drives?  

You migh consider adding a stick of ram--memory is cheap these days.

---

### Post by sourkraut on 2007-06-28
ok that makes things quite a bit clearer.  
For some reason I over looked the system requirements. (sorry)
It may be possible to boot from the floppy if the floppy is known as a "removable device".  but I have moved Removable Devices to position one **and it still does not boot from the floppy.**  And I know that the disk is good because I have used it recently on my desktop.


So if your recomendation is to** invest money** into my laptop to make it work I think that I am going to have to find another option. long story short, missing buttons, no cover for cd drawer,.....
functionality is all there but the glamor is missing.

**is there a linux distro out there that is fun to use but with out the bells and whistles of Ubuntu?**
If so I would be happy to try that.  My ultimate goal is not to be left behind in the world of computers and I see the Linux/Ubuntu surge as a great thing, and I want to be part of it.

[B]Thanks for your input
Sourkraut  [/B]

---

### Post by stchman on 2007-06-28
Yes, Ubuntu requires at least 256MB RAM.  I would not go under 512MB.  I am going to assume that you can use PC133.  You can get it on ebay pretty cheap.

---

### Post by bigken on 2007-06-28
ye I agree 512mb of ram  at least ;)

---

### Post by logos34 on 2007-06-28
I'd try some featherweight linux distro like puppylinux, featherlinux, Damn Small, Zenwalk...It would be nice if you could  run Xubuntu because Ubuntu is such a great version of linux.  But try any of the above just to see if you can get the installation going, then you can use whatever built-in parititoner is available to wipe the drive and create partitions.  But it sounds like the immediate problem here is getting the right options to the kernel so it can load.  It's a hardware issue.  But after that is fixed is $15USD too much to spend on giving some 'umpf' to that dogeared 'ol laptop? (that'll get you an additional 128 or even 256MB ram--look for a rebate sale).
> 
It may be possible to boot from the floppy if the floppy is known as a "removable device". but I have moved Removable Devices to position one and it still does not boot from the floppy

You could try enabling 'bootup floppy seek' (if you have that option).  If you have 'removable' set as the first boot device int he BIOS and you're seeing the floppy drive light come on, then it's trying but for some reason cannot read the bootable image on the floppy disk; if you DON'T see the light come on then it's bypassing the drive.  Also check the the 'removable' drives section and make sure that the floppy is at the top).

---

### Post by firedancer on 2007-06-28
puppylinux !


DBAN if you really need wiping the stuff off !

---

### Post by jbennet on 2007-06-28
debian will run on 128mb

---

### Post by Super TWiT on 2007-07-05
> **stchman said:**
> Yes, Ubuntu requires at least 256MB RAM.  I would not go under 512MB.  I am going to assume that you can use PC133.  You can get it on ebay pretty cheap.

I have gotten the gnome version of Ubuntu to work very smoothly on a laptop with 192 MB of RAM.  I did use the alternate CD to install though.

---

### Post by ChIkEn on 2007-07-05
I have 1 Gb ram and I get the same thing. :(

---

