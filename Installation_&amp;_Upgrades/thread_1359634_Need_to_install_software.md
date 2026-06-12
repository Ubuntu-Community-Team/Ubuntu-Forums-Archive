---
title: "Need to install software"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2009-12-19
I'm a Linux newbie and don't know how to do a lot of things.  Five months ago,  I asked a friend at FreeGeek Columbus to delete the extaneous operating systems from my computer just leaving the one I used, and he accidently deleted them all. “No problem,” I said, “I'll just reinstall when I get home.”
 
 But everytime I try to reinstall K/Ubuntu, I get an error message saying 
 			Installation Failed
 			The installer encountered an error copying files to the hard disk:
 			[errno 5] Input/output error
 			. . . 
 
That happens with four Ubuntu installation Cds, three live Ubuntu Cds, one Kubuntu live CD, and one Fedora live CD. I suppose there's a problem with my DVD rom.  PCLinuxOS and openSUSE, however, do install, so those are what I've been using (I've only recently ceased with openSUSE, for the time being).

Today, however, I got lucky trying out something different.  I used an Ubuntu 9.04 alternative CD (not live as they abort when they come to the input/output error message) to install the base system and grub with lvm.  It allows me skip over software installation which is where the input/output error message happens.  It boots to a command line.  I don't know what commands to use to get the software to install from a mirror, or how to install repositories from the command line.

Will someone help me out here?  I've never had Kubuntu, per se (only Ubuntu with the KDE desktop); so since PCLinuxOS GNOME 2010 (a rolling distro) is more stable and polished than Ubuntu 9.10, I'd like to fill my base system out with Kubuntu software.

Any and all help and direction would be very much appreciated. By the way; 10 months ago, I didn't know what an operating system was and had no clue about even the notion of free source technology.  For me, computing started with Hardy Heron and I really miss Ubuntu.  Please help me get home. :P

---

### Post by sgosnell on 2009-12-19
Did you verify the md5sum for the downloaded .iso files, and check the integrity of the burned disks?  Getting a bad burn is all too common, and it may just be a bad CD, or a corrupt .iso.

---

### Post by Randymanme on 2009-12-19
No to all of the above.

Do I need to do that with the CD I used today?

---

### Post by sgosnell on 2009-12-20
I would recommend it.  Boot from the CD, but select the option to check the disk for errors.  If none are found, check the md5sum of the .iso you downloaded.  Instructions are [here](https://help.ubuntu.com/community/HowToMD5SUM).  Some people say that downloading via torrents is more likely to give a good .iso.

---

### Post by Randymanme on 2009-12-20
"./pics/logo-50.jpg file failed the Md5 checksum verification.  Your CD or this file may have been corrupted."

I burned the CD (along with about 6 others) somewhere in the area of six or seven months ago.  What do you suggest next?

---

### Post by sgosnell on 2009-12-20
Download a fresh .iso, preferably using torrents.  Verify the md5sum, then burn to CD, and verify the integrity of that before trying to install.  Burn it at the slowest speed you can tolerate.

---

### Post by Randymanme on 2012-09-20
Thank you very much.  Sorry to have neglected to say, "Thank You."

Thank you very much.

---

