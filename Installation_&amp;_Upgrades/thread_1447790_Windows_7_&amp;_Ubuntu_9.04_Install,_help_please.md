---
title: "Windows 7 &amp; Ubuntu 9.04 Install, help please?"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by sh4rkbyt3 on 2010-04-05
I'm (hopefully) ready to jump into the world of Linux.
 
I have a few questions though that I need some advanced users to answer, if you would please:
 
I am using a 1Tb drive with Windows 7 x64 installed.
 
I would like to put Ubuntu (9.04) on a separate drive (320 Gb) because of conflict issues I've had before using Ubuntu and Windows (XP/7) on the same drive. 
 
1) Is this possible? Would it be a complicated mess to do so?
2) Would I have to install Ubuntu 9.04 in x64 bit version since it would be on a seperate drive? 
3) Would Ubuntu be the best OS for me to use or would another Linux OS be better given these facts?

---

### Post by Naitsirhc Hsem on 2010-04-05
1) yes, not complicated
2) you can choose 32 or 64 bit
3) ubuntu is userfriendly and supported by many other programs

---

### Post by RedSingularity on 2010-04-05
If you are installing Ubuntu to a separate drive I suggest you unplug the drive your not using during the install.  That way there is no chance of grub being overwritten.

---

### Post by oldefoxx on 2010-04-05
I do not agree with the unplug drive notion.  Yes, it leaves the unplugged drive intact, but changes the drive identification and other boot options that should show up under grub.  And it is not necessary.

Start the install.  You get to the partitioner phase, you have three choices about how to proceed.  Take the manual, or last one.  You then get to tell the partitioner exactly which partition(s) to use and for what.  I always just designate root (/) and swap.  The others just go along with /, unless you specify otherwise, like a different partition for /home.  You can make a number of partition changes while there if you want.  Don't ask for a new partition table unless you just want to completely wipe the contents of that whole drive.

That should do it.  At the final step, where a list of things to be done is shown, there is an Advanced button.  Here is where you tell it where to install the /boot/grub setup, or whether to not do it, and the default is (hd0), which effectively means /dev/sda1.  You change this to (hd1), you want /boot/grub on /dev/sdb1 instead.  This works best on some PCs, usually those equipped with both EIDE and SATA drives, since in some cases they put one interface ahead of the other in the scan order.

---

### Post by Mark Phelps on 2010-04-06
Well ... everyone has their own opinions ... and I have mine.

While unplugging the driver is not necessary, I have found it to be a good way to ensure that no damage is done to the MBR or partitions on the other drive.

So, I highly recommend that approach.

Also, I do this all the time and have had absolutely no problems with GRUB or the new GRUB2 with doing this.

Using GRUB2, it's a simple matter to reconnect the Ubuntu drive, boot from that drive, start Ubuntu, open a terminal, and enter "sudo update-grub".  GRUB2 will then find all the kernels and OSs on the system, adding the needed entries to the GRUB menu.

I've done this several times and found it to work flawlessly.

---

### Post by sh4rkbyt3 on 2010-04-06
Thank you sincerely for the quick replies AND the advice.
 
Not to start an argument but I am liking Mark's idea and Red Singularity's a lot. I've tried installing Ubuntu versions 8.10, 9.04 and the new Karmic to a dedicated partition on my hard drives and it's ruined 3 drives previously by locking the MBR and the version of Windows OS and Linux I was using (XP, Windows 7 beta, Windows 7) to the point where I could not gain back the space from either OS (Linux or Windows) and the drives geometry changed severly thereby ruining the drives. 
Several NLTDR errors show up when the drive is scanned (mapped) independently but cannot be repaired or wiped.
 
The results of Windows and Linux interactivity so far have been nothing short of completely disastrous and expensive for me. 160Gb HDD locked, 320 Gb HDD locked, 500Gb HDD locked.
Portions of all the drives are still available so I use them to archive some programs but at this point I can't continue to buy drives and know that each time my MBR is going to be corrupted and portions of the drive will be made unavailable.
 
So I need to remove my C:\Windows drive and install the secondary drive (F:) and install Ubuntu on it. Update GRUB 2, turn off computer then reinsert the C:\Windows drive and it will automatically be recognized and everything configured properly?

---

### Post by Calash on 2010-04-06
> The results of Windows and Linux interactivity so far have been nothing short of completely disastrous and expensive for me. 160Gb HDD locked, 320 Gb HDD locked, 500Gb HDD locked.
Portions of all the drives are still available so I use them to archive some programs but at this point I can't continue to buy drives and know that each time my MBR is going to be corrupted and portions of the drive will be made unavailable.

What happened to the drives to cause parts of them to be inaccessible?  Nothing in the MBR, short of forcing a totally incompatible MBR onto the drive, should be causing data issues.  Unless something else happened you should be able to repartition the drives to be able to use them again.

---

### Post by setyo wirawan on 2010-04-06
i use windows 7 and Ubuntu 9.10.. There is no problem.. still work together.. first i install windows 7, just like another instalation.. then after that i instal Ubuntu 9.10..

---

