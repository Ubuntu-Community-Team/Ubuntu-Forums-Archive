---
title: "Installed Hardy Heron. Now can't boot Windows XP Pro. XP does not show in GRUB either"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by drNoor on 2008-06-29
URGENT HELP NEEDED. And I'm totally new to this.

Installed Hardy Heron onto my HP laptop. My HDD configs were:

80GB HDD in 2 partitions.
Partition 1 - C: main system
Partition 2 - D: data

Both looks ok and was able to mount when I run from Live CD.

After installation, both disappeared. Replaced by one HDD called 'filesystem'. Can't find the partitions using Places>Computer> or Places>Computer>Filesystem either. Seems to have disappeared.

And I cannot restart using Windows XP pro even. Tried 'ESC' during startup to go to GRUB. Option to start via Windows is not available too. The only three options available were to start UBUNTU normally, in recovery mode or in memtest mode.

Have I formatted by mistake? Hope I didn't. 

How do i get back to booting with XP?

Apologies if this is a duplicate but have scanned through all threads and most lost me at half-way mark. 

Tried to reboot using Windows CD. Can't do that either. GRUB always starts and bypasses the CD load. How do I do that?

Need help urgently. Thanks.

---

### Post by ibutho on 2008-06-29
To see the partitions on your disk, run Applications -> Accessories -> Terminal and enter the command below
```
sudo fdisk -l
```
Please post back the output.

---

### Post by drNoor on 2008-06-29
> **ibutho said:**
>  Please post back the output.
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9354    75135973+  83  Linux
/dev/sda2            9355        9729     3012187+   5  Extended
/dev/sda5            9355        9729     3012156   82  Linux swap / Solaris

---

### Post by ibutho on 2008-06-29
Unfortunately it seems like you wiped off Windows when you installed Ubuntu. The output above shows that there are no Windows partitions on your hard disk.

---

### Post by upchucky on 2008-06-29
hes right, the one you see called filesystem is your main ubuntu install, the other is the extended partition you made for files, and the last is the swap file linux may or may not need but has to be there just in case.


if you have the live cd, knoppix works best, you can repartition the drive, blow away everything, install windows again, then install ubuntu, gotta install windows before installing ubuntu.

this time make sure u r not creating one drive for ubuntu.

---

### Post by arbjrm on 2008-07-06
deleted my post

---

