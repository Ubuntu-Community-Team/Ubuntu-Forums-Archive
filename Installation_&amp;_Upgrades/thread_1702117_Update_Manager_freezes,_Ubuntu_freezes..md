---
title: "Update Manager freezes, Ubuntu freezes."
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by John Coulthard on 2011-03-07
I did a rather large (300+mb) update on my dual boot Dell Inspiron 1501. The download worked as expected. About 2/3rds of the way through the update the machine froze (it responded to nothing). Eventually I powered it down by holding down the power button for 10+ seconds. 

On reboot, WinXP works fine. Ubuntu get's to the splash screen with the machine name and freezes again. Trying Ubuntu 10.10 Recovery Mode gets down to 

"running /scripts/init-bottom ... done." ... then nothing but there is disk activity - which stops after about 20 seconds and I wait ... and I wait... Nope - it is dead. 

I couldn't figure out any way to even get into command line mode so decided to simply re-install Ubuntu. This is not proving to be as straight-forward as I had hoped. The best guide I have found so far is... 

[http://ubuntuforums.org/showthread.php?t=1577455](http://ubuntuforums.org/showthread.php?t=1577455) "how to reinstall ubuntu"

So I am back in my standard install CD again and choose advanced install. Now looking at "Allocate drive space". My current partitions and boot loader location are: 

sda1 (fat16) 90.4mb 
sda2 (ntfs) 58.3 gb 
sda5 (ext3) 56 gb 
sda6 (linux-swap) 2.4 gb 
sda3 (fat32) 3.2 gb 

Device for boot loader installation: /dev/sda ATA Hitachi HTSS54161 (120GB) 

I highlight sda5 and click on "Install Now".  

Result: "No root file system is defined - Please correct this from the partitioning menu." 

My reading, 

e.g. [http://ubuntuforums.org/showthread.php?t=1626263](http://ubuntuforums.org/showthread.php?t=1626263) 

suggests that /dev/sda is the correct place (which is the one it rejects). If I had my choice I'd skip this step as the machine boots fine in the sense that I get asked which OS I want and WinXP loads fine and Ubuntu at least gets going. 

I'm getting a little worried about the amount of flailing around I am doing. I really don't want to damage my WinXP, even though I don't use it very often. Intuitively it seems to me that this should be more straight forward than it is turning out to be. 

I guess at this point I would like advice about where to specify the root file system and some assurances that after that highlighting sda5 and clicking "Install now" that is all there should be to it (i.e. I am on the right track). 

Alternately I wonder if there is some way to get to a command line on my existing system and somehow manage to get the Update Manager to complete it's task - now that would be wonderful.

---

### Post by bayan.rafeh on 2011-03-07
I have been up that alley before. To specify the root partition simply right click /dev/sda5 then edit and specify the root folder as "/"(no quotes) Nothing will happen to your winXP partition since this is Ubuntu only and Grub will be reinstalled.

---

### Post by Hakunka-Matata on 2011-03-07
You can boot from an Ubuntu LiveCD and examine and work on (via terminal if you like) you disc installed Ubuntu OS.  Are there no older images to choose from on the Grub boot menu?  You say you can boot into Recovery mode, so you must be seeing the Grub Menu at startup?

---

### Post by John Coulthard on 2011-03-07
Thank you for the quick responses. 

Hakunka-Matata: Yes there were old images there to try and I did try them but got exactly the same response. 

bayan.rafeh: Thank you - as I enter this Ubuntu is in the middle of the installation process on my laptop :). It was a really trivial thing that was tripping me up - I didn't realize **I had to "double click" on the sda5 choice not merely highlight it.** Once I "double clicked" and it prompted me for the extra information all became clear and some of the stuff I read in the other discussions became much clearer. 

I'll mark this solved as soon as the installation process finishes completely.

---

### Post by John Coulthard on 2011-03-07
The install process appeared to go normally. The machine restarts after removal of the installation CD and I get: 

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) 
Pid: 1, comm: swapper Not tainted 2.6.35-27-generic #48 Ubuntu. 
followed by a call trace. 

The initial Grub menu comes up fine. I can choose WinXP and it starts ok. If I choose Ubuntu I get the above. 

Feels like that mount point didn't get set up correctly. I wonder if it is sensitive to trailing blanks. I'll try again.

---

### Post by John Coulthard on 2011-03-07
All is well! 

The selection of the mount point is a menu option so there is no chance of getting the syntax wrong. The secret was to format the partition. The initial Grub menu is now much cleaner showing only one Linux partition to choose from (whereas on the previous attempt there were many). **I would judge that formatting the partition is a NECESSARY step in the reinstallation procedure. **

---

### Post by Hakunka-Matata on 2011-03-07
Please mark Thread Solved when finished.

---

### Post by Hakunka-Matata on 2011-03-07
Thanks

---

