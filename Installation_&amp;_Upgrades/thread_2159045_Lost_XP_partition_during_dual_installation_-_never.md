---
title: "Lost XP partition during dual installation - never said goodbye !"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2013-07-01
After purchasing a used RM Mobile One 945, 2Ghz with 2Gb ram, and with xp pro installed, but no recovery disc, I used my live cd 12.04LTS disc to create a dual boot laptop.
At least that's what I thought I'd done.
During the installation, I've wedged 12.04 into 8Gb, thinking that I'd restricted XP to that size.
Customised 12.04 to my liking( Gnome Classic without effects) then discovered, when I rebooted that it went straight to the Ubuntu splash screen. No sign of the Grub(?) screen offering the usual choices along with XP, and no sign of the expected 60G disc in the file manager.

I've downloaded Bootrepair and run it, creating the info summary at [http://paste.debian.net/13758](http://paste.debian.net/13758)
and now have the initial screen I'm used to, but no sign of XP.
If I look at the Advanced Options/Other Options in Bootrepair, 'Repair Windows boot files' is greyed out.

So long since I've done an installation from scratch, and not used Bootrepair before, I can't remember what I need to do, so I'd be very grateful for a guiding hand.

(I do have xp recovery/installation discs for my Toshiba laptop, likewise for a Dell laptop, and a Win 98 system disc, but I assume none of these will be of help in recovering the necessary files, whatever they are.)

John

---

### Post by Mark Phelps on 2013-07-01
XP is gone.  There is no NTFS partition anymore.  Don't know what install option you used, but whatever it was, it reformatted the entire drive, wiping out the XP partition.

How did you do the repartitioning to make room for Ubuntu? Did you shrink XP using GParted and then create Linux partitions, or did you use the SLider in the installer? 

The complication now is that the Linux filesystem has ovewritten the Windows filesystem, and if you simply restore the XP partition, that will most likely destroy the Linux filesystem.

If you want to get the XP files back, you will need to be able to connect the drive containing those files to a Windows PC, download and install a Windows data recovery app, and run it against the drive.  IF you use RecoverMyFiles from Runtime Software, that will be able to reconstruct the folder and file organization that was there in XP -- but you will need to write that to a different drive.  And, to do the actual file recovery, you will have to purchase a license online.

You could also install EASUS Partition Master on that Windows PC to see if it can simply restore the former XP partition.  Sometimes, it can do that and it is free.

---

### Post by grey1beard on 2013-07-01
Thanks for the speedy reply, Mark. I think it best to draw a veil over what I might or might not have done - too embarassing !

New question then is to expand my current 12.04 partition to take up the full hdd.
Hardly dare touch it, but must bite the bullet, to mix a few metaphors.
Any quick advice, or link?
Regards
John

---

### Post by oldfred on 2013-07-01
You can just use gparted from liveCD to resize LInux / (root). You cannot do that from inside your install. Your not showing a swap but if you had one you would also have to click on swap and swap off as liveCDs use swap to speed things up.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

### Post by grey1beard on 2013-07-01
Thanks, oldfred.
Frustration took hold, and,having lost this copy of xp ( but I have it on my laptop), I reasoned that SWMBO didn't realy need it !
She has only been using Ubuntu since I got her past her technophobia, so that wasn't really an issue, just another possible backup.
So I'm starting the re-install from scratch - complete with /home and swap partitions this time.
Regards

John

---

### Post by oldfred on 2013-07-01
I finally shut my XP down about a year ago. I still have it on a connected drive but have not booted. I had promised myself to stop using it for years but had one app I was still using. But finally the Linux version was almost good enough, and it just was not worthwhile booting XP once a month for that app.

---

