---
title: "Error dual booting Ubuntu 6.06 and WinXP with separate HD's"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by whimbrel46 on 2006-10-17
First of all: I am not an experienced Ubuntu user. But I'm learning. Ubuntu looks very good, and I want to give it a serieous try to replace Win XP.

I tried the following: 

- Existing Windows XP install is on two serial harddisks, connected to 1st and 2nd port on the motherboard.
- I disconnected these two HD's and connected a third HD to the 3rd port on the MB. I set the BIOS to boot from this disk. I installed Ubuntu 6.06 LTS via the installation DVD.
- I reconnected the two HD's and restarted, using the 3rd disk to boot from.
- Ubuntu started fine.
- My intention is/was to edit the grub menu lst file to include a Windows XP boot option. In this way, the Windows install is completely separate.
- After checking out if Windows would still boot with the 3rd disk in the system (I set 1st HD as the boot disk in BIOS) and returning to Ubuntu (setting the 3rd HD to be the boot disk in the BIOS) something was wrong:

Uncompressing Linux. . . ok, booting the kernel.
mount: Mounting /dev/sda1 on /root failed: invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off

-This is what happens when make the 3rd disk the only disk in the system, run the live CD and try to mount /dev/sda2 on the Linux drive.

mount:	wrong fs type, bad option, bad superblock on /dev/sda1, 
missing codepage or other error 
In some cases useful info is found in syslog - try 
dmesg | tail or so

- I have searched for other users with the same problem and found a number of threads:

On this forum:
[http://www.ubuntuforums.org/showthread.php?t=257790]("job control turned off (help please) ")

On the German Ubuntu forum
[http://forum.ubuntuusers.de/topic/25877/]("Windows "zerstört" Kubuntu-Partition - Thema anzeigen")

I am aware that having more than one HD can create a mix-up in drives (/dev/…) but sofar, it seems as if Windows modifies the Ubuntu partition.

Does anyone know?

---

### Post by Kateikyoushi on 2006-10-17
There is a bug on launchpad related to mixing sata and pata disk and changing the boor order.
I think it wasn't windows what cause this, because I also have multi drive dualboot and works more likely changing the boor order did.

When launchpad comes up I find the bug.

Could you show the output of this command from the live disc ?
```
sudo fdisk -l
```

If you can mount the ubuntu partition taking a look at your fstab would also help, after you give the fdisk's output we can tell how to mount it.

---

### Post by jhenager on 2006-10-17
I also had trouble setting up a dual boot system.
With SuSE, it automatically created a grub entry for Windows, and you just select whichever you want from a menu at bootup.
When I installed Ubuntu to my blank slave HD, it went ahead and  overwrote the MBR on the master. It wasn't really a big issue, since it had Vista RC1 on it, and I hadn't made a lot of changes to it yet.
Anyway, that was a little disappointing that even though I specified hdb as the destination.
What I ended up doing was disconnect one disk, make the remaining one master, install the OS, then swap them out and install the other one. 
Fortunately, my new m/b lets me change the boot device by hitting F8 or F12, and pick the one I want.

---

### Post by whimbrel46 on 2006-10-17
This is the result of sudo fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150255913+  83  Linux
/dev/sda2           18707       19457     6032407+   f  W95 Ext'd (LBA)
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdf: 517 MB, 517996544 bytes
32 heads, 32 sectors/track, 988 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         988      505839+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(986, 31, 32) logical=(987, 31, 31)

---

