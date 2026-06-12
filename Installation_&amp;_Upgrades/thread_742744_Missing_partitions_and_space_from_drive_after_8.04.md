---
title: "Missing partitions and space from drive after 8.04 upgrade"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by NanoTech on 2008-04-02
Hi, I've recently tried to upgrade my Ubuntu 7.10 installation (Which worked perfectly fine to my knowledge. I didn't use it much though) to the 8.04 beta. Upon rebooting and selecting Ubuntu-linux, I got the following:

```
	Booting 'Ubuntu hardy (development branch), kernel 2.6.24-12-generic'
	
	
Warning: Unrecognized partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool(err=26). Current C/H/S=16383/240/63 find --set-root-ignore-floppies /boot/grub/menu.lst

Error 17: File not found

Press any key to continue...
```

Pressing any key gives you the grub menu, but the top header part looks different than a normal install. (I used the wubi tool on the 7.10 cd to install. Note that the tool on the 7.10 cd isn't the full wubi.)

```
GRUB4DOS 0.4.3 2007-10-21, Memory 637K / 1021M, CodeEnd: 0x41538
```

None of any of the options work and all return the same "Error 17: File not found" as above.

The cause of this seems to be that everything past the end of my Windows XP partition doesn't exist. (Ubuntu is/was installed after that)

Here's the result from fdisk -lu:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059250016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Device 		Boot	Start		End		Blocks		Id	System
/dev/sda1		63		16798319		8399128+ 	c 	W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2	*	16803990		488392064	235794037+	7 	HPFS/NTFS
```

The drive appears the same in both GParted and the Windows Disk Manager with it only showing as around 232 GB rather than the correct 250 GB. Note that Windows XP still works fine despite the missing space.

Thanks in advance. :)

---

