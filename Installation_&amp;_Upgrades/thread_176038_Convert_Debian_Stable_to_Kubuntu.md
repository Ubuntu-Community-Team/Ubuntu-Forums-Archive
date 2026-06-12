---
title: "Convert Debian Stable to Kubuntu?"
date: 2006-05-14
forum: Installation &amp; Upgrades
---

### Post by rustleg on 2006-05-14
I am trying to install Kubuntu on a multiboot system with XP using a commercial boot manager (BootitNG). I have succeeded in installing Debian Stable Linux but not Kubuntu.

The boot manager manages an "extended" MBR which allows me to create many primary partitions (not just 4) and then it loads any 4 partitions into the MBR before passing control to the first chosen boot partition. At this point it also allows booting from CD.

When I installed Debian the installation routines in Debian correctly saw my MBR and allowed me to specify where I mount root etc. and where to install Grub (can't go in the MBR needs to go in the root partition). However the Kubuntu installer fails to see any of the MBR details and just presents me with my 200GB drive with a request for me to specify partitions. I am loathe to go ahead with this as I am not confident that it will treat the size specifications of the partitions in exactly the same way as my boot manager/partitioner, so I aborted the install here.

So my next idea is can I convert Debian Stable into Kubuntu. Maybe by editing /etc/apt/sources.list and running aptitude dist-upgrade? In which case what should my /etc/apt/sources.list contain?

Or is there another way?

By the way I am a newbie with Linux (maybe obvious).

---

### Post by Sef on 2006-05-16
It is not a good idea to convert Debian to Kubuntu.  Even though Kubntu is based on Debian, it doesn't use Debian's repostitories.  Best to install Kubuntu itself if you want it.

---

### Post by az on 2006-05-16
[QUOTE=rustleg]So my next idea is can I convert Debian Stable into Kubuntu. Maybe by editing /etc/apt/sources.list and running aptitude dist-upgrade? In which case what should my /etc/apt/sources.list contain?
[/QUOTE]

It could work.

Change the lines in sources.list to point to (if you are in the us)

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 

see here:
[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)

save, and then run

sudo apt-get update

and 
sudo apt-get dist-upgrade


You may need universe installed.  Just asdd universe to the end of that line and update and try again.  It may not be a pretty upgrade, but it should work fine.  Just don't keep both debian and Ubuntu sources active.  Pick one or the other.

---

### Post by rustleg on 2006-05-16
I have actually already tried what you suggested, although I didn't include universe. The dist-upgrade went through but the X server wouldn't load so left me with a bare terminal which at my stage of Linux knowledge (about zero plus .001!) I couldn't go forward with.

So I trashed this version and spend half a day trying to install Kubuntu from scratch. I finally found a combination of partitions on my hard drive which the installer recognised and managed to install it. It seems the installer is not as good a Debian Sarge's at detecting the partitions - I think Sarge must take its info from the MBR whereas the Kubuntu installer just tries to look directly at the drive -which in my case won't work because I have many primary partitions on it (managed by my boot manager)

Anyway thanks for the response.

---

