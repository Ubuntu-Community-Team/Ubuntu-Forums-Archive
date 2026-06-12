---
title: "installation on external hard drive fail"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by flannery on 2011-01-10
My original intention was to install a distribution of Ubuntu onto an external hard drive so i can use it on different computers.  I first downloaded and burned a copy of Ubuntu 10.10 and booted my Acer laptop to it.  I then plugged in my external hard drive and tried to install ubuntu onto it by partitioning the external hard drive.  After I did that, I booted from the external hard drive on my laptop and it ran the new distribution i created.  However, when I tried to boot it from a different computer it said something like "partition not found."  So the next time I tried to install ubuntu onto the external hard drive with out partitioning it, using the entire drive.  This is what started to cause problems.  

Now when I start up my laptop without the external hard drive plugged in i get "error: no such device: xxxx..... grub rescue>.  When I start it up with the hard drive plugged in a grub comes up with the new installation, my old ubuntu installation, and my old windows vista.

I'm not sure what's going on.  Any help would be helpful.  If you need any more information I've been going in circles on it for a long time so I can probably give you the info.

---

### Post by Hegh on 2011-01-10
The problem is that Grub needs additional files beyond what it places in the MBR on your internal hard drive.

What I've done before is I created a new partition on the internal hard drive mounted as /boot. This setup, although simple, cannot be used to boot Linux from the external hard drive on other machines.

To do that, you'll need to prevent Grub from installing to the MBR of your internal hard drive. Since it already has, here is an outline of what you'll need to do:

 1) Boot into Linux (if you can't, re-install with the partitioned external hard drive). If it gives you the option of where to install Grub, great! Install it to the external hard drive. But I don't think it will.
 2) From Linux, install Grub to the MBR of the external drive. You'll need to look up Grub's documentation for this, it's changed too much since the last time I did it.
 3) Boot into Windows and tell it (likely through the storage configuration) to reinstall the bootloader on the MBR. You may need to do this by running `fdisk /mbr` from a command prompt. Not sure how it works in Windows 7, last time I did it was around Windows 98.

Now, next time you boot up your computer, if you want to boot into Linux, make sure the external drive is plugged in and hit the necessary button (likely Esc) during POST to bring up the BIOS boot menu, and choose the external drive instead of the internal drive.

---

### Post by efflandt on 2011-01-11
You accidentally put grub on the mbr of your internal hard drive.  In the future if you install Ubuntu on an external drive, pay attention to the bottom of the manual partitioning screen to put grub on the external drive in 10.10 or later (or Advanced button in screen after setting username and password in 10.04 or earlier)

Boot into Ubuntu on the external drive.  Run mount command to see which drive the root partition is on, for example if it says something like:

/dev/**[COLOR=Blue]sdb[/COLOR]**1 on / type ext4 (rw,noatime,discard,errors=remount-ro,commit=0)

Then do: **sudo grub-install /dev/[COLOR=Blue]sdb[/COLOR]** (or replace **[COLOR=Blue]sdb[/COLOR]** with your actual external drive)

Reboot to the external drive and then do: **sudo update-grub**

Then you need to restore the MBR of your internal drive to a normal Windows MBR.  How you do that with a Windows system disk in recovery mode depends which Windows version (fixmbr for WinXP or earlier, or bootrec /fixmbr for Vista or Win7).  Or you can do that from Ubuntu [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by Butsy on 2011-01-16
I just installed Ubuntu 10.10 on a external HDD and had the same thing happen. I removed my internal hard drive running Win 7 during the install though. Win 7 booted great until I rebooted to the external Ubuntu drive, then Ubuntu rewrote my MBR. When I tried to boot to the internal HDD I had a choice to repair the os or ? (can't remember the other choice) which led to a system restore which repaired The win 7 MBR. Vista should have system restore on the Vista disk (assuming you have a Vista disk). I'm not using the external drive with Ubuntu again. Good luck!

---

### Post by Hegh on 2011-01-16
That's weird... It should not have written anything to your MBR during bootup. Sorry, I don't know what could have happened.

---

