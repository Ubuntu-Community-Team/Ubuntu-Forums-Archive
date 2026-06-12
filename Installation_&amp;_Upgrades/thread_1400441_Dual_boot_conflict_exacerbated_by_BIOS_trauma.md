---
title: "Dual boot conflict exacerbated by BIOS trauma"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Seadraconian on 2010-02-06
Ok.

CPU: 40 GB hard drive, 356 MB RAM

Running Windows XP service pack 2
Local Disk C:
   Free space: approx 31 GB
   Total size: approx 37 GB

I am using an USB keyboard and mouse.
This is awkward because I cannot select which OS to boot from, etc.
Also, cannot access BIOS to potentially turn on the legacy USB function.

We do not have a ps/2 keyboard, and believe me, I looked.
I acquired a usb to ps/2 adaptor:

[IMG]http://gadgets.softpedia.com/images/news/How-to-Connect-an-USB-Keyboard-or-Mouse-to-a-PS-2-Interface-And-Viceversa-2.jpg[/IMG]


Still no joy. Also, the keyboard doesn't work within the virtual Ubuntu, while it did when connected without the adaptor.

Getting my hands on a ps/2 keyboard is not an option.





To get into Ubuntu, I had to, within Windows, tell the computer that the Live CD was a bootable drive, so that it would be the first option over Windows, and therefore the automatic selection when I didn't (couldn't) make one.

This leads me into the Ubuntu 9.10 install, where I am told Ubuntu is already on the computer (half of the hard drive, with Windows XP on the 2nd half), and I can either install 9.10 beside it, or replace it.

If I choose to replace it, 9.10 takes over the entire 40 GB.

Part of the problem is that the partition that Ubuntu is apparently on is /dev/sda1, and Windows XP is /dev/sda2, but within the Palimpsest Disk Utility:


20 GB File System
NTFS File System
Partition 1 (HPFS/NTFS (0x07))
/dev/sda1


20 GB File Unrecognized
Unrecognized
Partition 2 (Linux (0x83))
/dev/sda2


So I'm worried that if I install 9.10 in /dev/sda1 like it wants me to, I'll be losing XP...

HELP!!

---

### Post by Seadraconian on 2010-02-07
Bump

---

### Post by darkod on 2010-02-07
If you can boot the ubuntu cd somehow, instead of selecting Install Ubuntu, select Try Ubuntu first and let it load the live desktop. Then open Gparted (System-Administration) and look at the partitions on the drive, and which one is ntfs, which one ext3/ext4.
Delete the ubuntu partition and make sure you leave your XP partition alone. You should delete all partition relating to ubuntu. For example, if there is logical partition inside extended, deleted the logical first and then the extended. Click the green button in Gparted to execute your choices. Leave the empty space as unallocated.
Then boot again with the cd, or just click the Install Ubuntu icon on the live desktop, and in step 4 tell it to Use Largest Available Free space. That will set ubuntu into the unallocated space you created.

But if your keyboard doesn't work in the boot menu I don't know how will you select which OS to boot during everyday use.

---

### Post by Sylslay on 2010-02-07
"But if your keyboard doesn't work in the boot menu I don't know how will you select which OS to boot during everyday use."

???Meake a plan witch OS will be use in next boot and change it in grub conifg or with start-up Manager  apps.

---

### Post by Seadraconian on 2010-02-07
@darkod: Followed your instructions and it worked like a charm!

About the keyboard, I will be able to borrow a PS/2 one in a week or two, and accessing XP isn't a priority, I just didn't want to wipe it. The computer I'm doing this to is just a side project thing (an old CPU we had lying around), everything important is on my laptop.

Thank you!

---

