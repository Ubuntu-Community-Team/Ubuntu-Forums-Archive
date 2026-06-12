---
title: "Install Error"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by NewsMan2010 on 2011-10-05
I keep getting this error when trying to install on a WinXP PC. This is odd as I have Ubuntu 11.04 running on two other old Sony Desktop PC's and obviously - they installed fine. 
 
:confused:

---

### Post by lcman on 2011-10-06
What's in your "computer" directory?

---

### Post by NewsMan2010 on 2011-10-06
Oddly, I did a search and found it was just a silly glitch. You have to eject all usb drives, etc., to get it to install. Really weird. 
 
Now, because my 2nd hard drive is a 60gb and it for some reason only shows up as a 31gb, the Ubuntu install won't complete because it says it has a partition.
 
I tried to use windows to fix it, but even in windows it only shows up as a 31gb, so I'm wondering now if it has the jumper pins (I read they could be causing this) are in the wrong positions making windows see it has 31gb.
 
:confused:

---

### Post by Hakunka-Matata on 2011-10-06
what kind of HDDs are you using?  A mixture of PATA & SATA?

---

### Post by NewsMan2010 on 2011-10-06
It's an older Sony Desktop from like 2005, one of the Sony entry level desktops. It had a standard 60gb 5,400 rpm HDD that I think was a Samsung.
 
After I installed a new WD Caviar Black 7.200rpm, I reformatted the 60gb HDD and made it a secondary drive. I can't recall if I changed the pin jumper things (might have so it wouldn't be a master boot drive anymore - and could have set the jumpers up wrong), but I do know it never again showed up as a 60gb drive.
 
So for that reason it seems Ubuntu Windows installer sees it as a partitioned drive and won't install until I get rid of the partition. 
 
That PC is at my parents house and I am at my apartment an hour away and fixing to head to class, so it will be Friday before I can get back up there to work on it again. 
 
Thanks for helping a n00b out, all! :D

---

### Post by Hakunka-Matata on 2011-10-06
If you have one IDE/PATA drive, and the other is a SATA, jumper the IDE Drive to be Master to be safe.  
Given your location you might want to consider bringing the hard drive(s) home to your place, you could install Ubuntu there @ your apartment.  Take the drive back to your parent's and plug it in.  Can't hurt anything.

---

### Post by NewsMan2010 on 2011-10-08
OK, got it working.

I'm posting from the newly installed Ubuntu 11.04 Sony now. :w00t:

I had to swap the drives around because the cable setup was wrong.
 
The MBD was on the slave connection of the the SATA and the slave was on the MBD cable. 

I also removed the jumper from the old hard drive and it shows up as an 80gb Sumsung drive now - after deleting the partition. 

So now, Windows XP is on the 7,200rpm WD blue drive and Ubuntu 11.04 is on the second drive (the original 2005 drive that came in this Sony)the Sumsung 80gb 5,400rpm.

The Sony model is PCV-RS300C that I ordered from Sony.com for my sister when she was in college. Of course it has been moved to my parents house and they just mainly use it for web browsing, so I figured Ubuntu would be much faster and better for that. :D

It rocks! Love it and I'm sure they will once they "feel" the difference! 

Thanks for the help, all!

---

### Post by mörgæs on 2011-10-08
Good, then please mark the thread 'solved' using 'thread tools'.

---

