---
title: "Wanna go from multi-boot to Ubuntu only"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by dkjMusic on 2010-09-26
I now have a quadruple-boot system with Ubuntu, XP, Vista, and Win7 (don't ask why). When I boot the PC, I get choices for Linux kernel and Windows 7 loader. If I choose the Win7 loader, I then get options for XP, Vista, and Win7.

GParted shows XP as the boot partition.

I want to can the Windows partitions, give their disk space to Ubuntu, and keep a partition I have for documents,

What are your recommendations for doing this so that I don't, for example, erase the entire disk and lose my Documents partition? Just unmount each Windows partition and free up the corresponding space, then expand Ubuntu to gooble up the free space?

---

### Post by sikander3786 on 2010-09-26
> Just unmount each Windows partition and free up the corresponding space, then expand Ubuntu to gooble up the free space?

Exactly that. If you want to keep your Documents partition, you can keep it. Otherwise copy them to your home folder/partition and let that partition disappear as well.

After that you'll also have to reinstall GRUB. I'll recommend that you create a separate /boot partition, 512MB atleast formatted ext3 and let GRUB install into it.

---

### Post by dkjMusic on 2010-09-27
> **sikander3786 said:**
> Exactly that. If you want to keep your Documents partition, you can keep it. Otherwise copy them to your home folder/partition and let that partition disappear as well.

After that you'll also have to reinstall GRUB. I'll recommend that you create a separate /boot partition, 512MB atleast formatted ext3 and let GRUB install into it.

OK. I got rid of every partition except for Maverick and my separate Documents. I then created an EXT4 partition and installed Lucid on it. So I can now boot into a "stable" Lucid or the "developmental" (not much longer) Maverick. Lucid is the default bootup.

When I opt to boot up Maverick, I get messages that indicate it thinks the three Windows partitions are still there. Is that an artifact due to my not yet reinstalling grub2?

I really appreciate your help on this.

---

### Post by sikander3786 on 2010-09-28
> 
When I opt to boot up Maverick, I get messages that indicate it thinks the three Windows partitions are still there. Is that an artifact due to my not yet reinstalling grub2?


I can't actually understand that statement. Does selecting Maverick bring up another GRUB menu where Windows is listed?

---

### Post by dkjMusic on 2010-09-30
> **sikander3786 said:**
> I can't actually understand that statement. Does selecting Maverick bring up another GRUB menu where Windows is listed?

Yeah, I'm sorry, that wasn't very clear.

When I select Maverick for the boot, the Ubuntu splash screen appears and I get messages which read e.g. "The disk drive for /media/Windows7 is not ready yet or not present. Press S to skip..."

After pressing S for each of the unavailable disks that I deleted via GParted, Maverick boots just fine.

---

### Post by Rubi1200 on 2010-09-30
Try running ```
sudo update-grub
``` from within Ubuntu.

---

### Post by coffeecat on 2010-09-30
> **dkjMusic said:**
> When I select Maverick for the boot, the Ubuntu splash screen appears and I get messages which read e.g. "The disk drive for /media/Windows7 is not ready yet or not present. Press S to skip..."

It could be that you have entries in /etc/fstab for automounting the three Windows partitions. Did you ever use ntfs-config or did you ever edit fstab yourself?

Post the contents of /etc/fstab and we can see. While you're about it, post the terminal output of:

```
sudo fdisk -lu
```

.. so that we can see your present partition layout.

---

### Post by dkjMusic on 2010-10-01
> **coffeecat said:**
> It could be that you have entries in /etc/fstab for automounting the three Windows partitions. Did you ever use ntfs-config or did you ever edit fstab yourself?

Post the contents of /etc/fstab and we can see. While you're about it, post the terminal output of:

```
sudo fdisk -lu
```

.. so that we can see your present partition layout.

I edited /media/fstab and did use ntfs-config.

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda9 :
UUID=ac0418a2-96b6-4995-b9f8-b42c765cb207	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=597282D273F915F2	/media/Documents	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda1 :
UUID=8AE410441887E334	/media/Local_Disk	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda8 :
UUID=01CAE569206335E0	/media/Ubuntu	ntfs-3g	defaults,locale=en_US.utf8	00
#Entry for /dev/sda5 :
UUID=01CA953818290890	/media/Vista	ntfs-3g	defaults,locale=en_US.utf8	00
#Entry for /dev/sda6 :
UUID=01CB04F03F2BFA60	/media/Windows_7	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda10 :
UUID=d472208e-c229-4e6a-a529-aea9e587099a	none	swap	sw	0	0

$ sudo fdisk -lu
[sudo] password for dennis: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    43825151    21911552   83  Linux
/dev/sda2        43827198   467989887   212081345    f  W95 Ext'd (LBA)
/dev/sda5        45817443   274679369   114430963+  83  Linux
/dev/sda6       274681856   278132735     1725440   82  Linux swap / Solaris
/dev/sda7       278133415   467989887    94928236+   7  HPFS/NTFS
/dev/sda8        43827200    45815807      994304   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001425 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1             245     3999743     1999749+   b  W95 FAT32

---

### Post by coffeecat on 2010-10-01
> **dkjMusic said:**
> I edited /media/fstab and did use ntfs-config.

I think you mean that you edited /etc/fstab, not /media/fstab. Anyway - I thought as much: when you boot up, fstab is trying to mount partitions that are no longer there. First - my apologies - but we need another output before you can decide what to edit in fstab. We can probably work it out from the information so far, but I would prefer to double-check the UUIDs. When you deleted the NTFS partitions, some of the other sda numbers got changed. That doesn't matter particularly because fstab uses UUIDs, but the commented /dev/sda* references are now misleading. For example:

> ```
#Entry for /dev/sda8 :
UUID=01CAE569206335E0    /media/Ubuntu    ntfs-3g    defaults,locale=en_US.utf8    00
``````
/dev/sda8        43827200    45815807      994304   82  Linux swap / Solaris
```It looks as though you are mounting the swap partition with the ntfs-3g driver. :-s You aren't (I hope!) but we need the UUIDs to be sure. Also, naming a mountpoint /media/Ubuntu for a NTFS partition worries me.

Anyway. Post the terminal output of:

```
sudo blkid
```Which will give us all the UUIDs and then we can see what's going on and take it from there.

---

### Post by dkjMusic on 2010-10-01
> **coffeecat said:**
> I think you mean that you edited /etc/fstab, not /media/fstab. Anyway - I thought as much: when you boot up, fstab is trying to mount partitions that are no longer there. First - my apologies - but we need another output before you can decide what to edit in fstab. We can probably work it out from the information so far, but I would prefer to double-check the UUIDs. When you deleted the NTFS partitions, some of the other sda numbers got changed. That doesn't matter particularly because fstab uses UUIDs, but the commented /dev/sda* references are now misleading. For example:

It looks as though you are mounting the swap partition with the ntfs-3g driver. :-s You aren't (I hope!) but we need the UUIDs to be sure. Also, naming a mountpoint /media/Ubuntu for a NTFS partition worries me.

Anyway. Post the terminal output of:

```
sudo blkid
```Which will give us all the UUIDs and then we can see what's going on and take it from there.

No, really, I did edit /media/fstab. Whoops, wait a sec, make that /media/.created_by_python-fstab. I don't know what I'm doing.:confused:

As far as /media/Ubuntu, that was a left-over partition that I was trying to use as the disk for an Ubuntu virtual machine, which didn't stick.

OK, w/o further adieu here's

$ sudo blkid
[sudo] password for dennis: 
/dev/sda1: LABEL="Lucid" UUID="509e43e9-202b-43ea-99f5-3ffe255fe4a6" TYPE="ext4" 
/dev/sda5: LABEL="Maverick" UUID="ac0418a2-96b6-4995-b9f8-b42c765cb207" TYPE="ext4" 
/dev/sda6: UUID="d472208e-c229-4e6a-a529-aea9e587099a" TYPE="swap" 
/dev/sda7: LABEL="Documents" UUID="597282D273F915F2" TYPE="ntfs" 
/dev/sda8: UUID="0bf48094-c1bc-4d7c-a3e6-ad0a03a6596a" TYPE="swap" 
/dev/sdf1: LABEL="BACKUPS" UUID="2CA7-9FE2" TYPE="vfat"

I do thank you for being thorough so I don't have to do this all over again.:)

---

### Post by coffeecat on 2010-10-01
Righty-ho. here's your /etc/fstab as it is now, except that I've added blank lines in between each functional line to make it easier to read and to see which comment belongs where.

> **dkjMusic said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0

#Entry for /dev/sda9 :
UUID=ac0418a2-96b6-4995-b9f8-b42c765cb207    /    ext4    errors=remount-ro    0    1

#Entry for /dev/sda7 :
UUID=597282D273F915F2    /media/Documents    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0

#Entry for /dev/sda1 :
UUID=8AE410441887E334    /media/Local_Disk    ntfs-3g    defaults,locale=en_US.utf8    0    0

#Entry for /dev/sda8 :
UUID=01CAE569206335E0    /media/Ubuntu    ntfs-3g    defaults,locale=en_US.utf8    00

#Entry for /dev/sda5 :
UUID=01CA953818290890    /media/Vista    ntfs-3g    defaults,locale=en_US.utf8    00

#Entry for /dev/sda6 :
UUID=01CB04F03F2BFA60    /media/Windows_7    ntfs-3g    defaults,locale=en_US.utf8    0    0

#Entry for /dev/sda10 :
UUID=d472208e-c229-4e6a-a529-aea9e587099a    none    swap    sw    0    0

```

If you check the UUIDs against your blkid output, you'll see that:

What was sda9 is now sda5 (your root partition).
What was sda7 is still sda7 (your ntfs Documents partition).
What was sda1 (ntfs) is now sda1 (ext4) with a label="Lucid".
What was sda8 (ntfs) no longer exists.
What was sda5 (ntfs) no longer exists.
What was sda6 (ntfs) no longer exists.
What was sda10 is now sda6 (your swap partition).

Which means we have identified the four lines in /etc/fstab that are causing the error messages now that the partitions have been deleted or reformatted. That is, three partitions deleted and one reformatted to ext4. You need to edit /etc/fstab. Open a text editor with root privileges with:

```
gksudo gedit /etc/fstab
```Be careful what you do now or you might make your system unbootable. It would be repairable but let's not go down that route. :wink: You have two choices. Either delete the unwanted lines, which are:

```
#Entry for /dev/sda1 :
UUID=8AE410441887E334    /media/Local_Disk    ntfs-3g    defaults,locale=en_US.utf8    0    0

#Entry for /dev/sda8 :
UUID=01CAE569206335E0    /media/Ubuntu    ntfs-3g    defaults,locale=en_US.utf8    00

#Entry for /dev/sda5 :
UUID=01CA953818290890    /media/Vista    ntfs-3g    defaults,locale=en_US.utf8    00

#Entry for /dev/sda6 :
UUID=01CB04F03F2BFA60    /media/Windows_7    ntfs-3g    defaults,locale=en_US.utf8    0    0
```Or comment them out with a # symbol at the beginning of the functional lines, like this:

```
#Entry for /dev/sda1 :
#UUID=8AE410441887E334    /media/Local_Disk    ntfs-3g    defaults,locale=en_US.utf8    0    0

#Entry for /dev/sda8 :
#UUID=01CAE569206335E0    /media/Ubuntu    ntfs-3g    defaults,locale=en_US.utf8    00

#Entry for /dev/sda5 :
#UUID=01CA953818290890    /media/Vista    ntfs-3g    defaults,locale=en_US.utf8    00

#Entry for /dev/sda6 :
#UUID=01CB04F03F2BFA60    /media/Windows_7    ntfs-3g    defaults,locale=en_US.utf8    0    0
```Make sure that the lines for sda7 and the swap partition don't run into each other. It's quite OK to have blank lines. Now save the edited file, reboot and the errors should have gone.

**Edit:** You now have a second swap partition, sda8, presumably as a result of your reinstall of Lucid. This is not a problem except that it's unnecessary - on a multiboot the swap can be shared unless you rely on hibernation. If you want to get rid of one of those swap partitions, you'll need to edit /etcc/fstab in either Lucid or maverick, depending which one you get rid of. Enjoy! :p

---

### Post by dkjMusic on 2010-10-01
I commented out the lines in /etc/fstab related to the "ghost" partitions. Maverick now restarts without any reference to the bygone disks.

Thanks again so much for your help.

---

### Post by coffeecat on 2010-10-01
Excellent - glad it's sorted. One little tip. If you ever need to automount ntfs partitions in the future, I would suggest avoiding ntfs-config. It's widely recommended in these forums, but I am of the opinion mistakenly so. It was a good idea but it has rough edges and has not been developed at all (seemingly) since it was first coded. I've been involved in threads where it has done unfortunate things. Now that you are comfortable editing /etc/fstab, it's much better to do this yourself.

Good luck!

---

