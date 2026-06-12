---
title: "Grub installed on wrong drive"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by GacaP on 2008-10-10
I have three drives. I used Acronis disk director to create a 30gb ext3 partition on my third 'warehouse' drive. I then rebooted and used a live CD to install ubuntu. That went fine.
The problem: when grub asked to install to HD0, I assumed that was my first drive and said yes. It wasn't. So now on reboot it loads straight into windows. I can get into Ubuntu by booting from the CD and then selecting boot from HD, where it will apparently look at the (in)correct drive and load grub.

How do I install grub onto the drive that my PC actually looks at before loading? How do I make sure that that is the right drive and that I am not erasing the start of something else?

Thanks for any help.

---

### Post by Pumalite on 2008-10-10
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-10-10
How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```

Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=512 count=1 2>/dev/null | strings | grep -i grub
```
So replace "sda" above with each of your drives. And finally, for each command that returns "GRUB" from the command above, please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". We can use the info from those commands to figure out exactly which MBR (Master Boot Record) Grub was installed to, and also which drive and partition Grub points to for its system files. That should greatly clarify your setup.

---

### Post by GacaP on 2008-10-11
**fdisk -lu:**

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc493bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   913841459   456920698+   7  HPFS/NTFS
/dev/sda2       913841460   972446579    29302560   83  Linux
/dev/sda3       972446580   976768064     2160742+   5  Extended
/dev/sda5       972446643   976768064     2160711   82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbe90be90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   145195469    72597703+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17da17da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   398267414   199133676    7  HPFS/NTFS


**sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub**
sda: GRUB
sdb: nothing
sdc: nothing

**sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump**
0000000 ff01                                   
0000002

---

### Post by caljohnsmith on 2008-10-11
OK, so according to those commands, you have Grub installed to your sda drive, and Grub is using partition sda2 for its system files (like menu.lst), so that's perfect. It looks like the only issue is that you have your BIOS set to boot the wrong HDD on start up (probably sdb as that looks like it has a bootable Windows on it), so most likely all you need to do is go into BIOS and change your boot order so that sda gets booted first. Let me know how that goes or if you run into problems. :)

---

### Post by GacaP on 2008-10-12
Ha yes, that solved it. Thanks for your help.

---

### Post by caljohnsmith on 2008-10-12
Glad you've got it booting correctly now. Cheers and have fun. :)

---

