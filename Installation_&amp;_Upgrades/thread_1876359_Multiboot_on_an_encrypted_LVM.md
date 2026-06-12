---
title: "Multiboot on an encrypted LVM"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by vangop on 2011-11-06
Hi!
I want to install multiple distros. Right now I have win and xubuntu, and linux is on luks encrypted LVM (separate boot).
Until now I thought of making a separate boot for each new distro, but now I think about using a [dedicated grub partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm"). 
I also read about grub chain loading but due to lack of knowledge I need some advice. I'm not sure what exactly I need to do to make a dedicated grub partition in a **RIGHT** way when the OS's are installed in the encrypted LVM, involving initrd and chainloading and whatever else.
Thanks!

---

### Post by vangop on 2011-11-07
anyone?

---

### Post by oldfred on 2011-11-07
I do not know about encryption nor LVM.

You link is to grub legacy and Ubuntu changed to grub2 with 10.10. Grub2 does not like to be installed to a PBR- partition boot sector, just the MBR.


[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition)
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

If you try this, you get a message about it being a bad idea.
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

### Post by vangop on 2011-11-07
Thanks for your reply.
I wasn't going to use that howto - just linked it from google - since I thought dedicated grub partition is a kind of well-known trick.
From the grub2 dedicated partition article (herman's page) it seems that grub is installed to MBR, just the files go to the dedicated partition. 
But it doesn't explain how I should partition the disks for those distros I want multiboot into; where the kernels should be installed, how should I update the kernels while keeping this dedicated partition working, and most important how to handle/setup initrd (for encrypted lvm).

---

### Post by oldfred on 2011-11-07
Again, I do not know if LVM changes things, but I have installed grub2 to NTFS, FAT32 & ext3 flash drives and then manually maintained the grub.cfg file. When you have the grub only install, you do not get any of the os-prober auto updates. But grub2 will directly boot many installs, so you do not have to chain load. But if the install uses grub legacy, an advantage of chainloading is that you do not have to update your grub2 grub.cfg file with the new kernel  on a system update.

this is for booting an ISO which I also do, but I also add extra entries to boot several of my installs on my hard drives, just in case.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

If Debian based (not sure about others), there are links in / (root) to the most current kernel.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by vangop on 2011-11-09
Here's my thoughts.
My current layout is win, boot partition, luks crypted lvm.
```
[=====DEVICE=====] [==FILESYS==] [======LABEL======] [====SIZE====] [MAJ] [MIN] 
[sda1            ] [ntfs       ] [win              ] [    71.15 GB] [  8] [  1] 
[sda2            ] [ext4       ] [boot             ] [   191.00 MB] [  8] [  2] 
[sda5            ] [crypto_LUKS] [<unknown>        ] [   394.42 GB] [  8] [  5] 
[dm-0            ] [LVM2_member] [<unknown>        ] [   394.42 GB] [253] [  0] 
[dm-1            ] [ext4       ] [root             ] [    37.25 GB] [253] [  1] 
[dm-2            ] [ext4       ] [<unknown>        ] [     9.31 GB] [253] [  2] 
[dm-3            ] [swap       ] [<unknown>        ] [     9.31 GB] [253] [  3] 
[dm-4            ] [ext4       ] [<unknown>        ] [   338.54 GB] [253] [  4] 

```

Now how I think it works.
...grub loads initramfs which in turn decrypts luks, activates LVM and then starts init in the OS's root.

Now I want to host more OS's under that luks lvm, so the process should be:
1. grub is installed to mbr. It's grub.cfg is manually maintained - I add chainload command to pass loading to the particular OS grub/loader. Everything else is the same - initramfs etc.
2. Distros have their own /boot (not a separate partition anymore, part of /). Kernels installed there, so kernel updates do not break that external grub. Each distro has grub installed into its partition.
How does it look?
Hope I didn't forget anything.

---

### Post by oldfred on 2011-11-09
I know if we run boot script with LVM, you need this:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)

And grub has a lvm.mod which you would need to load. Do not know how grub handles the encryption.

---

