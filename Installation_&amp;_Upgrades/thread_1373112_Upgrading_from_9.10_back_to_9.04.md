---
title: "Upgrading from 9.10 back to 9.04"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by UsedBits on 2010-01-05
Ubuntu 9.10 has too many problems for me to continue using it.  The X server freezes (almost entirely when using FireFox), it locks up, and it doesn't recognize my parallel printer hidden behind a parallel-to-usb converter.
 
How does one revert (I consider it an upgrade) back to 9.04?  I'd like not to lose work I was able to get done between system resets (like email, Quicken, etc.).

---

### Post by raymondh on 2010-01-05
> **UsedBits said:**
> Ubuntu 9.10 has too many problems for me to continue using it.  The X server freezes (almost entirely when using FireFox), it locks up, and it doesn't recognize my parallel printer hidden behind a parallel-to-usb converter.
 
How does one revert (I consider it an upgrade) back to 9.04?  I'd like not to lose work I was able to get done between system resets (like email, Quicken, etc.).

Am sorry, you are facing a fresh/clean re-install as there is no downgrade path from Karmic to Jaunty.

If you have a separate /home (which contains YOUR files), you can just re-install Jaunty root over the existing Karmic Root ... and then mount your  Karmic /home to Jaunty.  

*This will require selecting 'manual' in step 4 of the process.  You then identify which is the existing root (/) partition and proceed to format (ext3 or ext4) and select the mountpoint / from the drop-down menu.  The next step is to identify the existing /home and just select the mountpoint (/home) but **DO NOT FORMAT** as it will erase all data.  Once those two have been selected, you can proceed with the install.  When you get to step 6 (I think), **make sure you use the same username and password you have now.** * 

If you don't have a separate /home, now will be a good time to create one (when you re-install Jaunty).

As always, have a working/tested back-up of your files.  There are no guarantees when doing partitioning work on your HD.

Regards,

Raymond

---

### Post by UsedBits on 2010-01-05
Thanks, RaymondH, for your reply.  It has been about 10 years since I last played with my systems to the degree you describe (SunSPARC IPX with Linux).  I'm too afraid to try something like that with real data (wife 3.3 would kill me if I lost all the email and Quicken data).

I've uninstalled compiz to see if FireFox plays better with 9.10.  But if the freezes, hangs, and crashes continue, I'll be forced to call the new kid at work who helped me stripe my disks and get GRUB installed on the RAID 0 array.  (motherboard stripe, not an OS stripe)

---

### Post by raymondh on 2010-01-05
> **UsedBits said:**
> (wife 3.3 would kill me if I lost all the email and Quicken data).


LOL.  I lost 7 years worth of quicken data once.  I survived the onslaught from the wife thanks to a back-up plan then :)

Good luck ... happy ubuntu-ing.

Raymond

---

### Post by UsedBits on 2010-01-06
Totally removed compiz.  Having never run without a window manager, I was surprised at how windows behaved without it.  However, after running FireFox for longer than ever before, it finally crashed (the kind where the mouse freezes, too).
 
I've reinstalled compiz just to get a window manager.  I remember other window managers from when I was playing around with my SunSPARC IPX with Linux, but can't remember their names now.
 
At any rate, until I back up my data, I'm doomed to have to continue with 9.10.

---

### Post by presence1960 on 2010-01-06
> **UsedBits said:**
> Totally removed compiz.  Having never run without a window manager, I was surprised at how windows behaved without it.  However, after running FireFox for longer than ever before, it finally crashed (the kind where the mouse freezes, too).
 
I've reinstalled compiz just to get a window manager.  I remember other window managers from when I was playing around with my SunSPARC IPX with Linux, but can't remember their names now.
 
At any rate, until I back up my data, I'm doomed to have to continue with 9.10.

Don't hesitate in backing up your data, which is something you should do on a regular basis anyway. Every hard disk is one day closer to it's demise and if you have no backup regimen in place when it does die you will be in trouble. At least if you have a working backup on a separate disk if one disk goes you still have your data. The odds of both dying simultaneously are rare. Personally I go one step further. I have an internal disk and an external for backups. So my data is replicated on 3 disks: my data partition which itself is a 250 GB SATA disk, my internal back up disk & my external back up disk. While nothing is foolproof I am very confident about the security of my data.

You can use rsync for command line backups or grsync which is a GUI for rsync if you want a graphical backup.

---

### Post by thodges999 on 2010-01-07
> **UsedBits said:**
> Totally removed compiz.  Having never run without a window manager, I was surprised at how windows behaved without it.  However, after running FireFox for longer than ever before, it finally crashed (the kind where the mouse freezes, too).
 
I've reinstalled compiz just to get a window manager.  I remember other window managers from when I was playing around with my SunSPARC IPX with Linux, but can't remember their names now.
 
At any rate, until I back up my data, I'm doomed to have to continue with 9.10.

Hi again, What is your video card and which driver are you using?

---

