---
title: "Alernate CD fails testing"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by jerryduk on 2008-08-01
I have downloaded the alternate CD and run the checksum which all appears OK.

When I test the CD the following file fails as corrupted ./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.24.19.21_i386.deb

I have burnt the .img twice and the same file fails both times. I am now downloading the file again. Is there something else I should do? 

Thanks

[COLOR="Red"]Update - for whatever reason on about the sixth attempt it burned fine and the CD checked out. Thanks to all those commented. If this helps anyone in the furture just keep trying, change media, change recorder if possible, change software and eventually it should work.[/COLOR]

---

### Post by Herman on 2008-08-01
If the md5sum for the file you downloaded is right then your .iso is okay and it won't be any help to re-download the same .iso file again.

Make sure you use good quality CDs or DVDs, and if you still have trouble, maybe you need to check your hardware. 
Maybe I'm different because I live in a dusty environment, (a small Australian 'outback' town), but I find that my computers tend to suck in dust and occasionally, the optical drive lenses may need a wipe. (Once in a 'blue moon').

I have also had trouble with batches of cheap CDs. People tend to buy the cheapest they can get, so sometimes the cheapest ones are all the store sells. For most people the quality doesn't seem to matter much. 

It seems like we can get away with using cheap CDs and a slightly dirty CD drive for everything else except installing Ubuntu. Maybe it's because there's so much software packed into one CD.

What software are you using to burn the .iso to disk? I'm also wondering if it might have anything to do with the CD writing program you're using or your settings, as files beginning with a . are hidden files, so there might be a problem copying the hidden file with your software or settings? (Just another guess, I'm not sure).

---

### Post by mikewhatever on 2008-08-01
Check the downloaded iso file before burning.
[https://help.ubuntu.com/community/BurningIsoHowto#MD5%20Sums](https://help.ubuntu.com/community/BurningIsoHowto#MD5%20Sums)

---

### Post by zvacet on 2008-08-01
I supose that you still have iso which give you trouble.Download same iso with torrent and point download to the folder with existing iso.Torrent will just check for corrupted files and replace it with good ones.After that check md5sum again and burn iso on lower possible speed and check disc integrity.If everything is fine go for install.

---

### Post by Partyboi2 on 2008-08-01
Try using another burning program to burn the disk at a low speed, I suggest [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") if you are using windows, which is a small program (a couple of mb) Has always worked for me.

---

### Post by jerryduk on 2008-08-02
Thanks for comments so far: I have tried using three different burn packages including imageburn. I have now had two different files come up as corrupted. I have been using RW CDs and perhaps that's a mistake? Maybe I need to use a write once version?

If the ISO passes the MD5SUM check is the ISO OK or could it be corrupt? or contain a corrupt file.

May try torrent next ????

---

### Post by Herman on 2008-08-02
If your downloaded .iso file passes the md5sum check then it is okay and you don't need to re-download the same file again. 
Look for a problem somewhere else instead.

I have had good luck with CD-RWs and bad luck with some CD-R discs. A few other people claim the opposite. I think as long as you buy good quality optical discs it doesn't matter if you use CD-RW or CD-R or DVD, etc., as long as your optical drive supports the type of disc you're trying to burn.

Maybe try copying the .iso file to a USB flash memory or a data CD and take it to a freind or relative and see if their computer can burn it to disc successfully. If it still doesn't work try a different blank CD-RW or a new CD-R or something, sooner or later your luck will improve. :)

---

### Post by jerryduk on 2008-08-02
I have tried burning the CDs on two different machines and always they fail the CD check in ubuntu but at different files. I'll keep trying.

---

### Post by Sef on 2008-08-03
> I have tried burning the CDs on two different machines and always they fail the CD check in ubuntu but at different files. I'll keep trying.

Happens at times.  Once it took me about 6 downloads to get a good md5sum match.

---

### Post by confused57 on 2008-08-05
> **jerryduk said:**
> I have downloaded the alternate CD and run the checksum which all appears OK.

When I test the CD the following file fails as corrupted ./pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.24.19.21_i386.deb

I have burnt the .img twice and the same file fails both times. I am now downloading the file again. Is there something else I should do? 

Thanks

[COLOR="Red"]Update - for whatever reason on about the sixth attempt it burned fine and the CD checked out. Thanks to all those commented. If this helps anyone in the furture just keep trying, change media, change recorder if possible, change software and eventually it should work.[/COLOR]

Glad you finally got it to work, thanks for the update...your persistence paid off.  I had a similar experience recently trying to install Hardy 8.04.1, using the alternate cd, on my sister's older pc.  The alternate installer would fail at 6% at the Select & Install Software, fortunately I had carried 2 different alternate install cd's with me at the time I was trying to install...the 2nd cd stalled at 6% for 10-15 minutes, but eventually completed the installation.  Her cd-rom drive is old & probably dirty, which is more than likely what was causing the problems.  I had previously used the alternate install cd's to install Hardy on one of my pc's, so I knew they were good.

---

### Post by karachuonyo on 2008-08-05
Same thing happened to me with Kubuntu 8.04 and Ubuntu 8.04 iso when veriying the burned d with K3b. It fails with an error but when I do a cd check before installing it passes. BTW I always use cdrw because every 6 months i do a fresh install of new version and just overwrite the old cd image.

---

