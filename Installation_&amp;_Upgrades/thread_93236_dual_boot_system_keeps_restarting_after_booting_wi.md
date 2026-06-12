---
title: "dual boot system keeps restarting after booting windows"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by OneSeventeen on 2005-11-21
At work I need to troubleshoot Microsoft products, so I dual boot Windows XP and Ubuntu 5.10.

After resizing the partion, I installed 5.10 on the remaining hard drive space, which all went well, but it did not detect windows XP and didn't add it to the menu.lst.

So I manually added it to menu.lst, and booted into windows, tried to defrag the hard drive, cancelled the defrag because I realized I needed to delete some old linux ISO's before defragging, and once I tried a new defrag it said checkdisk was scheduled to run so I couldn't defrag.  (makes sense, right because you can't defrag before checkdisking, especially when I was never asked if I wanted to checkdisk... otherwise the end user might know what is going on with the OS, and we can't have that)

So as with every issue in windows, I rebooted, but after my Dell Optiplex GX 280 finished with it's boot process (POST) and should have gone to GRUB, it instead rebooted and started the POST all over again.

So now my machine reboots itself, and will probably continue to do so for all of eternity.  I'm just using an old Ubuntu 5.06 live CD I had lying around now, but I'd really like to know if there is a quick fix to get grub to reinstall itself from the live CD, or do something like that to fix the issue without starting from scratch.

---

### Post by yesplease on 2005-11-21
Perhaps you can boot the install CD in rescue mode and fix (reinstall) Grub from there.  [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

---

### Post by OneSeventeen on 2005-11-21
thanks, that worked perfectly :)

---

### Post by OneSeventeen on 2005-11-22
New update:
***Every Time*** I boot into windows, it rewrites the MBR, but not completely, just enough to make me have to use the rescue console to reinstall GRUB.

Any way to keep Windows from doing this, or at least to add GRUB to Windows' bootloader?

Perhaps just adding a script to a bootable USB device that will tell the computer to boot via GRUB, then if it isn't plugged in, just use the Windows MBR?

---

### Post by yesplease on 2005-11-23
This is not normal.  

As a workaround it may help to put Grub on a USB stick or on floppy, you can use the method in the thread I mentioned above. Your floppy is /dev/fd0. 
In the BIOS bootup sequence you can put floppy first. 

This may help if windows does not interfere with the floppy. I boot from floppy and this setup automagically survived a dist-upgrade and kernel-upgrades.

Does Windows inform you that it will overwrite the mbr, or is it that you find the mbr broken after using windows? Either way, that should not happen.

---

### Post by OneSeventeen on 2006-03-28
Okay, I haven't touched this in a while because I've been using my laptop for development (it has Ubuntu 5.10 on it).  I'm now getting tired of bringing my personal laptop to work just to get work done that should be easily done on my primary computer.

I'm going to format the partitions that had linux, and reinstall Ubuntu from scratch.

Is there a way to write GRUB to a USB stick during the install (I don't have a floppy drive)?

The goal being, if the UBS stick is in, it boots to linux, if it isn't, it boots to Windows.

I'm sure I could just install as usual, run Windows' fixmbr command to rewrite the master boot record, then install GRUB to the usb stick, but I'd rather do it all during the Ubuntu install if at all possible, or at least I'd like to know for sure what needs to be done to get it to install properly on the USB stick, as the thread's I've seen for installing it onto USB are a 9 or10 step process that involve doing a lot of extra stuff I've never had to do before.

---

### Post by Divermarv on 2007-09-05
It appears that I am going to have this problem also. I've just installed ubuntu 7.04 to dual boot with windows xp on my work desktop. I booted into ubuntu just fine, and then restarted and booted into windows xp just fine. But this morning, I thought I'd restart and boot into ubuntu for awhile, but my system just keeps rebooting. It appears that it restarts just after GRUB loads.

I did not get any indication that windows changed my MBR. Now as I don't have anything meaningful in ubuntu just yet, I'm reinstalling from the boot cd, but I'd sure like to get this dual boot thing working well. I'm really excited about trying out ubuntu! There may be a convert here!

---

