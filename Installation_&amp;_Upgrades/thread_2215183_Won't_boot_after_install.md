---
title: "Won't boot after install"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by belfbri on 2014-04-05
Have installed Ubuntu 12.04 on my system using an external DVD drive. After rebooting it was freezing on "Loading Operating System". Tried the steps here [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) and now when it reboots, the message "Loading Operating System" appears and below that it says "Load Error". The pastebin link is [http://paste.ubuntu.com/7207264/](http://paste.ubuntu.com/7207264/)

---

### Post by oldfred on 2014-04-05
You may have to hold shift key down until grub menu appears.

Your Intel video chip may need a boot parameter, often nomodeset is not correct for Intel, but that may work also.

  Older Intel video card:
 i915.modeset=1 or i915.modeset=0 
newer:
  i915.i915_enable_rc6=1

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by belfbri on 2014-04-05
Thanks for the response. Very much appreciated.

I wasn't getting anything by pressing the shift key so looked into it a bit further and found a suggestion of changing the timeout in grub. The only way I could do this was to find some way to boot the box. Before I used the CD to install, I had been trying with a USB stick to install. Everything installed ok but the box wouldn't boot without the install USB stick inserted. That's when I discovered through some other posts that grub was getting installed to the installation media. That's why I tried the CD install this time thinking there was no chance of it writing to the CD and therefore would be forced to install to the hard drive. Alas this didn't work and I was still unable to boot. That's when I tried the steps to repair boot. Now using the original USB stick I can get the box to boot and was able to change the grub options. I changed the timeout and replaced quiet splash with nomodeset as you suggested. Now I can press the shift key and I get "GRUB Loading" but it also says "Read Error" still (I previously wrote Load error but that's because part of the message was off screen and I was assuming it said Load). I also tried adding i915.i915_enable_rc6=1 to GRUB_CMDLINE_LINUX_DEFAULT but it''s not making any difference - it still won't boot and I get the same "Read Error" on screen. So it will boot using the installation USB inserted which is using what I am assuming to be no extra options defined, but I don't want to have to keep the USB stick in there just to be able to boot the machine. It's like it's not reading the boot partition, perhaps?

---

### Post by oldfred on 2014-04-05
If you can boot install, not live installer re-run BootInfo report. Original one only shows sda, your 128GB drive.

Some BIOS do promote a flash drive to sda, which then creates issues. All the auto install options with Ubuntu install grub to sda.
Best if your system does promote flash drive, is to use Something Else and at bottom of partitioning screen where you select partitions, mount points & formats is a combo box. It also defaults to the drive that is sda, but lets you change to another drive. Do not install to partitions as it looks like one time you did install grub to sda1 which is a partition.

---

### Post by belfbri on 2014-04-09
Sorry to have gone quiet for a couple of days. I did actually try "Something Else" and select the correct destination for grub from the drop-down during one of the installs, but that didn't help. But I have finally got it to work. I did another fresh install but first in the BIOS I changed SATA to IDE mode.

Thanks for all your help.

---

