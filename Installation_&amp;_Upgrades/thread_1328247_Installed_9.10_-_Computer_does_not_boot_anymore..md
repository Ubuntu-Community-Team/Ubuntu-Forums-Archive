---
title: "Installed 9.10 - Computer does not boot anymore."
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by GodShapedHole on 2009-11-16
I just made the switch from Windows and after installing Ubuntu (on the former Windows partition formatted to exp4 by the installer CD), I can't BIOS boot anymore. I have no clue what happened there - I was not aware that the installer mucked around with my BIOS flash. Does it?

I have never had boot issues on this machine before, and now when trying to boot up my computer, the BIOS gives its usual beep on startup, and proceeds to hang on the splash screen that prompts you to press DEL for setup. I wish I _could_ get to setup.

Even though I know it's not exactly recommended, I did this install without using the live disk first. I figured that if something would crop up, I could always just go back and reinstall Windows. I tried Ubuntu a few years ago (6.10 or 7.4 I believe) but couldn't use it (interestingly) because of hardware incompatibility - my wifi card was not supported. I have a different wifi card now, and I figured that it would probably work now. I thought since I'm already slightly acquainted with Ubuntu already and did not need to check out the experience I wouldn't need to - but now I'm afraid that since I didn't check for hardware compatibility first I might have screwed something up. 

But it's not Ubuntu that fails to boot, it's my BIOS! How did that happen, and what can I do? Do I have to to have a computer store reflash it?

<edit> Holy crap. Just as my posted message appears, the computer ended its hang and booted - into the CD. I told it to reboot hoping it would work again, but nope, hanging on POST again. I took out the CD and hope waiting for another half hour will make it come out of the hang again. If it did it once... Any suggestions?

---

### Post by darkod on 2009-11-16
I have never heard of any Linux or even Windows OS to tamper with your BIOS. Definitely not flashing it.

Depending on the MB there is backup BIOS, are there any options to enter that? Also, you might consider clearing the CMOS (BIOS), but sometimes it could possibly make things worse, depending what the problem is now.
Anyway, clearing it means unplugging you power cord from the PC, usually taking the backup battery on the MB out, and sometimes using jumper to clear the cmos. Your MB manual will give you details. If you don't have it go to the manufacturers website they would have it there.

PS. The single beep is actually signal for successful POST (Power On Self Test). It is very strange to get the single beep and the pc not to continue booting normally. It might be a long shot, but can you try with another keyboard. Keyboard errors can stop the boot process but it usually says on screen, and it would be coincidence to get a fault in the keyboard just when you were installing ubuntu. But strange things are happening.

---

### Post by TheHimself on 2009-11-16
Can you boot the computer using the live CD?

---

### Post by GodShapedHole on 2009-11-16
The long shot with the keyboard worked - with a twist. I removed all USB devices and lo, BIOS boots again! Ubuntu doesn't boot, seems the install is botched. Let the install application check itself and the RAM, everything is OK. Will attempt to format partittion again and reinstall Ubuntu - should I make it /boot? I wasn't sure so I thought leaving it alone would probably be best. Was I wrong?

---

### Post by darkod on 2009-11-16
Personally I have:
/
swap
/home

In case you want to install over it you can keep /home without formatting and just mount it. no specific need for separate /boot as partition.

And I always prefer to create them manually, leaves the choice with me, not the automatic installer.

swap of 2GB is sufficient, maybe 4-5GB max if you have lots of ram and you want to use sleep/hibernate. Otherwise 2GB is enough. The other partitions as per your wish and the available space.

---

### Post by audiomick on 2009-11-16
> **GodShapedHole said:**
> The long shot with the keyboard worked - with a twist. I removed all USB devices and lo, BIOS boots again! 

Reminds me of a particular Laptop a couple of years ago that would always hang up if you tried to shut it down with USB anything plugged in. It was a problem with the Model. A company I was working for had them as Sound Technician laptops, and they all did it.

re Partition sizes: I did a 9.10 fresh install for someone recently, and the / had around 2.7 GB in it. My Ubuntu Studio, after distro Upgrades from 8.04 to 8.10 to 9.04 to 9.10, and installing everything that even remotely interests me for the last 2 years, is up to nearly 6 GB. The folder grows withh time if you don't take measures to clean it up, but no where near as much as windows. I know you can clean out, but don't know how. The recent install became necessary because the / on that computer, which was about 5 GB, was 100% full. The reassuring thing was, the computer didn't crash or lock up or any of the other things that another OS might do. The first sign of trouble was that open office stopped being able to load pictures into documents.
To cut a long story short, 8 or 10 GB is probably more than enough for / for the next few years.

---

