---
title: "GRUB assistance restoring to a second disk"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by thompsw on 2013-07-12
My root disk died and I'm trying to restore to a second disk.  I had a complete dump from a couple of days earlier, so this should be relatively easy ... except for GRUB !

I'm running 12.04.2 at this point.  

1) I plugged in the new external drive, which is SATA.  It shows up as /dev/sda
2) I ran grub-install on sda
3) I mounted the drive, restored the complete image from the dump
4) I edited fstab in the restore, fixing the UUID to the new disk
5) I ran grub-mkdevicemap on root (the internal drive that I'm running from at this point)
6) I ran update-grub 

The menu entries for sda1 are generated, because it sees the other linux kernels out there.  The "set=root" is generated correctly but the "root=UUID" was not.  It originally still had the UUID of the dead disk -- why is that ?  Of course that didn't work so I tried editing the cfg, fixing that UUID to be the correct one, but it still won't boot.  In fact the bios skips right over it even though the disk is marked bootable.

I've been screwing around with this for some time now in various combinations.  If I try booting directly from that drive, it's skipped over, as above.  If I let the internal drive produce its menu list and select sda, it simply hangs.

What am I missing ?  This should be easy, right ?  

}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 532699cc-fc21-4008-a1a6-f20a30bf0a21
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=532699cc-fc21-4008-a1a6-f20a30bf0a21 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-2.6.31-14-generic
}

---

### Post by sudodus on 2013-07-12
I think you should run grub-install now. Try according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If still no go, please describe what kind of backup you have, and how you restored it to the new disk.

---

### Post by thompsw on 2013-07-12
I had actually run grub-install as well on that external disk.  I forgot to mention that.

I'm using dump to create the backup.  I've been using it for quite some time for weekly backups and have done restores of the entire ubuntu environment to additional disks before without any problems.

I did some more troubleshooting, this time using "recovery mode" and it looks like I'm getting a segmentation fault.  I tried taking another dump, this time of the working internal disk, restoring again to that external drive, updating fstab etc. and am still getting the segmentation fault.

Dave.

---

### Post by sudodus on 2013-07-12
I know, you wrote that you had run grub-install, but I think you did it too early. Do it *now*, when you have everything in place, and locate the boot-loader in the the head of the drive, and point to the current location of the /boot directory (if mounted on /mnt, /mnt/boot).

---

### Post by thompsw on 2013-07-12
I found my problem.  It wasn't with GRUB at all -- it was with the restore.  I reran after mke2fs and then restored and was able to boot from it; then did an update-grub from there and all's well.  Some trash left on the disk was creating the segmentation fault.  

Thanks for trying to help -- 

Dave.

---

