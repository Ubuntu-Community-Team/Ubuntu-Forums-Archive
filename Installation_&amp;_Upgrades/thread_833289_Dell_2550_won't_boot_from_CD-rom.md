---
title: "Dell 2550 won't boot from CD-rom"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by yalkshire on 2008-06-18
Hi guys,

I was hoping to get some help from this forum. I've installed ubuntu and kubuntu before on several PC's and used its user-friendly interface. However, that's about it. I never did anything "tricky" or had any problems untill now.

I got a DELL 2550 server from my work, it was either that or they threw it away. Of course I wanted the server, even if it's only to experiment. There were no licenses/software/drivers included with the server. The DELL has always been running on windows server 2003. 

I tried to fire it up with a CD-rom from ubuntu (bios is with CD-ROM as first boot sequence). That didn't work (couldn't find any bootable device). Just out of curiousity I tried putting in a windows XP CD. it booted fine, tried an installation, XP installed. 

I've tried booting ubuntu with a USB stick and a CD-rom, but it keeps telling me that it couldn't find anything to boot from.

Any help/tips are greatly appreciated.

I have a floppy disk as well, if that might be necessary like in the win95 days.

thanks!

---

### Post by avtolle on 2008-06-18
You are using the server iso, yes? Some thoughts on things to check/consider. 1) Did you check the md5sum of the iso after download? 2) Burning to CD-R at a low speed (4x) is what I do, and my elderly h/w handles this; any faster or on CD-RW, no good. 3) Given the problem with the USB stick (presuming you were using the same iso to install on the USB stick) I think there might be a problem with the iso as downloaded. 4) Just in case you were using a Live CD for the boot attempt, I'd try the alternate install CD instead (text based installer, installs full system) as it works in many situations where the Live CD doesn't. 5)How much RAM does the old beast have? If <384 mb, and if you're trying the Live CD, use either the alternate CD or the server iso. Apologize for the rambling and somewhat disconnected nature of this.

---

### Post by wpshooter on 2008-06-18
Have you tried to boot that server to a WIN98SE bootable diskette ?

P. S. - Is the Ubuntu CD that you are using to attempt this installation the SAME Ubuntu CD that you had successfully used on other computer ?

---

### Post by yalkshire on 2008-06-19
hi guys,

to answer your questions:

yes I used the same CD-ROM which I used to install my other computer.
The server has 2GB of ram (2 times 1GB)
The USB stick has indeed the same ISO as the CD-rom.
I've tried WIN98SE floppy disk and it boots fine.

I'll try the text-based installer this evening and burn the CD-rom at a lower speed (16X for the moment) so I'll try 4X instead.

thanks for the help guys!
I'll give an update this evening.

---

### Post by yalkshire on 2008-06-19
as promised an update :

I burned the alternate CD and watcha know, it booted up this time!

choose install ubuntu but it crashes on loading the installation modules on 0%. Maybe there was a problem with the CD/wrong MD5checksum so I redownloaded the ubuntu with the MD5, checked everything, reburned the CD at speed 1X (damn that's slow) and everything went OK on my PC side. Data check was fine as well. rebooted the server with the new CD and it crashes again...

Next I called up one of my friends if he still had some ubuntu CD's, and he did, version 5.04, mailed to him from shipit.ubuntu.org. So they're the original CD's. Okay it's an old version, but I'll download the updates afterwards if it works. Unfortunately it crashes again, now on 1% instead of 0%.

In all three cases I did a check on my pc afterwards if the CD was ok, and in all three cases it said on the server that there was a damaged CD, MD5 wasn't correct, or the data on the CD was corrupt. 

I double check all three CD's on my PC, and they turned out okay.

My CD-rom (installed XP from a CD-rom before), RAM (did a memtest), HDD (did a disk damage test) are all okay.

I'm all out of ideas on this one... :confused:

There might be one option left and that's doing a PXE boot (I get the option when booting the server). I've never done it before, and don't even know how to set it up. I only have a windows machine at my disposal for the moment which is probably going to make things 5 times harder than necessary. but I'm willing to give it a try. Otherwise I get my linux machine back next week thursday. Waiting a week won't kill me (I hope :sad:)

---

### Post by wpshooter on 2008-06-19
Yalkshire:

Have you considered that the CD-Drive on the old server may be defective ?

Have you tried cleaning the CD-Drive ?  Have you checked to see if perhaps the firmware on the CD-Drive needs to be updated ?

Have you checked the connections on the CD drive ?

Does the hard drive(s) on this computer have any remaining information, i.e. O/S, programs and/or data on them ?

If not, have you tried getting [www.killdisk.com](www.killdisk.com) and WIPING the hard drive(s) completely clean and then retrying the install again ?

---

### Post by avtolle on 2008-06-19
I think it is time to consider trying some boot parameters. I don't know what kind of hard drives are on the server, or if there's a RAID configuration, or whatever, so this first one is just "to try". As the system begins to boot, hit F6; there should come up a screen, at the end of which is a boot line. Add to the end of the boot line "all-generic-ide" (w/o the quotation marks) then hit b to boot, and see what happens. There are many of these parameters to try, and, if I have a bit of luck, I'll be able to give a more complete list (or a link to a post with a more complete list) shortly.

---

### Post by avtolle on 2008-06-19
[http://ubuntuforums.org/showthread.php?t=833492](http://ubuntuforums.org/showthread.php?t=833492) see post #3 for some other boot parameters to try, along with some links. HTH.

---

### Post by wpshooter on 2008-06-19
P.S. - Have you checked to see if perhaps the BIOS on your server may need updating ?

Also, why were they getting rid of the server in the first place ?

Have you ran Memtest to be sure that there is not a problem with the system memory ?

---

### Post by yalkshire on 2008-06-19
Hi all,

I've considered that the CD-rom may be defective, but as I after trying ubuntu the first times I also tried installing XP from a CD-rom. That worked fine. so I doubt it that there's something wrong with the CD-rom drive.

I've checked all connections within the server including the one from the CD-rom.

All hard disks are completely wiped out (company policy).

The BIOS is up to date (just checked)

They got rid of the server because it was tax deductable and because of the recent energy price rising it costed more to maintain the damn thing that it actually gained.

I performed a memtest with the alternate installation CD and this was fine as well.

I'll try the boot parameters now, hopefully that'll help.

thanks for the responses


EDIT : The crash nearly always happens on -- ./dist/hardy/main/binary-i386/Packages file failed the MD5 checksum verification. Your CD or this file may have been corrupted.

---

### Post by yalkshire on 2008-06-19
meanwhile I had an interesting development : booting from the live CD from version 5.06 which was also in my friends CD-rom case worked. Unfortunately the install option to the live CD was only added as of version 6.06 so I'm back where I started.

This proves there's something wrong in the install configuration which was (not) there before. I'm still experimenting with the parameters, but no luck so far.

---

### Post by wpshooter on 2008-06-19
Maybe I missed this but have you burned the ISO image to a **different** CD of high brand name quality, say either Sony or Imation ?

And when you are getting that recurring error message, is this when you are checking the ISO sumchecks or is it from the CD integrity check function that is found on the initial Ubuntu boot screen menu ?

P. S. - Have you tried installing Gutsy instead of Hardy ?

---

### Post by avtolle on 2008-06-19
Clarification for me, too; I inferred that you got the recurring error message when trying to install.

BTW, as a bit of a long shot, given the recurring error message about the denominated file, and you may just not want to try this, I suggest downloading the iso from a different mirror *just in case* the mirror (which I presume, subject to rebuttal) from which you downloaded previously has a corrupt file. A thought.

---

### Post by wpshooter on 2008-06-19
> **avtolle said:**
> Clarification for me, too; I inferred that you got the recurring error message when trying to install.

BTW, as a bit of a long shot, given the recurring error message about the denominated file, and you may just not want to try this, I suggest downloading the iso from a different mirror *just in case* the mirror (which I presume, subject to rebuttal) from which you downloaded previously has a corrupt file. A thought.

Yes, I agree, I thought of that but it slipped my mind to mention it.

---

### Post by ShadowHawk86 on 2008-08-13
I'm having the exact same problem actually. I've downloaded from two different mirrors(CA and CO), burned to two different CDs (Imatation and Memorex), and tried to install on two different 2550's. 

There is something happening with the 8.04.1 installer because as I said, I'm having the EXACT same problem (md5 matches, etc) where the install hangs between 0-2% and almost always on the mentioned file.

---

