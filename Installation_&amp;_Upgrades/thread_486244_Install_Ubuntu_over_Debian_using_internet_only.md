---
title: "Install Ubuntu over Debian using internet only?"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by Ozdemon on 2007-06-27
I have an old Gateway 9300 laptop that cannot boot from CD or usb (trust me, it can't).  

I have installed Debian because I couldn't get the Ubuntu install without CD to work, see posts #23-#26 [http://ubuntuforums.org/showthread.php?t=427540&page=3]("http://ubuntuforums.org/showthread.php?t=427540&page=3")

So do I resign myself to Debian or is there a way of downloading and installing Ubuntu over the internet?

BTW I looked at Netboot install, but that is way over my head.

---

### Post by Sonofmoog on 2007-06-27
> **Ozdemon said:**
> I have an old Gateway 9300 laptop that cannot boot from CD or usb (trust me, it can't).  

I'm betting you can boot from your CDROM drive .. if you have the Smart Boot Manager and a floppy drive which is bootable.  Google for it, make the disk, (the SBM is free), insert your CD, select boot from CDROM, and you should be good to go ..

---

### Post by Ozdemon on 2007-06-27
> **Sonofmoog said:**
> I'm betting you can boot from your CDROM drive .. if you have the Smart Boot Manager and a floppy drive which is bootable.  Google for it, make the disk, (the SBM is free), insert your CD, select boot from CDROM, and you should be good to go ..

The CD-drive is broken - it does not spin.

BTW I am going crazy with debian -  I can't even install firefox. ](*,)

---

### Post by trak87 on 2007-06-27
I used to read about people installing Linux via FTP all the time. I've never done it but that was all the rage a while back. Google it.

---

### Post by mkoyle on 2007-06-27
Back in the days of Breezy I 'upgraded' from Debian to Ubuntu by changing my sources.list

It isn't for the faint of heart, but if you have a minimal Debian system, it should work.

Change your sources list (as root or with sudo)
> 
 nano /etc/apt/sources.list

Remove the Debian sources and add the Ubuntu ones 

> 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

 ## Major bug fix updates produced after the final release of the 
 ## distribution.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

then run (probably as root but if you have sudo, with sudo)

>  apt-get update
 apt-get upgrade
 apt-get install ubuntu-desktop ubuntu-minimal ubuntu-docs 
 apt-get dist-upgrade

If you have problems, come back and post them.  There might be a dependency issue... you might have to remove a package that is giving you trouble and then start over, it just depends on which release of Debian you are using.  If you have trouble, try 

> apt-get -f install

and then go back to the other commands above.

cross your fingers and wait for a long time ... it might even work.  Watch out-- someone is going to post here that that is a terrible and impossible and foolish thing to do.  Really, though it is nearly the same as an upgrade from one version of Ubuntu to another.  Make sure you remove the Debian sources and you should be in business.  If you have problems with particular hardware or software, you can find the solution.  It will mostly be a problem with old setup files being left behind.  When it asks if it should modify setup always answer yes. 

good luck,

--Matthew

---

### Post by kerry_s on 2007-06-27
> **Ozdemon said:**
> The CD-drive is broken - it does not spin.

BTW I am going crazy with debian -  I can't even install firefox. ](*,)

Debian is great, it's just as good as ubuntu, but faster.

in debian firefox is iceweasel> **su & apt-get install iceweasel**
or
you can use synaptic if you want to do it by gui.

Are you running a etch only system?

i'm running a lenny/sid system.

---

### Post by Ozdemon on 2007-06-28
**UPDATE**

My hard drive failed during a re-install, - a funeral service was held last night, followed by a wake.  Many thanks for the suggestions - I will now buy a 2nd laptop with a bootable cd drive.

---

