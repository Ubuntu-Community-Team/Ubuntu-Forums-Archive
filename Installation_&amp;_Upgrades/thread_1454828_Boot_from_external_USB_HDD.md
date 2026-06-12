---
title: "Boot from external USB HDD"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by richr on 2010-04-15
After removing the Windows HDD from my laptop I installed Ubuntu to a new HDD that I installed in it - it works fine when used as an internal drive. But now I have put the Ubuntu disk in an external enclosure and replaced the original Windows HDD internally. 

Now, if I change the BIOS boot priority to CD/DVD -> USB HDD -> Internal HDD will it be the case that I can boot Ubuntu when the external HDD is connected and Windows when not?

Also, if I boot to Unbuntu from the external HDD, will the internal Windows drive be left untouched? I'll be in pretty hot water at home if I damage that!

Thanks

Rich

---

### Post by Mark Phelps on 2010-04-15
> **richr said:**
> After removing the Windows HDD from my laptop I installed Ubuntu to a new HDD that I installed in it - it works fine when used as an internal drive. But now I have put the Ubuntu disk in an external enclosure and replaced the original Windows HDD internally. 

Now, if I change the BIOS boot priority to CD/DVD -> USB HDD -> Internal HDD will it be the case that I can boot Ubuntu when the external HDD is connected and Windows when not?
If, as you seem to indicate, you have set up each drive to boot in isolation, then this should work fine.

> Also, if I boot to Unbuntu from the external HDD, will the internal Windows drive be left untouched? I'll be in pretty hot water at home if I damage that!
When you boot Ubuntu, in the Places menu, it will list the MS Windows partitions -- by default.  If you click on any of those icons, Ubuntu will then mount the corresponding partition read/write.  So, as long as you don't touch those icons, and don't mount the partitions, nothing in MS Windows will be touched.

---

### Post by richr on 2010-04-15
Thanks very much for that. I thought that would be the case - I'm just being super cautious. I suppose GRUB is only required if you are going to keep both bootable discs attached and want to be given the choice of which to use at start up?

Rich

---

### Post by oldfred on 2010-04-15
Some have had issues in the past. These are not my comments but one's I copied, but it may be worthwhile to do. It seems that grub often was updating to the internal MBR not the external.  

It is not that difficult to reinstall grub or windows boot loaders if you have the CD handy.

Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by richr on 2010-04-16
That all sounds a little nasty but because I'm not installing GRUB then am I safe to assume that this won't apply in my case?

Rich

---

### Post by richr on 2010-05-17
Have finally got around to giving this a go. It all worked fine as expected. So, after having changed the boot priority (CD->External HDD->Internal HDD), the laptop will boot from the external HDD to Ubuntu if it's connected and to Windows if not.

---

