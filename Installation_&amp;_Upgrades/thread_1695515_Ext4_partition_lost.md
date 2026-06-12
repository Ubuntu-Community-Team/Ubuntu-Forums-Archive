---
title: "Ext4 partition lost"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by fl0at on 2011-02-26
I'll keep it brief since I'm having to post from an iPod.  I started a windows recovery DVD to access bootsect  and after the factory DVD loaded, I realized it was only a restore disk, so I exited.

After reboot I got hit with grub rescue> so I booted a Live CD to reinstall grub, but couldn't mount my Linux partition.  So I launched gparted and low and behold, my Ext4 drive was listed as "unallocated."

So, I booted a partition recovery live cd (partition wizard home edition) and ran a search on the drive and found my partition and restored it.  Feeling pretty good I applied the changes and rebooted straight into grub rescue>.

Unphased, I booted back into live, only to stall on the mount.  So I booted gparted and noticed the exclamation point next to the partitin.  And it was at this point I realized I restored the partition as Ext3, as, apparently, PWHE didn't support Ext4 and thought it was just Ext3.

So I booted UBCD to see if Parted Magic would be of any use, only to find that it won't boot.

And now I have no idea what to do to restore the partition to Ext4, any ideas?

---

### Post by 7xs on 2011-03-04
Try testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk). Avoid writing files to the lost partition before trying to recover.

---

