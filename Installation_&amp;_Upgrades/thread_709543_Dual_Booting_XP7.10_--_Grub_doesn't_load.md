---
title: "Dual Booting XP/7.10 -- Grub doesn't load"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by ejreynolds on 2008-02-27
Hi All,

Hope somebody can help me.  I just recently installed 7.10.  I already had a XP installation on the drive.  I used a qparted livecd to resize that partition and give up some free space to create both an ext3 partition for my ubuntu install and some swap space.  I installed ubuntu and everything works great.  I restarted, got the grub menu, selected windows and I booted into windows correctly.  However when I restarted to go back in *nix, GRUB didn't come up and it went straight back into windows.  The only way I can get back into Ubuntu is to run the qparted livecd again, and turn off the "boot" flag on my windows partition.  Then I can reboot and grub shows up again.  But when I select windows, I get locked into using windows and grub dissapears again.  I have no idea why the boot flag for my windows partition keeps getting set (and honestly I'm not entirely sure what its purpose is).  Also, I can restarted multiple times and get back into ubuntu, its just when I select xp do I get stuck with xp.

If it helps, I ran "fdisk -lu":
Disk /dev/hda: 160.0 GB, 160041885696 bytes
150 heads, 63 sectors/track, 33077 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0af20af2

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    12171599     6085768+   b  W95 FAT32
/dev/hda2   *    12171600   312568199   150198300    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79cb6742

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   446446349   223223143+   7  HPFS/NTFS
/dev/sda2       446446350   488392064    20972857+   f  W95 Ext'd (LBA)
/dev/sda5   *   446446413   486303614    19928601   83  Linux
/dev/sda6       486303678   488392064     1044193+  82  Linux swap / Solaris

Edit: Also when I run the same tool when I'm having this no-showgrub issue there is an askterisk next to /dev/sda1 which i'm assuming means it is flagged as bootable.

Thanks!
-Erik

---

### Post by Pumalite on 2008-02-27
Set the flag to hda1 and see what happens.(the problem might be that you have XP in hda2 and Grub might have installed to hda1)

---

### Post by Belak on 2008-02-27
> **Pumalite said:**
> Set the flag to hda1 and see what happens.(the problem might be that you have XP in hda2 and Grub might have installed to hda1)

The **boot** flag should be on the Ubuntu partition if the previous message was unclear

---

### Post by Fire_Chief on 2008-02-27
Hi Eric,

Did you tell the installer to put Grub in the MBR of the system during the installation? (more specifically on the MBR of the first drive the system attempts to boot from?)

Regards,
Fire_Chief

---

### Post by Pumalite on 2008-02-27
Have you looked at your sudo fdisk?
The flag is set to hda2 also.

---

### Post by dstew on 2008-02-27
About the boot flag, its use is for the Windows-type boot loader. The BIOS is supposed to load and execute whatever is in the MBR of the boot disk. In Windows, that boot loader looks for a partition with a boot flag, and loads the boot sector of that partition, and jumps to it. The boot loader checks the boot flag also. In Linux, the grub boot loader is configured to load its stage1.5 from the rest of track0 of the boot drive. It is targeted to stage1.5 by a block addressing scheme that ignores the boot flag. Stage1.5 is targeted to the grub root partition which contains stage2 by a similar addressing scheme, and also ignores the boot flag. Once stage2 is loaded, the kernel is selected and grub is done.

The problem is that some BIOSes check for a boot flag *before* they load the MBR into memory. This is a hardware specific problem. See this [thread]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115633"). However, in those cases I don't think it matters which partition on the boot drive has the boot flag activated if grub is in the MBR.

As far as the flag getting reset, that I don't know about, but the makeactive directive in the grub menu for booting Windows will set the boot flag, because the Windows boot loader checks for it. Also, the boot flag only works in Windows if it is set in a primary partition. Therefore the boot flag in your /dev/sda5 partition would be seen by Windows as no boot flag on that disk.

Maybe your behavior is due to the BIOS trying to directly boot the flagged partition. Some BIOSes can do this. If so, you might be able to install grub onto a *partition* instead of into the MBR, set the boot flag to that partition (to instruct your BIOS, not grub) and then it might work properly.

---

### Post by ejreynolds on 2008-02-27
I realized I had an old 5 gig or so partition at the beginning of hda1 which I got rid of and shifted/resized the larger partition.  Fixed everything.  Thanks for everyone's help!!

---

### Post by Pumalite on 2008-02-27
Good Luck.

---

