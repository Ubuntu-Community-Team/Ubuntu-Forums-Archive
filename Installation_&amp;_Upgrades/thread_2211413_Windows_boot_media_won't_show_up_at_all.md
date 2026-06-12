---
title: "Windows boot media won't show up at all"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by Stephanie_Litchfie on 2014-03-15
So I gave Ubuntu a try, and as much as I love it, I'm a gamer and half my games don't work. Back to Windows I go!

Except, it won't let me install it. I've tried using a dvd and a usb stick, and neither of them will show up in the boot menu at all in the BIOS. I tried connecting my other hard drive, and that won't show up either (running Windows 7) even if I have the Ubuntu hard drive disconnected. I've tried restoring the setting to default, and that didn't do anything.
Any ideas?

---

### Post by efflandt on 2014-03-17
With some computers (especially Dell) even if you set CD/DVD or USB to boot before hard drive in drive order, it may still default to booting from hard drive unless you are currently booting the alternate device that you last booted from. So in the BIOS splash screen you may still need to press whatever hotkey (possibly F12 or Esc) that your computer uses for you to manually select the boot device. Having installed Linux should not affect that because the BIOS splash screen comes up before any operating system boot is initiated.

That is probably a safety feature, so you do not accidentally boot a potentially malicious removable device. The only virus I ever caught many years ago was from accidentally booting an infected floppy disk (Stoned Empire Monk alias Monkey virus).

---

### Post by oldfred on 2014-03-17
Also Windows installer will only install to a primary NTFS formatted partition with the boot flag.
Or if you have unallocated space and available primary partitions.
But if available primary partition is after your extended partition, Windows may just delete your Linux partition as it does not see it and just rewrites partition table without it. Best to have good backups and backup partition table separately.

       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

