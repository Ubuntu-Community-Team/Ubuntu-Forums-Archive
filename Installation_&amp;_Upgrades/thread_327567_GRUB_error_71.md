---
title: "GRUB error 71"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by herrma29 on 2006-12-29
Yesterday I was attempting to clean out my ubuntu partition using the live cd and reinstall Ubuntu over that. I accidentally clicked on the ntfs partition though (I know I know) and cleared out my windows install.

So today, I popped in my toshiba recovery cd and reinstalled windows. It told me that it was wiping the hard drive clean which I was ok with. I figured I could just reinstall ubuntu alongside a renewed windows without all of the junk it has accumulated over the years. After the recovery disc was done with all it was doing, I took it out and the computer rebooted.

When it rebooted, it went to grub. This surprised me enough, because I was thinking there was going to be nothing on my drive except Windows. Grub spat out an error 71 at me (don't know what the heck that is) and then stopped doing anything. On the next restart, I went into BIOS and switched the cd back to the top position in my bootup order, put the cd in and restarted it a couple of utimes, every time it went to grub instead of going to my ubunt cd. I was hoping I could reconfigure grub from the live cd, but it won't let me do that. Any help would be greatly appreciated as I will be needing my computer sometime or another.

---

### Post by coffeecat on 2006-12-29
Very puzzling, particularly as there is no Grub error 71. They only go up to 34, as you can see in the [Grub manual]("http://www.gnu.org/software/grub/manual/"). I suspect you mean error 17, which is:

> 17 : Cannot mount selected partition

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.which doesn't get us much further.

I wonder if the Toshiba CD sets up one of these weird and wonderful multi-partition installations with hidden recovery partitions, in which case it may only have restored the main C: partition and perhaps a hidden one and left the Ubuntu one intact, but with an amended partition table which is why Grub is getting confused. One thing we can say for certain - the Toshiba CD didn't restore the Windows bootloader to the mbr - grub stage 1 is clearly still there.

In your situation I would have booted up the live Ubuntu CD and used Gparted to examine the partition layout - without clicking on any partitions of course. :wink: But it sounds as though the HD is still getting boot priority after you changed the boot order settings. Are you sure you saved your changed settings before quitting the BIOS?

---

### Post by herrma29 on 2006-12-29
Here is exactly what my screen says when I start up:

> GRUB Loading stage1.5

GRUB Loading, please wait
Error 71

Not 17.

I did get my ubunto live cd booted up just now though, I had moved my cd boot up to the top AND disabled it. D'oh. So we'll see how it goes once everything is loaded up.

---

