---
title: "&quot;bad PBR sig&quot;"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by NightSky on 2006-08-12
Hi all. My first post in this forum!

OK, here's the deal:

I just installed Ubuntu desktop on my SCSI hard drive I had laying around.  After installing from the CD and rebooting, I get the message "bad PBR sig" right where the OS should load.  So my computer goes to the next boot device.

Here's my system specs:
Asus A7N8X-X with Athlon 2.1 2600
1st HD:  IDE 80GB Maxtor with my windows install
2nd HD:  SCSI 16GB Seagate where I'm attempting to install Ubuntu (controller is an Adaptec 2940U2W)


I'm guessing that Ubuntu is seeing my IDE drive as primary?  Unfortunately, I have no way to disable the on-board IDE controller so that Ubuntu would not see the HD.  I have to remove the HD from the boot order in the BIOS so it won't boot from it.

Basically, I would like to choose from the bios which drive I want to boot from.  In this case, it's set on SCSI but I get that error message.


On a side note, I tried Sun Solaris for the heck of it on the same setup and I had no problem at all booting from my SCSI drive.  But I've reformated the drive since then so I can install Ubuntu.

This is my main computer for windows since I'm using it as a "Tivo" PC using Snapstream Beyond TV.  I want to install Ubuntu so I can learn Linux.

Thank you all for your time!

---

### Post by NightSky on 2006-08-12
So no one can help me?  :( :(

---

### Post by NightSky on 2006-08-13
nevermind guys.  I dug into my computer to disconnect the ide drive so I can install onto the SCSI.  Now it works like a charm but I did not wnat to go as far as opening my PC.  

Thanks for the help anyway.

---

### Post by spasticus on 2006-11-09
you might want to enter your bios. I'm pretty new at this too, but I found some threads on dual boot.
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot)

these tell you how to boot if you've got two hard drives.  

Personally, I did what the above thread mentioned, and found that I could boot into ubuntu if I chose which hard drive to boot from, i. e. slave or master

However, when I chose XP the screen gives me bad pbr.

I looked into the jumper settings for my hard drives.  basically what I derived is this, if you can get the right jumper settings you should be able to boot into XP.

DOn't take my word for it.  It worked for me because I work with IDE, and the cables for the harddrives enable cable select.

---

