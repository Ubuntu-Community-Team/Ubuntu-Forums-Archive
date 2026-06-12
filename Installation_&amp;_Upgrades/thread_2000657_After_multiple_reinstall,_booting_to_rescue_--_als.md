---
title: "After multiple reinstall, booting to rescue -- also nvidia update kills dual rotate"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by rabarrett on 2012-06-09
Hi,

I'm fairly new to linux.

I installed a dual boot (win xp already there) of ubuntu 12.04 (32bit).  Everything was great, but after I updated all programs, my nvidia driver stopped working correctly.  Specifically, it no longer recognized there was a 2nd monitor, and even after I found the nvidia settings (separate from Setting's "Display" controls), it could use both monitors, but couldn't rotate (a big problem since I use both in portrait mode).

Searching for solutions on that didn't work, but I figured I would just reinstall ubuntu and not run the update.

The reinstall doesn't seem to work.  It just boots to "error:  no such device:  f890010a-1fb.... grub rescue>"

I CAN use the DVD install disc to boot and run things, but I don't know what to do.

In the meantime, I've tried to reinstall about 10 times (using the "replace current ubuntu" as well as "custom" after deleting the old linux partitions and then making a swap partition and ext4 linux partition assigned to / .  That will get it to reinstall, but I still have the "no such device" "grub rescue" problem.

Note:  I'm careful to point the new install (on custom) to the drive where I made the ext4 partition, which is /sdb1 (I've pointed to /sdb and /sdb1 but neither seem to solve the problem.)  (I'm on /sdb1 because I have an old windows drive I'm using for storage on /sda, but not booting to.  My current windows95 installation was booting to the 2nd disk also.

Please let me know if you need anymore information from me.

I appreciate any help.  

Richard

(I'd prefer to keep my win95 installation, but I backed up in case I'm forced to delete it.)

Ultimately I'll need to solve my nvidia dual display, rotation problem after I get going again, so if anyone happens to know how to keep the update from killing my working setup, I'll be much obliged.

---

### Post by drs305 on 2012-06-09
rabarrett,

Welcome to the Ubuntu forums.

If this is an older computer is your new installation deeper into the drive than the one that worked? It's possibly a BIOS limitation that is caused by a 137GB limitation - BIOS/GRUB can't see files deeper into the drive than that.

You can check from the rescue prompt. Assuming you know the Ubuntu partition, try running:
```

ls (hdX,Y)/boot/grub
```
The first drive (X) is 0, the first partition (Y) is 1; i.e. sda5 is (hd0,5).

If it can't see the files and you know they are there, this could be the problem. The solution is to create an installation, or at least the boot partition, within the first 130GB. You can also try to enable LBA or large drives in BIOS, or get a BIOS update.

If this isn't the issue, try installing Boot Repair from the LiveCD and see if it can fix things. If it can't, run the boot info script and post the RESULTS.txt contents or link.

The Boot Repair link is in my signature line.

---

### Post by rabarrett on 2012-06-10
I tried boot repair (found it on another post in the meantime--no luck).  

The computer is 5 years old.  When I opened it, I found I had 3 drives hooked up--2 RAID, 1 IDE.  I took off the two that I thought of as non-primary to trouble shoot.  It turned out that one of them was the windows one I was booting to before installing Ubuntu 12.04.  That made me consider directing the computer to write the boot record there.  So after hooking back up the win95 driver... 

I reinstalled, this time directing it to write the boot info on the non-linux drive.  That worked... mostly.

My boot info is still (somehow) corrupted from when I used boot-repair.  It boots fine, but when it is in the process of booting the ?spashscreen now has garbled graphics instead of a clear picture (green and black lines, also some light and dark blue, above the ubuntu logo--before it gets to the login screen, which is working as it should be).  This surprises me because it was from a fresh install.


It also won't boot into windows95 anymore.  It gives me that option, but when I select it, it says "Windows could not start because the following file is missing or corrupt: <Windows root>\system32\hal.dll.  Please re-install a copy of the above file."  I'm not sure how to do that (or if it will solve the problem).

Thoughts?  (It'd be nice to get my win95 boot back.)

Finally, I'm not willing to let it update any programs because I'm afraid my nvidia driver will go back and not let me rotate the screens.

---

### Post by drs305 on 2012-06-10
> **rabarrett said:**
> 
I reinstalled, this time directing it to write the boot info on the non-linux drive.  That worked... mostly.

My boot info is still (somehow) corrupted from when I used boot-repair.  It boots fine, but when it is in the process of booting the ?spashscreen now has garbled graphics instead of a clear picture (green and black lines, also some light and dark blue, above the ubuntu logo--before it gets to the login screen, which is working as it should be).  This surprises me because it was from a fresh install.


As you surmise, this isn't a boot issue but an OS problem. You might be able to solve the video problem by installing a driver for your video card. At the Grub menu (hold the SHIFT key down if it doesn't appear), press 'e' to edit the menu entry and cursor to the end of the 'linux' line. Backspace to remove everything after "ro" and add "nomodeset". Press F10 or ctrl-x to boot.

If you don't get the unwanted video problems during boot, it's probably a driver (or lack of one) that is causing it. Try adding or changing your video driver card via "Additional Drivers".
> 
It also won't boot into windows95 anymore.  It gives me that option, but when I select it, it says "Windows could not start because the following file is missing or corrupt: <Windows root>\system32\hal.dll.  Please re-install a copy of the above file."  I'm not sure how to do that (or if it will solve the problem).

I don't use Windows but I'd do a search of the exact error message. It sounds like a problem that would be well documented online.
> 
Finally, I'm not willing to let it update any programs because I'm afraid my nvidia driver will go back and not let me rotate the screens.
In cases such as this I usually make a backup image of the partition and then add/remove packages in an attempt to fix it. If the test fails, I restore the image. I use fsarchiver, which is a simple command line backup utility, but there are plenty of apps such as rsync and Clonezilla that are popular on the UF as well.

---

### Post by YannBuntu on 2012-06-11
Hello
> **rabarrett said:**
> My boot info is still (somehow) corrupted from when I used boot-repair.

Please could you indicate the URL(s) that appeared after you used Boot-Repair? if not, please could you run Boot-Repair, click "Advanced options", then click the "Backup partition tables.." button, save the ZIP file somewhere, then send it to me by email (yannubuntu ATT gmail DOTT com) or attach it to your reply in this discussion.

---

### Post by rabarrett on 2012-06-12
I would, but I repartitioned, formatted and reinstalled.  I don't think the info is there anymore.  I also don't seem to have boot-repair in the new install (the command doesn't work and I didn't install it this time).

The screensplash messed up graphic is still present.  I'm not sure how to address that, but everything else is working fine, so I'm afraid to mess with it.

Windows still isn't working, but I haven't tried everything I've looked up yet.

---

### Post by YannBuntu on 2012-06-12
> **rabarrett said:**
> Windows still isn't working

Some Windows boot files may be missing. Please could you:
- indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1")?
- backup your documents
- get a Windows CD (you may need it)

---

