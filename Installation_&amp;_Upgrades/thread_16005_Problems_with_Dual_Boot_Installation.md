---
title: "Problems with Dual Boot Installation"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by caiphn on 2005-02-18
Hello all, I had a very unproductive day yesturday unfortunately.

I got a copy of Partition Magic to partition my existing 80 gig Windows XP Partition, split it into two 40 gig partitions. I had recently downloaded the Ubuntu installation. I booted up the Ubuntu installation but something had gone wrong with the partitioning and it wouldn't let me install Ubuntu properly, and I ended up having to reformat completely, thus loosing the XP part. No biggie, I had just backed up less than a month ago. 

I reinstalled Windows XP and partitioned the first 40 gigs using the Windows XP INstallation CD for windows XP, planning on using the other 40 for Ubuntu. After formatting and installing Windows XP, I got 'invalid operating system'. I do a search and apparently this is due to the MBR with incorrect information, so a fdisk /mbr seemed to fix it so when I did the Windows installation again, it went through.

There was a problem with the Ubuntu CD so I had to redownload it, and reburn it. Apparently I had burned it too fast as it couldn't get past 8%. When I ran into this snag, I went to boot back into Windows XP (Which I loaded on the primary partition of the first HD as I read that it has to be located on, and which had just been correctly reinstalled earlier in the day as I messed up the first time) but I am getting invalid operating system AGAIN now. I tried to run fixmbr and fixboot, not knowing what to do and just seeing these files available and running a /? with them they seemed to apply to my problem. (These are available on the Windows XP CD) I am at a loss as to how to boot back into XP in order to re-burn the Ubuntu so I can continue with the installation. I'm assuming the reason this happened is because Grub was not installed which would have acted as the bootloader, although of course as a total newbie I'm not sure why it happened again, although it's obviously something to do with the MBR. Anyone have any ideas, or should I just reformat and reinstall XP again? :?

---

### Post by caiphn on 2005-02-18
Hmm.. unlelated to initial problem but I redownloaded Ubuntu on another computer as I wanted to still try to install it on the other partition, and I reburned it .. and now when I first press enter when it starts I get a 

uncompressing Linux

crc error

system halted.

I'm going to try to rip another copy of this.. I've never had any problems with these CDs before but they're definately becoming problematic.

---

### Post by caiphn on 2005-02-18
I made another copy and the exact same thing is happening. I'll try it on another computer and see if that makes a difference.. I used nero to burn them all (the two that crash and the one that crashes at 8%)\


---- EDIT ----

Nah, get the same error on both computers. Not sure what happened, maybe the image I downloaded got corrupted somehow.

---

### Post by yazdzik on 2005-02-19
Dear Cai,
  What version did you download?  The installer must have a very recent libparted, or you must have LBA enabled in your bios, else the windows install reads the disk geometry one way, and linux another.  Then, affter partitioning, there is no was for the windows nt loader to find the OS,  and fixboot/fixmbr will not help.

If, on the other hand, you simply did not get far enough to install a boot loader, the windows command console commands should still work, presuming the geometry read is the same.


See the article :  [http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/).

All good wishes,

Yazdzik

---

### Post by caiphn on 2005-02-19
Yazdzik,

I downloaded version the i386 version 4.10. Something must have happened in the downloading as I have two CDs with the exact same error.  :-? I will take a look at the article right now, thank-you for taking the time to respond to me.  :-)

---

### Post by stoneguy on 2005-02-19
[QUOTE=caiphn]I downloaded version the i386 version 4.10. Something must have happened in the downloading as I have two CDs with the exact same error.  :-?[/QUOTE]

I had problems like this d/ling a Linux ISO awhile back. It wasn't until the 4th try that I got one that matched its published MD5. Weird thing was, the 1st 3 tries had the same wrong MD5 checksum. Thank goodness distros supply them.

---

### Post by bored2k on 2005-02-20
[QUOTE=caiphn]Yazdzik,

I downloaded version the i386 version 4.10. Something must have happened in the downloading as I have two CDs with the exact same error.  :-? I will take a look at the article right now, thank-you for taking the time to respond to me.  :-)[/QUOTE]


I had ubuntu problems while installing when it came out at the beggining. The problem? My HDD was not that ok... it wouldnt install

Download ur ubuntu and from the same site get the MD5SUMS, and test ur dled image , if the numbers are equal, the CD is OKAY.

If problem persists, try DL HDD Regenerator for it to check for HDD cluster errors .

---

### Post by wallijonn on 2005-02-20
You may need to boot from the WXP install CD, go into recovery mode, then copy ntldr and ntdetect.com to c:/

That may fix your problem.

---

### Post by caiphn on 2005-02-21
What I did is I just redownloaded a third time, and it liked the CD. At that point when grub finished installing I was able to boot into Windows again. :)

---

### Post by wallijonn on 2005-02-21
Congratulations. Now the real fun begins... You'll probably want to head over to the HOWTO/FAQ section. (You can take a shortcut by hitting the button in my signature).

---

