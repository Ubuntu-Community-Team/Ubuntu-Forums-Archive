---
title: "Advice on Hard Drive with Bad Sector(s)?"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Sodbuster on 2008-10-09
I was wondering if I could get some advice on how to proceed with my laptop's hard drive.  I have a Fujitsu MHU2100AT (100GB) drive and when I try to install Ubuntu from the Live CD it doesn't give me the option to resize the Windows partition... only to use the entire disk.  I ran the Gparted Live CD and it said the Windows partition had 2 bad sectors in it and that the drive was now considered unreliable.  Apparently I could still do the partition resize but do it all manually and I don't quite have the knowledge to feel confident in that.  It basically involved running ntfsresize and fdisk to get it done manually.  

Can anyone guide me through this?

Also, should I just look into replacing the entire hard drive?

Thanks.

---

### Post by forger on 2008-10-09
Do you still have windows installed?
Boot using windows, do a full scandisk/checkdisk there (not sure, I think it's my computer > right click on drive > properties > Scan disk).
Note: You might have to restart your pc in order to actually do the scan!

And of course, shutdown windows properly (start > Shut down, and not hibernate or standby or I don't know what) :)

---

### Post by Sodbuster on 2008-10-09
Yes, Windows is still installed.  I did the scan disk twice with it rebooting in order to start the operation, as instructed by Gparted.  It still says I have bad sectors and can't resize the partition.

---

### Post by forger on 2008-10-10
well.. if you bought it within the last 3 years you can ask for a replacement :)
[http://www.fujitsu.com/us/services/computing/storage/hdd/discontinued/mhu2100at.html](http://www.fujitsu.com/us/services/computing/storage/hdd/discontinued/mhu2100at.html)

---

### Post by Sodbuster on 2008-10-13
I noticed that... and then I swore when I realized 3 years was a month ago.  So I'm kind of hosed on that :(

I think what I'll do it just forgo putting Linux on my laptop and just wait until I get a new one (not in the forseeable future) or wait until I build a new desktop.  The desktop might come sooner rather than later since I have an older computer collecting dust which was replaced by my laptop, but wasn't bad at all.

---

