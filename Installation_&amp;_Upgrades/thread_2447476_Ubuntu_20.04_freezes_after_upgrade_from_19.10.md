---
title: "Ubuntu 20.04 freezes after upgrade from 19.10"
date: 2020-07-19
forum: Installation &amp; Upgrades
---

### Post by eddugo on 2020-07-19
Updated HP laptop to 20.04 from 19.10. 19.10 had no issues.  When it comes out of suspend by opening the lid or pressing a key, nothing works except the mouse and the clock after the log in screen.

Thank you in advance for your help

Ed

---

### Post by eddugo on 2020-07-20
Update:  Tried the laptop again last night and everything worked until a reboot.  Now nothing works again including Windows - loads but nothing will work on the screen.

Got live distro to work. Tried Boot repair.

[https://paste.ubuntu.com/p/FgHCh62ndr/](https://paste.ubuntu.com/p/FgHCh62ndr/)

Still doesn't work

---

### Post by eddugo on 2020-07-25
Update:  

If anyone has the same problem.  After reloading all the software, I stored a folder with 6.3 Gig - 3600 files on the desk top and 20.04 froze again.  The same file was stored on the desktop before I upgraded from 19.10 with no problem.  i am guessing that could be the problem as i was able to get it to work, removed the folder and it works fine now.

---

### Post by zebra2 on 2020-07-26
If you are dual booting Win10, it may not hurt to turn off fast boot in Windows (power settings).  In addition I put /home on a separate partition on the linux side. In addition and this is just my own way of doing things, but I don't care for upgrades. I always go for a clean install for a version change. An upgrade will inherit all of the accumulated problems from the previous version (possibly). In this regard it doesn't hurt to save off your .config files for browser, email, and etc software.

I suppose you know that Ubuntu switched to a swap file in 20.10. It will still use a partition if available.  If you have two os's sleeping it should be a swap file that is used and not a partition. 

If you have fast boot enabled in windows your system may be "unclean" for a linux boot.

---

### Post by eddugo on 2020-07-26
It was dual boot with windows 10.  I wanted to eliminate that as a possible problem so I just installed 20.04 on the entire disk.  I restored the laptop little at a time to see what may have caused the problem and it was fine until the large file on the desktop.  Your text says Ubuntu went to a swap file in 20.10 - 20.04 too?  I probably did not have one as this laptop was dual booted with 19.10.  I'm guessing no swap file could stop it from coming out of suspend.

---

### Post by zebra2 on 2020-07-26
The swap file started with 20.04. It creates itself and is dynamic.  They switched to a swap file because  #1 the swap partition wasn't getting encrypted with full disk encryption. And #2, problems sleeping If the swap partition wasn't large enough to handle all of the ram. #3, grub problems with dual boot.  You don't say if your /home is on a separate partition but I suggest that you do that if you intend to use linux. Your partition should be...

/root (20 gig)
/home rest of (drive)

or if you want to play with kernels it might be. 


/boot (1 or more gig.)
/root (20 gig)
/home (rest of drive)

This scheme makes it easier to reinstall because you will only need to reformat /root and leave /home intact. I have been using the same /home for years and have copied it from one computer to another many times.

you may get differing opinions on this site about the actual partition sizes. If you copy your large file to the home directory you should have no problems sleeping the desktop with this partition scheme.

---

### Post by eddugo on 2020-07-26
I didn't do a custom install - just let the install program make the changes.  it has 2 partitions 1 = 537 MB and 2 is the rest.  I added more software to it today and I had a problem with it coming out of hybernation.  Can't change that in program settings any more ( been using Ubuntu since 7.04)

---

### Post by zebra2 on 2020-07-26
There are a lot of members on this forum that know considerably more than I do. Perhaps one of them have a solution for your problem.  It has never occurred to me for even an instant to use the auto installer. That is an easy solution for beginners. I personally consider it to be risky.

---

### Post by eddugo on 2020-07-27
Thank you for your input.

---

