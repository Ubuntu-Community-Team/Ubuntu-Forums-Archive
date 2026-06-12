---
title: "Windows XP over writes Windows 7 Grub 2 Boot entry after sudo update-grub."
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by Pulse7 on 2011-06-22
**This is my problem.**  GRUB 2 replaced the boot entry for Windows 7 when I installed Windows XP.  I tried to create my own menu entry for Windows XP
but it seamed to me that it was superseded by the Windows 7 boot loader.

**Hi everyone,**

I have a brand new desktop PC - Core i7 processor, 2 TB hard drive, 6 GB RAM.

My problem:  I don't know how to bring back a menu entry that was over written / Superseded by another OS being detected by update-grub; in this case Windows 7.  I installed Ubuntu 11.04 at the end of many other Linux OS's.  So it is a Multi-boot setup.  

Basically Windows XP has replaced the Windows 7 boot entry in the GRUB 2 Boot menu after running update-grub. 

Then to get Windows 7 back I booted off the Windows 7 Install DVD and used the boot repair option. 

This then changed the working Windows XP Boot Loader to boot Windows 7 which I wanted but there was a catch.
-->   Windows XP didn't boot any more because it was replaced / Superseded.


The Linux OS's boot fine.

---

### Post by oldfred on 2011-06-22
Do you have both windows in primary partitions?

The issue is windows not grub. Windows can only boot from a primary partition with the boot flag. So if you add additional windows it literally moves the boot & boot files of the second install to the first one with the boot flag. Grub then only sees one windows install as the second has no boot files to boot.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words (Vista & 7 are essentially the same):
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You can post this to review your current installs:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Pulse7 on 2011-07-04
**Hi**

I've reinstalled XP onto a primary partition next too my Windows 7 partition.  

I then typed in,  sudo fdisk -l 
which gave me my partitions and usb devices.  Then tried,  sudo blkid
for check. Then I mounted the Ubuntu partition by,  sudo mount /dev/sda11 /mnt.
And then finally I typed,  sudo grub-install --root-directory=/mnt /dev/sda.

Rebooted and then typed in,  sudo update-grub 
for a refresh of the menu.

Anyone know of the steps too get Windows 7 and Windows XP too run side by side with 8 other Linux Distributions.

These other distros are bootable under GRUB 2 but after,  sudo update-grub
there was only 1 Windows entry that of the new install of XP.

Any one with an idea on this would be great.

---

### Post by oldfred on 2011-07-04
Did you read post #2. It explains how windows only boots from one partition. I also posted instructions on how to install to get two separate boots.

---

