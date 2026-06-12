---
title: "Partial software update run leaving machine unable to boot (used boot-repair)"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by abierbaum on 2015-06-10
I am running Ubuntu 14.04.2.  I ran the software-updater today to get the latest updates.  (I held back updating the linux kernel and headers but allowed everything else)

Part way through the update, the system started to hang while running the update process.  (system load went through the roof and all terminal and chrome windows stopped responding).  I think it was running installation scripts for one of the grub-efi packages, but I can not be sure.

In the end the system stopped making progress so I had to hard reset it by holding the power button.

Upon restart grub started to an empty grub terminal with no configuration.  I booted a live CD version of Ubuntu 14.04 from a USB stick and followed the instructions on the Boot-Repair page [1].  The output from my system is here: [2]

The standard boot-repair process did not resolve the issue.  Now I have a configured grub, but when it attempts to start linux it doesn't make it further than trying to load the init fs.  The system shows drive access for a second or so and then stops all progress with no error messages or other signs of progress.

Any recommendations for a next step?



1: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2: [http://paste.ubuntu.com/11692232/](http://paste.ubuntu.com/11692232/)

---

### Post by ian-weisser on 2015-06-10
> **abierbaum said:**
> The standard boot-repair process did not resolve the issue.  Now I have a configured grub, but when it attempts to start linux it doesn't make it further than trying to load the init fs.  The system shows drive access for a second or so and then stops all progress with no error messages or other signs of progress.

That seems like expected behavior if you interrupt an update before the system an initramfs and tells grub where to find it.


> **abierbaum said:**
> Any recommendations for a next step?

Reinstall.

You can use a Live media to locate your old initramfs, and manually adjust GRUB to use it. However, there is no assurance that your system has all the packages you need to actually work, nor that the mismatched versions you have won't crash unexpectedly.

A reinstall will usually be a faster way to get a working system again.

If you wish to determine what went wrong instead of reinstalling, start with /var/log/apt logs of the update.

---

### Post by oldfred on 2015-06-11
Did you try turning off secure boot in UEFI?

Hard shutdown is not recommended, always remember the skinny elephants first. Hard shutdown while system is doing something almost always creates corruption and then a fsck may solve issue. Of course re-install should also work. It takes me 10 minutes to install from my hard drive to my SSD on a pre-partitioned drive.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.

---

