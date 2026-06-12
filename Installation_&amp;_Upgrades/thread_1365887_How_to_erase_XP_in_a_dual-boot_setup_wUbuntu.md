---
title: "How to erase XP in a dual-boot setup w/Ubuntu"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by Old Newville on 2009-12-27
I installed Ubuntu 8.04 LTS on my Dell Dimension box earlier this year in a dual-boot setup with Windows XP, which was already on the drive when I added Ubuntu.  

As I got up to speed, I added VirtualBox with a fresh install of XP. We found that the VB version of XP works so well that we don't use the original XP anymore (no point to rebooting the computer when I can run Ubuntu and XP at the same time). I'd like to get the original XP off my hard drive and make that partition useable to Ubuntu (and VB).

How do I do this without damaging my system? If I simply erase the XP partition, will I still be able to boot up my system, since XP was on the drive first?

---

### Post by audiomick on 2009-12-27
Hi.
As far as I know, but wait and see if someone else has another opinion, you can simply remove the partition that XP is on, and add the space to your Ubuntu install.

Afterwards, you will have to update your grub to remove the reference to the windows install. You should find what you need for that here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

To remove the XP partition, install gparted from the repositories, or burn a gparted live cd from here
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Herman on 2009-12-27
You'll need to make sure you have a good backup of all your files first.

Whenever I'm doing work like that with partitions I usually use GParted and the dd command.

I would use GParted from the Ubuntu Live CD or from Parted Magic Live CD for deleting the Windows XP partition.

If Windows XP was the largest, and taking up more than half of the hard drive it would then be simple to us a dd command to copy Ubuntu to a new partition at the start of the hard disk.
```
dd if=/dev/sda2 of=/dev/sda1 bs=4096 conv=notrunc,noerror
```Where: You want to copy partition 2 to partition 1
Where: Partition /dev/sda1 is the partition you want to copy Ubuntu to, (your old Windows partition), 
and where: Ubuntu is in /dev/sda2. 
CAUTION: BE very careful with the dd command, it is powerful and can do a lot of good if you're careful but it can also do a lot of damage if you're not careful with it.
You can use the copy and paste function in GParted if you want to be more careful.

The next step would be to delete the  old copy of Ubuntu. (Using GParted).

Just to be safe, after the old Ubuntu has been deleted I'd try booting the new copy of Ubuntu before going any further, to make sure it still works.
If it doesn't, it should still be easy to recover the old copy which has been deleted by using TestDisk.
After the new copy of Ubuntu is tested and proves okay, it will be alright to boot a Live CD again and resize the new Ubuntu to fill the entire disk. 
From then on there is a likelyhood that the old installation will begin to be overwritten by new files, so soon your old Ubuntu installation won't be recoverable anymore, not even with TestDisk.

That plan won't work if your Ubuntu partition is larger than your Windows. 
You can copy a partition to an equal or larger partition but not to a smaller partition. 
If that's the case you'll need to shrink your Ubuntu partition first. You may decide to remove some files, that's up to you. It might make things easier.
Or copy it to some other disk such as an empty USB external hard drive, (with dd), and then copy it back again, but to the start of the hard drive.

---

### Post by Old Newville on 2009-12-27
Thanks for the replies.

I have a 160 GB hard drive essentially split into two equal halves  -- one for Ubuntu and one for Windows. So, you're saying I should copy the Ubuntu image to the XP area of the disk, and use the live CD to resize the partition. That doesn't sound too complicated. Do I need to change anything in GRUB?

---

### Post by Herman on 2009-12-28
> Do I need to change anything in GRUB?Yes, now that you mention it, probably you will. 
You said installed Ubuntu 8.04 LTS, so you're still using 'Legacy' GRUB and I don't think Hardy Heron's GRUB had full UUID support in GRUB yet.

It would probably be a good idea to get yourself a Super Grub Disk to reboot with initially after copying the partition until we can get a chance to edit your menu.lst and re-install GRUB.

---

### Post by Herman on 2009-12-28
If you're not in a hurry and you can leave the computer running all night, you can use the 'move' function in GParted to move the entire Ubuntu partition instead. That's simpler, it avoids changing the partition number and then you won't need to edit menu.lst.

Editing menu.lst is easy though, and moving the entire partition is quite a slow process. It's an option some people prefer though. It's up to you which way you'd prefer to do things.

---

