---
title: "Fedora 13 not recognized by Grub2."
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Muffinabus on 2010-09-03
I was installing Fedora 13 on my computer as I need it for a class I'm taking but wanted to keep Ubuntu (10.04) as well.  So now the setup is: Windows 7 on sda, Ubuntu and Fedora on sdb.

I did not install the bootloader when Fedora 13 prompted to.  Running sudo os-prober and sudo update-grub only finds Windows 7.

I know I can manually add it in 40_custom but have no idea how to go ab out that.  The output of my fdisk -l is as follows:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33eb33ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       14594   117115904    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19123   153600000   83  Linux
/dev/sdb2           29650       30402     6037505    5  Extended
/dev/sdb3           19123       19187      512000   83  Linux
/dev/sdb4           19187       29650    84046848   8e  Linux LVM
/dev/sdb5           29650       30402     6037504   82  Linux swap / Solaris

```

I'm pretty sure sdb4 is Fedora, as I cleared about 80 GB for it.  Any help here?

---

### Post by andrewthomas on 2010-09-03
You need to install fedora's grub to its /boot partition in order for grub2's os-prober to pick it up.  Go into Fedora and install grub.

EDIT: it looks to me that /dev/sdb3 is your fedora /boot  and /dev/sdb4 is your fedora /

---

### Post by oldfred on 2010-09-03
These are from older posts as grub2, I thought found it now. Is Fedora installed correctly? 

You will have to update partitions & UUIDs from this example

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by Muffinabus on 2010-09-03
> **andrewthomas said:**
> You need to install fedora's grub to its /boot partition in order for grub2's os-prober to pick it up.  Go into Fedora and install grub.

EDIT: it looks to me that /dev/sdb3 is your fedora /boot  and /dev/sdb4 is your fedora /

I deleted the partitions and reinstalled Fedora in the same spot with Grub installed on sdb3 and Ubuntu's Grub still cannot find it.

---

### Post by andrewthomas on 2010-09-04
go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow the instructions and post the results in your next post

---

### Post by garvinrick4 on 2010-09-04
> **Muffinabus said:**
> I deleted the partitions and reinstalled Fedora in the same spot with Grub installed on sdb3 and Ubuntu's Grub still cannot find it.
Do not use LVM on install and just choose to not install any grub at all. When through
with install boot into ubuntu or install with grub2 and update-grub. I use this same method with fedora-redhat-opensuse. There is a spot to not choose any grub installation at all at end of installation in fedora13. They all use grub-legacy if they used grub2 then I would just install to sda

---

### Post by andrewthomas on 2010-09-04
> **garvinrick4 said:**
> **Do not use LVM on install** 
Sorry, I forgot this part.

---

### Post by Rubi1200 on 2010-09-04
> **garvinrick4 said:**
> Do not use LVM on install and just choose to not install any grub at all. When through
with install boot into ubuntu or install with grub2 and update-grub. I use this same method with fedora-redhat-opensuse. There is a spot to not choose any grub installation at all at end of installation in fedora13. They all use grub-legacy if they used grub2 then I would just install to sda
Absolutely!! I have also done it this way with zero issues. If there are problems, reinstalling GRUB2 to sda quickly sorts it out.

---

### Post by Muffinabus on 2010-09-05
Thanks for the help everyone, reinstalling Fedora and manually managing the partitions without LVM works flawlessly and now Grub recognizes that Fedora is installed.  Never even knew about LVM until you guys brought it up.

---

