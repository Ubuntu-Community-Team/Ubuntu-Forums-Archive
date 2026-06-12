---
title: "Trouble Installing even with Alt Install CD"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by PSyMastR on 2006-11-29
Hi, for a while now I have been using Ubuntu on my laptop (Since 5.04) and have constantly either reinstalled completely or upgraded all the way to 6.10.  Now, I want to install 6.10 on my computer.  I have tried the regular install CD, but it never boots into GUI mode to install, weather if I use splash, quiet on or off, splash off, etc...  It keeeps giving me errors with the irq and tells me to boot with irqpoll, I do that, still doesn't work.  So , then I decide to try the Alternative install CD.  I do a text line boot, with irqpoll added at the end, just to be safe.  It partitions just fine, etc...  Yet, it freezes at 6% in the "Select and install software" section, and eventually gives me this error:

An installation step failed.  You can try to run the failing item again from the menu, or skip it an choose something else.  The failing step is: Select and install software.

Now, its weird, because I was able to install 5.04 on my computer a long time ago, but now even that is giving me problems with the same hardware.

P4 2.8 Ghz
ATI Radeon x700pro 256mb
1 GB DDR2 ram
80 GB HD (Using SATA cables as first master)
250 GB HD (USing SATA cables as second master)  This is where I am installing linux to.  A 14.9GB partition at the beginning of the hard drive, followed by the swap.  Then the rest of the hard drive is NTFS full of files.  (I have XP installed on my 80GB hard drive)

I am using a very old 24x speed CD rom drive, I also have a SD/CF/MS/xD card reader internal that it keeps trying to mount as well, would that cause any problems?  Just wondering.  Thanks in advance.

EDIT:  The package it cant seem to get is /pool/main/e/evolution/evolution_2.8.1-0ubuntu4_i386.deb

EDIT2:  Here is the whole error:

```
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ Release i386 (20061025.1)]/pool/main/e/evolution/evolution_2.8.1-0ubuntu4_i386.deb MD5Sum mismatch

E: Unable to fetch some archives, maybe run atp-get update or try with --fix-missing?

0 upgraded 663 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B/439MB of archives.

After unpacking 1569MB of additional disk space will be used.

tasksel: aptitude failed (100)
WARNING **: Configuring 'pkgsel' failed with error code 1
WARNING **: Menu item 'pkgsel' failed.
```

---

### Post by finferflu on 2006-11-29
You should check those CDs you've burned using the utility provided (when you boot the CD), and see whether you burnt them correctly. Usually you should burn them at a really slow speed, I suggest you at least 4x.

Hope it helps, and good luck! ;)

---

### Post by Henry Rayker on 2006-11-29
I'm not certain, but it could be an issue with the SATA drives...or the fact that you have 2 masters...but I'm not certain on that one as I don't have a SATA drive at all =\

---

### Post by PSyMastR on 2006-11-29
I re-burned the CD, reinstalled, it finally completed the install, but now Ubuntu freezes at the bootscreen.  Just my luck. lol.

---

### Post by finferflu on 2006-11-29
Don't give up, just try to reinstall.

---

### Post by PSyMastR on 2006-11-29
I tried to reinstall, it did nothing.  What is going on :(

EDIT:  I have taken pictures of what happens.

Here is what it freezes as:
[img]http://img447.imageshack.us/img447/3167/pic0271vk0.jpg[/img]
Here is what happens if I try to go into console mode (Ctrl+F1)
[img]http://img447.imageshack.us/img447/193/pic0272ix9.jpg[/img]

---

### Post by finferflu on 2006-11-30
The only solution that comes to my mind now is installing Dapper Drake and trying to upgrade to Edgy... I'm sorry for you, I understand how you feel...

---

### Post by PSyMastR on 2006-11-30
I tried booting the 6.06 CD, and it all loads fine, but it crashes at the X server when it basically is about to load.

X Server Output:

```
Fatal server error:
no screens found
```

Now, I know for sure my screen works, or I wouldn't be reading the error lol.  Hmm...

I tried saving the detailed error to my USB drive, floppy, etc... but the command line version of the live CD gave me no access to it.  I tried every point in where ubuntu mounts stuff to, plus even tried mounting something and it showed a passthrough.  Anyway, it detected my correct graphics card, so I dunno.

---

### Post by finferflu on 2006-11-30
I think there something wrong with your xorg.conf, you should check carefully the xorg.conf file when you are shown the error...

---

### Post by wpshooter on 2006-11-30
PSyMastR:

Are you checking the integrity of your Ubuntu CD by running the verification test which is found on the initial Ubuntu boot screen menu, as was suggested to you in post #2 above ???

Have you tried cleaning your CD drive ?

Does your CD drive have the latest and greatest firmware installed ?

Are your BIOS on the latest released version ?

Have you ran memtest on your memory ?

Does you computer boot and run O.K. in Windows ?

Try reseating your video card.

---

### Post by PSyMastR on 2006-11-30
This is the 6.06 (live CD installer thingy) that was trying to boot.  I did nothing to the xorg conf.  Im still in the live CD, and can access it by nano.  Any suggestions on what to look for?  Sorry, Im new to the xorg stuff.

Oh, and thank you so much for helping me all this time.

---

### Post by PSyMastR on 2006-11-30
> **wpshooter said:**
> PSyMastR:

Are you checking the integrity of your Ubuntu CD by running the verification test which is found on the initial Ubuntu boot screen menu, as was suggested to you in post #2 above ???
**Yes, many times.  6.10 was checked and double checked, 6.06 was checked, even though its factory pressed by Canonical Ltd.**
Have you tried cleaning your CD drive ?
**Yes**
Does your CD drive have the latest and greatest firmware installed ?
**Yes**
Are your BIOS on the latest released version ?
**Yes, as a matter of fact, I just updated it yesterday and tried again to make sure, it wasn't that much of an update though.  My mobo is very new.**
Have you ran memtest on your memory ?
**Yes, many times**
Does you computer boot and run O.K. in Windows ?
**Yes, GRUB boots windows perfectly fine, and so does the standard windows installer.**
Try reseating your video card.


Hope that answers some confusion.

---

### Post by wpshooter on 2006-11-30
Then I would try this.

Back up all of your info on your 250gb drive.

Then get KILLDISK program and WIPE everything off of that drive.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then attempt to install Ubuntu.  And make 3 partitions for Ubuntu: /root, /home, and /swap. Make Ubuntu partitions, type ext3.  And make another partition for your other info.  Might want to consider partitioning that one as FAT32.

Good luck.

---

### Post by PSyMastR on 2006-11-30
Im going to have to get another 250 gig drive to back it all up.  Its 210 gigs of data lol.

I think it may be an incompatability with my graphics card and xorg no?

Device "ATI Technologies, Inc.  Radeon X700 Pro (RV410)"

---

