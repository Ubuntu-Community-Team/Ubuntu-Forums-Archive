---
title: "Cannot merge partitions"
date: 2020-12-23
forum: Installation &amp; Upgrades
---

### Post by tapasray on 2020-12-23
I am running Ubuntu 20.04 LTS as my primary OS in a dual-boot set-up with OEM Windows 10. I have a Windows partition, an Ubuntu partition and a common NTFS partition, which I use for storing most of my data. As the Ubuntu partition has run out of space, I have freed some space from the common NTFS partition. The "unallocated space" (us) is adjacent to my Ubuntu partition (U) - to the left of it in the graphical representation. But I can't merge the two either with Disks or gParted. I have tried formatting the us to ext4 as the Ubuntu partition is ext4, but that hasn't helped. I would really appreciate some help with this.

---

### Post by CatKiller on 2020-12-23
You don't merge partitions, you extend a partition into unallocated space.

You also can't fiddle with a partition while it's mounted, which means you need to boot from a live USB if you're trying to fiddle with your / partition.

---

### Post by tapasray on 2020-12-23
> **CatKiller said:**
> You don't merge partitions, you extend a partition into unallocated space.

You also can't fiddle with a partition while it's mounted, which means you need to boot from a live USB if you're trying to fiddle with your / partition.

Thanks, @CatKiller. I tried extending, too, but that didn't work either, clearly because the Ubuntu partition was mounted. Doing it from Windows should work. If not, will try with gParted on a pen drive.

---

### Post by CelticWarrior on 2020-12-23
No, doing it from Windows doesn't work.

You need to boot a live session and use Gparted in it, first moving the partition to the "left", then extending.

Make sure you have backups.

---

### Post by Impavidus on 2020-12-25
Doing it from Windows won't work, as Windows doesn't understand ext4 partitions. It only understands some native Windows stuff. But every Linux live disk, like the one you used to install Ubuntu, has a partitioning tool included.

Make sure you've got backups. People make errors and power failures happen.

---

### Post by TheFu on 2020-12-25
> Make sure you've got backups
This cannot be stressed enough.  Backup anything on any storage connected to the system. Not just the stuff for ubuntu.

Also, there are some setups with non-GPT disks which might not allow extending an existing partition.

---

### Post by tapasray on 2020-12-25
Thanks,

---

### Post by tapasray on 2020-12-26
Thanks, @CelticWarrior, @Impavidus and @TheFu. Yes, I backed up everything before trying to do these things, and indeed, I could not do the resize operation (adding unused space to main Ubuntu partition) from Windows. Managed to create a gParted Live USB stick, but that is as far as I got. I am unable to include this (gParted) in my boot options and don't see any way of doing that in Grub. That's where things are now.

---

### Post by CatKiller on 2020-12-26
It doesn't have to be a specific gparted image - the installer that you used when you installed Ubuntu has all the tools you need. In either case, though, you turn the image file into a bootable system with a particular tool - I like Etcher, but there are quite a few to choose from. Some UEFIs are set up to always boot from a bootable USB/DVD filesystem if it's present, and some you'll need to press a key to invoke a specific one-off boot choice.

---

### Post by tapasray on 2020-12-26
> **CatKiller said:**
> It doesn't have to be a specific gparted image - the installer that you used when you installed Ubuntu has all the tools you need. In either case, though, you turn the image file into a bootable system with a particular tool - I like Etcher, but there are quite a few to choose from. Some UEFIs are set up to always boot from a bootable USB/DVD filesystem if it's present, and some you'll need to press a key to invoke a specific one-off boot choice.

Ok, let me try with the Ubuntu installer.

---

### Post by TheFu on 2020-12-26
after boot, choose "try ubuntu", then pick **gparted** from the menu somewhere.

---

### Post by tapasray on 2021-01-05
I was able to resize after unmounting the partition.

---

### Post by tapasray on 2021-01-05
I was able to resize the partition to include the unused space after unmounting the partition. Was unable to do it earlier bercause I had forgotten to unmount. 

Thanks.

---

