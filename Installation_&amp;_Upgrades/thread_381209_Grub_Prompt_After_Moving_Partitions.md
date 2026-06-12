---
title: "Grub Prompt After Moving Partitions"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by LesFromIL on 2007-03-10
Installed UB 6.1 a month or so ago. Dual boots with XP using BootMagic boot manager, so grub NOT installed in MBR. Everything works fine. Recently, had to resize and/or move some partitions, which included moving the Ubuntu partitions (/boot, /(root), /home). Now when I select the Ubuntu installation from the BootMagic menu, I simply see the "GRUB>" prompt.

How can I fix this?

---

### Post by Captain_Riker on 2007-03-12
Hello there,

Let's see: You moved your Partitions? All?

So there is a file called menu.lst, located in /boot/grub/. This file tells grub were the Kernel image and the initrd image are.

The critical lines are like this:

[I]title           Ubuntu, kernel 2.6.17-11-generic
!!!!! -->root            (hd0,4) 
!!!!! -->kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda11 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot[/I]

Just look up the Partition identifier (using the program you used to re-partition or simply start the LiveCD of Ubuntu, see below), i.e. hda5 or sda3.

Then use the LiveCD, mount your /boot partition and use vi to edit your menu.lst (vi (/boot/grub/)menu.lst.

The first line *root (hd0,4)* specifies where your bootloader, grub, is located. First HDD !!5th!! partition. **Mind that grub starts counting from 0**, other then the rest which start with 1. Given that your /boot-partition is now hda7, you have to change (in my example) the line to *root (hd0,6).* The next line specifies the kernel image and, this is the important thing, where your **root-partition** is. *root=/dev/hda11* in my example. Change this to the new device. If it is now hda12, simply change that to root=/dev/hda12. [B]Mind to use HERE the correct identifier.
[/B]

After rebooting everything should work fine, besides ubuntu ending up in the maintenance shell. The UUID's of your partitions have changed. That makes some more editing necessary. This time it's the fstab located in /etc.

You might be able to get into your system, ignoring this, by typing startx while in the maintenance shell. But to get it working correctly it is necessary to change the UUID's of the given partitions in your fstab.

If your able to boot again after changing your menu.lst and need further advise on how to edit your fstab, let me know.

Hope this will help you
Captain_Riker

---

### Post by LesFromIL on 2007-03-12
Thanks for the advice. Now for some specifics.

Since the the partitions only MOVED (due to resize of an existing NTFS partition), and all of the partitions are in the SAME order as they were before, the data in the menu.lst file should not need to change.

Here is how the drive was partitioned BEFORE the resize:

sda1     FAT
sda2    NTFS (C-drive)
sda3    ext3 (/boot for Fedora Core 6)
sda4    Extended Partition containing:
     sda5     NTFS (D-drive)
     sda6     NTFS (E-drive)
     sda7     NTFS (F-drive)
     sda8     NTFS (G-drive)
     sda9     FAT32 (H-drive)
     sda10   EXT3 (/(root) for FC6)
     sda11   EXT3 (/home for FC6 & Ubuntu)
     sda12   SWAP (for FC6 & Ubuntu)
     sda13   EXT3 (/boot for Ubuntu)
     sda14   EXT (/(root) for Ubuntu)
     -          - (UNALLOCATED SPACE within Extended Partition)
-    - (UNALLOCATED SPACE outside of Extended Partition)

This was the partitioning scheme in place when Ubuntu was first installed and worked.

Sample line from menu.lst file:
     title     Ubuntu....
     root    (hd0,12)         [corresponds to /dev/sda13 - /boot for Ubuntu]
     kernel  /vmlinuz.... root=/dev/sda14      [/ for Ubuntu]
     initrd   /initrd.img...
     quiet
     savedefault
     boot

Now, here is the layout with new (resized) NTFS D-drive partition:

Since the the partitions only MOVED (due to resize of an existing NTFS partition), and all of the partitions are in the SAME order as they were before, the data in the menu.lst file should not need to change.

Here is how the drive was partitioned BEFORE the resize:

sda1    FAT
sda2    NTFS (C-drive)
sda3    ext3 (/boot for Fedora Core 6)
sda4    Extended Partition containing:
     -          - (UNALLOCATED SPACE within Extended Partition)
     sda5     NTFS (D-drive, now resized from 5GB to 20GB)
     sda6     NTFS (E-drive)
     sda7     NTFS (F-drive)
     sda8     NTFS (G-drive)
     sda9     FAT32 (H-drive)
     sda10   EXT3 (/(root) for FC6)
     sda11   EXT3 (/home for FC6 & Ubuntu)
     sda12   SWAP (for FC6 & Ubuntu, slight resize from 2055.2MB to 2047.3MB)
     sda13   EXT3 (/boot for Ubuntu, slight resize from 1004.5MB to 1004.0MB)
     sda14   EXT (/(root) for Ubuntu)
 
So the /dev/sdaXX values did NOT change and the GRUB partition number did NOT change. So it appears that no editing of the menu.list file in /boot/grub should be necessary.

GRUB is NOT my primary boot loader. I am using BootMagic for that which is what is in my MBR. GRUB is (or was) installed in the boot sectors of (I believe) sda13 (/boot for Ubuntu).

In order do any of this resizing with Partition Magic, I created images of the partitions that PM would not move using Acronis True Image, made all of the necessary changes using PM, and then restored the partitions using Acronis True Image. Perhaps the restore did not restore the boot sectors????

Any additional feedback would be most helpful.

Thanks,
Les

---

