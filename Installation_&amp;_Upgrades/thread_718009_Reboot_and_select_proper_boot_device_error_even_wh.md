---
title: "Reboot and select proper boot device error even when boot device is connected"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by Slamuwell Jaxson on 2008-03-07
Hello,

I had Windows XP installed on an internal hard drive in my computer and decided to try Ubuntu out by installing it on my external hard drive. When all seemed well after the install, I rebooted, got to the Grub menu listing 3 Ubuntu options to boot or Windows XP (I don't know why it is showing Windows XP in Grub) and when I select any of the Ubuntu boot options I get the 'file not found' error, and when I select Windows it tells me to remove disks, media etc and press any key to reboot but when I press any key it does not reboot. Also, when I turn off my external hard drive and reboot in an attempt to load Windows, I get the "reboot and select proper boot device' error, even though I had reset my bios to boot from the internal hard drive. Any ideas? Thanks in advance

---

### Post by logos34 on 2008-03-07
You might want to restore the windows bootloader to the MBR of the internal drive, either using the XP install CD (>recovery console>**fixmbr**) or [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

Then [reinstall grub ]("http://ubuntuforums.org/showthread.php?t=224351")to the mbr of the external usb drive.  Change **groot** and **root **lines in /boot/grub/menu.lst to (hd**0**,x).  

Select boot drive via the bios, or a[dd map commands to your windows entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") in grub so you can boot XP on a second disk.

---

### Post by Slamuwell Jaxson on 2008-03-09
Thanks, but I've tried to restore the MBR multiple times with no success :( so I just reformatted and reinstalled Windows XP. I was able to install Linux on it's own dedicated enclosed internal hard drive and get Windows up and running, but when I manually change the BIOS to boot from the Linux drive and select Ubuntu from the Grub menu I get the "Error 15: File not found" error. Is this because Grub is not looking in the right place? Any idea on how to fix this? Much thanks in advance

---

### Post by logos34 on 2008-03-09
Maybe there's a typo in the ubuntu entry.

Boot from the live cd and post the output of
[B]
sudo fdisk -l[/B]

and your **/boot/grub/menu.lst** as well (access root partition from the live cd or from within windows if you have fs-driver)

---

