---
title: "Migrating Ubuntu to a new hard drive"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by SEMW on 2006-08-12
Hi everyone!

OK, here's the situation.  I have three hard drives; a 40 GB one with Windows XP, a 7.8 GB one with Ubuntu, and a 120 GB one.  The 120GB one has a 100GB partition for documents, media etc. and a 20GB partition which currently has SuSE 10.1.

I would like to transfer Ubuntu wholesale from the 7.8 GB drive to the 20 GB partition currently occupied by SuSE; preferably keeping everything everything exactly as it is.

With the right partitioning tools I could probably be able to prepare the 20 GB partition (format, divide into main and swap, etc.), but what about then?  Is there a tool that will just clone the Ubuntu partition and drop it in the 20GB one?  Or would just going into Windows and copying and pasting the entire contents of the drive work? (I can read & write to ext2 & 3 from within Windows).  Would Ubuntu automatically recognise what's happened when I boot, or are there config files I'll need to edit (from within Windows, maybe)?

One additional problem is that when I installed SuSE, it's GRUB took over from Ubuntu's GRUB.  If I get rid of the SuSE installation, will the Ubuntu GRUB automatically reinstate itself?  If not, how do I reinstate it?

Many thanks, everyone;

 - Simon

---

### Post by aysiu on 2006-08-12
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) might help you, but you'll have to adjust your /etc/fstab and /boot/grub/menu.lst. You may have to reinstall Grub, too.

---

### Post by SEMW on 2006-08-12
Damn, I knew it was too good to be true.

Firstly, aysiu, thanks for the link; excellent program.

OK.  First I deleted the SuSE partition, then booted from the Ubuntu Live CD (which took 3/4 of an hour, it doesn't seem to like my hardware) and restored GRUB to the 7.8GB hard drive.  Then I divided up the new 20 GB partition into two 10 GB ones, and used partimage to image the 7.8 GB hard drive onto one of the 10GB partitions, then restored that image to the other partition.  Then I deleted the temporary partition which had the image, and expanded the partition which now had a clone of Ubuntu on it to take up the whole space (minus a 1GB swap partition).

So far so good.  Everything seemed in order.

I booted back into Windows, and made the necessary changes to fstab on the new partition, which seemed fairly strightforward.  I wasn't sure which GRUB, the new or the old, would take priority; so I took no chances and edited both of them, replacing all instances of (hd2,0) with (hd1,0) (the old drive was hdc, the new one is hdb), with the intention that that would then, even if it reads the GRUB files from the old partition, boot from the new partition, where I would be able to use "root (hd1,0)" in the GRUB prompt.

It didn't, it booted from the old partition.  No matter.  I went through the process of getting GRUB to boot from the new partition; specifically:
```
sudo grub
root (hd0,1)
setup (hd0)
```
So I rebooted; it read GRUB from the new Linux partition fine, I selected Ubuntu, it started booting, and...

```
Mounting root file system...
Waiting for root file system...
```

Jammed, at the point above.





So near, and yet, so far...





My current fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  ntfs    umask=0222    0    0
/dev/hdb6       /media/documents  ntfs    umask=0222    0    0

```
Which I'm reasonably sure is now right.  My new Ubuntu partition is the primary partition on hard drive B, with the swap file being the first extended partition.

The only thing I can think of is that there may be other configuration files that I need to edit?

Any ideas?

Many thanks,

 - Simon

---

### Post by SEMW on 2006-08-12
Anyone?

---

### Post by SEMW on 2006-08-13
OK, I fixed it -- the problem was the GRUB menu.lst (which is slightly counter-intuitive, since I thought GRUB was just a boot menu, and the problem came after Ubunutu had already stated loading).  I'd changed the "kopt=" line to hdb1.  I'd changed the "groot=" line to (hd0,1).  I'd changed the "root" line for all the boot options to (hd0,1).  What I haden't done was change the "kernal" line on all the boot options to hdb1.  Changing that let it boot.

It's rather annoying how menu.lst seem to mix and match the two notations.  Kopt uses one, groot uses the other, and the menu items use both in different lines.  Why not decide on one notation and stick with it?

Oh well.  Thanks, all.

 - Simon

---

