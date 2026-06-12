---
title: "Cannot Install Dapper Drake"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2006-06-10
I cannot install DD.

The CD crashes.

this is STUPID!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Fix the bloody installer!!!!!!!!!!!!!!!!

-----------------------------------------------------------------------

Okay...I've calmed down.

Tried to upgrade from BB to DD on DUAL boot laptop (XP)

System crashed --- Lost EVERYTHING.

Wiped LINUX partion.  Extended NTFS to full disk, erased GRUB.

Will resize NTFS with GParted LIVE CD and then try again.

This is REALLLLLLLYYYYYYYYYY dissappointing.  I wish DD had been properly beta tested.

---

### Post by John.Michael.Kane on 2006-06-10
cement_head if your using the Desktop CD, and are having problems please try the [**Alternate install CD**]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso") burn the iso at a slow speed, and run md5checks.

---

### Post by frogotronic on 2006-06-10
[QUOTE=SD-Plissken]cement_head if your using the Desktop CD, and are having problems please try the [**Alternate install CD**]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso") burn the iso at a slow speed, and run md5checks.[/QUOTE]

Okay.

Problem seems to be that I cannot resize the NTFS partion.

Not with the Ubuntu DD CD, Not with the GParted LIVE CD.

Ran a disk check under windows - came up clean.

I'll try the alternate DD CD.

---

### Post by frogotronic on 2006-06-11
Success!

Okay, it took me a whole day.  First, Let me say that the upgrade from BB to DD was extremely frustrasting and caused a lot of mental anguish. ](*,) 

Luckily, I was waiting for Dapper Drake before I went entirely over to Ubuntu (on ly laptop).  So I had all my data files backed-up; so that was good...very good.  BUT I lost all my configuration.  In all fairness, I've buggered my platform upgrading windows - but that's neither here nor there.

_First Problem: X-server/GNOME hang_

I could not resolve this problem - I believe it was a NVIDIA driver issue.  I had to wipe the entire ext3 partion and do a clean install.  I am running XP/Ubuntu as a dual boot and managed to screw up the GRUB and the MBR.  Used XP install disk, choose 'R' option and typed the term 'fixmbr' to fix the MBR and then ran a "chkdsk C: /f /r" under windows.  Had to do this several times and then the everthing seemed okay.

I resized my NTFS partion to include the entire drive (single 40 GB HDD) using GParted LIVE CD.  Windows booted clean (I think this step is important, if you car about windows)

_Second Problem: Install_

  To be fair; after everything was okay on the windows side, I then resized the NTFS to back to 20 GB and left 20GB blank/unallocated. Then I did a clean install of DD.  Everything went okay.  I tried to do the manual partion which was straightforward and intuitive under BB and I couldn't make head or tails of it in DD.  This GUI needs work, and more explanation.  Especially as MOST people will first try Ubuntu/LINUX as a dual boot situation, or as a second HDD.

  Going back and choosing the install on largest free partion worked.  DD is now installed.

_Third Problem: Wireless Networking_

  Wow, what can I say?  Supposed to be easier under DD - in my case it was much more difficult.  Luckily I have a MN720 microsoft wireless card (discontinued, I believe) which has a Broadcom chipset.  This [wireless install guide]("http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear") worked for me.  Wireless is a bit clunky; but working.  Don't know what to do if you have a non-Broadcom chipset.

  I'm a BIG fan of the GTK WiFi project as it has allowed me full functionality in ubuntu as per windows when it comes to wireless.  Seems to have a few issues in DD.  Will post more when I troubleshoot it all.

_Fourth Problem/Issue/Resolution_

  I downloaded AUTOMATIX and ran that - it got me plugins, Java, and NVIDIA drivers.  I'll try installing the latest NVIDIA drivers in a bit.  But AUTOMATIX resolved clunkiness issues with wireless, when I downloaded the laptop wireless support "package".

**OVERALL** 

DD looks and feels A LOT nicer.  The install is more difficult than BB; which is unfortunate.  This needs to be resolved - It seems not only Microsoft rushes things to "market".  BUT at least we (I) can fix the problems. To me, this is the HUGE and most attractive reason to use UBUNTU.

L8R
- CH

---

### Post by JohnBoy55 on 2006-06-11
Something that may be helpful for future installs not to mention hdd crashes is imaging your drive. I've managed to keep my sanity by using Norton Ghost to make a backup of my drive before I upgade or radically change something. If I screw something up (and I usually do), I have a recovery path. Good luck!

---

### Post by pjbgravely on 2006-06-14
You made your life harder by deleting your Linux partitions and expanding the NTFS partition. Next time just reformat the Linux partitions. To make it even easier, make a / and a /home, so you only have to formate the / partition when things go wrong, and you don't have to restore your data from backup.

Paul

---

### Post by frogotronic on 2006-06-15
[QUOTE=pjbgravely]You made your life harder by deleting your Linux partitions and expanding the NTFS partition. Next time just reformat the Linux partitions. To make it even easier, make a / and a /home, so you only have to formate the / partition when things go wrong, and you don't have to restore your data from backup.

Paul[/QUOTE]


Yep, you're right.  It's a STEEP learning curve.  I seem to always have to make every mistake before I don't.

Anway, it pretty good - someprinting hassles from DD to networked, or XP connected printers

-CH

---

