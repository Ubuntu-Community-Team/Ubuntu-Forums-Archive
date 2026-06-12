---
title: "Dell XPS 410"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by merlinus on 2014-08-07
A friend is trying to get 14.04 to run on this computer.  The live DVD does not work, but he installed it anyway, and it seemed successful.  gparted shows the correct partitions and filesystem.  But on boot-up he gets the initramfs prompt.  Typing exit gets him to what appears to be the desktop, but there are no menus nor icons.

Any ideas?

---

### Post by oldfred on 2014-08-07
Did you install with UEFI or BIOS?
That live installer did not work should be a clue. If you can resolve that, then you will know issue.

This says you need some UEFI/BIOS settings.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

      
 Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

Perhaps a driver is missing, but it seems you need to update, similar to this that was a keyboard issue.

 update-initramfs with keyboard drivers.
[http://ubuntuforums.org/showthread.php?t=2201983](http://ubuntuforums.org/showthread.php?t=2201983)
A simple fix is the following: you should add your keyboard driver name  to the /etc/initramfs-tools/modules file and update the initrd.img with  update-initramfs -u.

Now older so most issues should have been resolved.
 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by merlinus on 2014-08-08
The try feature did not work (never even booted to a desktop), but the install did.  Sorry if I was not clear.  Also since it only boots to an initramfs prompt, can drivers be updated?

---

### Post by oldfred on 2014-08-08
I think to do that you have to chroot into your install from your working live installer. But if live installer does not work.....

Often to get live installer to work, it may need boot options. 
I have nVidia and have to have nomodeset, which I think works for AMD. Intel chips often need other settings also. The community Dell link discusses some UEFI/BIOS settings that also may be required.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1 - video options are mostly for Intel
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Some systems require both video and other boot options.

---

