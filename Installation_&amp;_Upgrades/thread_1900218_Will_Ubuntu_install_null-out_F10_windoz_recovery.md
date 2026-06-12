---
title: "Will Ubuntu install null-out F10 windoz recovery?"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by johnbessa on 2011-12-25
I apologize if this has been asked before...

I want to find out if my F10 recovery button will work (on a Vista-era aprox. 2008 SONY Vaio laptop) if I install Ubuntu on its own partition.  I am assuming Ubuntu will overwrite the initial MBR.  I have looked but I cannot tell how the F10 boot works, if it is in the MBR or in some firmware.  Most pages discussed the situation after-the-fact.

TIA, John

---

### Post by uteck on 2011-12-25
When I schrunk my Win7 partition to make space to install Ubuntu on my Samasung laptop, I still have the Windows recovery boot option that grub picks up.  The new version of grub that has been used by Ubuntu for the last year or two looks at each partition on all drives to see what is installed there.
I am not familer with the Sony F10 boot, but I imagein it is just a way to boot into the recoverey partition, so installing Ubuntu should not affect it, but if it does, you will still have an entry in grub that you can choose from.

---

### Post by iiiears on 2011-12-25
Hello,

You may want to check out the windows recovery command line.
Particularly fixboot and fixmbr.
 
  Lose your recovery partition and you are possibly stuck purchasing a Windows Installation disk for 100+ dollars with no guarantee you will have all the drivers you need pre-installed. This is particularly true with a laptop. Special keys and features might only be supported after downloading a driver from the manufacturers website. 


I would make a disk image of the recovery partition before installing Linux. partimage live cd or ghost or seatools (there are other free tools offered by your drive manufacturer.)This will require a couple of hours, an external drive cdrom/dvdrom/usb/firewire/esata and before commiting to anything test your backup to see if it boots. Do it on another machine or disk by shrinking that more easily restored partition if you must. 

Don't have an external disk? Try ebay for a used 30gb - 100gb (Less than $50) and an external drive case (less than $15)
 It's great to have all install images and drivers and any files, saved games in one place.

---

### Post by Mark Phelps on 2011-12-26
> **johnbessa said:**
> I want to find out if my F10 recovery button will work (on a Vista-era aprox. 2008 SONY Vaio laptop) if I install Ubuntu on its own partition.  I am assuming Ubuntu will overwrite the initial MBR.  I have looked but I cannot tell how the F10 boot works, if it is in the MBR or in some firmware.  Most pages discussed the situation after-the-fact.

TIA, John
Most probably -- it will NOT work if you do that.

Couple of possible reasons:
1) Size -- if you shrink the Vista partition to make room for Ubuntu, the recovery utility may not then be able to restore to that partition because it's too small.
2) Presence of Linux filesystem -- likely that the recovery utility will try to reformat the drive to prep for restore, and the presence of a Linux filesystem could confuse it.

Best bet, if you want to be able to restore Vista later, is to use a partition imaging tool (like Free Macrium Reflect) to image off the Vista partition to an external drive, and also use the option to create a Linux Boot CD.  That way, if you later want to restore Vista, just boot from the CD, connect the external drive -- and run the MR Restore.

---

### Post by johnbessa on 2011-12-26
Hi guys, thanks for the replies.

There is no reason the recovery drive should get written over, it is just the MBR that I am concerned about, and I don't know how the F10 boot works, if it accesses the MBR or has firmware that goes to the partition in a hard-wired sort of way.

I actually do, and/or, grok all that you suggest.  I have a 2 terabyte drive that I use exactly for that.  Bottom line for me is that I HAVE to have MS Word 2007 for school--pure nazi-like oligarchy, like learning masters psychotherapy under hitler, no ifs ands or buts.  (But they will get theirs in the end, as they did last time 'round!  --Uncle Bob, RIP, North Africa to Berlin)

I "chunk" my windoze just like Unix, but with the desktop as root.  I also have a tcsh shell that runs in cmd line (rare item from 15 yrs ago) that runs at the root level on the C:/ drive unlike cygwin, which is dozer compliant.  And I would really like to go back to XP, but it isn't possible w/ laptops.  Emulation is a possibility, but from experience there is a major performance hit (could be wrong), and probably a long list of got-yas.

So all my data is managed uniformly across all OSs, and I hope to finally get an L4 posix environment going to get to the next step, despite resistance, which is technically homeostasis.  The resistance is here as everywhere, is linked to the oligarchy problems above--the problem is spread equally across all humanity, is the basis of civilization, and is both genetic and maladaptive.

---

