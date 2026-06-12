---
title: "[SOLVED] Grub creation error/bug?"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-11-16
I am curious whether this is a bug or not.

I have 4 HDD's:> 
 sudo blkid
/dev/sda1: UUID="32dd3252-53b9-4647-b538-95793e7a55e2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d81a0c0e-1b88-40fb-abed-2c9b15d0db6f" 
/dev/sdc1: UUID="30F70D6E790F4174" LABEL="Backups" TYPE="ntfs" 
/dev/sdd1: UUID="25610e0c-64f0-4512-a31c-49ddf2a9c1ff" TYPE="ext2" 
/dev/sdb3: UUID="4f92449d-38a5-4453-b22e-9e3785987a02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: TYPE="swap" UUID="67e9932c-9bf7-4186-b147-0b534ed4080f" 
/dev/sdf1: SEC_TYPE="msdos" UUID="48F4-EAEE" TYPE="vfat" 
/dev/sde1: SEC_TYPE="msdos" UUID="48EA-8696" TYPE="vfat" 
/dev/sdd5: TYPE="swap" UUID="bf5881cf-1674-4f8e-a1b7-96083c9f0dd2" 
/dev/sdg1: UUID="48F4-EAEE" TYPE="vfat" SEC_TYPE="msdos" 
/dev/sdd2: UUID="1306a0e0-da49-4c2a-bc75-87a7c682aba3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdg: LABEL="NEW VOLUME" UUID="E4B5-EDFE" TYPE="vfat" 
/dev/sdh1: UUID="0000-0000" TYPE="vfat" SEC_TYPE="msdos" 
/dev/sdi1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 
/dev/sdi: LABEL="NEW VOLUME" UUID="E4B5-EDFE" TYPE="vfat" 
/dev/sdb5: TYPE="swap" UUID="4e1e2438-4522-4134-95c5-af5de6d4b796" 
/dev/sdc3: UUID="4f92449d-38a5-4453-b22e-9e3785987a02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: TYPE="swap" UUID="67e9932c-9bf7-4186-b147-0b534ed4080f" 
/dev/sdc5: TYPE="swap" UUID="4e1e2438-4522-4134-95c5-af5de6d4b796" 
/dev/sdb1: UUID="ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d" SEC_TYPE="ext2" TYPE="ext3" I have Ubuntu 8.10 on hd1,0/sdb1.
I just installed Kubuntu 8.10 on hd2,0/sdc1

The grub was written to hd0,0 as the Ubuntu drive but is incorrect. This is the grub menu.lst that comes up upon start-up and was created after Kubuntu unstall:

> title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: 
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro single 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot
The first menu choice above is Kubuntu and the second, Ubuntu. As you can see the Ubuntu is shown as hd0,0. If I select that it starts loading with the Kubuntu splash but login is Ubuntu. I used Super Grub to boot from and edit the Ubuntu drive to hd1,0 and it loads with the Ubuntu splash and goes to the Ubuntu login.

Below is the Ubuntu menu.lst. which I edited. I removed the "root (hd0,0)" which was written in originally. This menu.lst is not the one loading at this time. I will edit the menu.lst which is currently loading and incorrect for Ubuntu.

> 
title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: KUBUNTU 8.10
root

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
kernel        /boot/memtest86+.bin
quietI know that I can delete any reference to hd0 or whatever and the OS will load according to the uuid without any problem.

I bring this up because I feel that this is where a lot of confusion and boot failures occur after an installation. This can be especially difficult to a new user.

The physical order of my HDD's is never anywhere similar to how grub writes or even how booting from a LiveCD reads it.

The actual order is, according to the bios boot listing:
**(1)** /dev/sdb3: UUID="4f92449d-38a5-4453-b22e-9e3785987a02" SEC_TYPE="ext2" TYPE="ext3"  ATA Hitachi 250Gib No OS IDE Primary/Master
**(2)** /dev/sda1: UUID="32dd3252-53b9-4647-b538-95793e7a55e2" TYPE="ext3" SATA Western Digital 160 Gib with Ubuntu, SATA1
**(3)** /dev/sdd2: UUID="1306a0e0-da49-4c2a-bc75-87a7c682aba3" SEC_TYPE="ext2" TYPE="ext3"  SATA Maxtor 160 Gib, SATA2 with Kubuntu 8.10
**(4)** /dev/sdc1: UUID="30F70D6E790F4174" LABEL="Backups" TYPE="ntfs" ATA with SATA adapter Western Digital 40 Gib, No OS, SATA3

Any thoughts?

I have read of this issue on Launch Pad and have reported similarity to pre-existing bug report.

---

### Post by meierfra. on 2008-11-16
> I am curious whether this is a bug or not.

As far as I can see, everything is working the way it is supposed to.

> The physical order of my HDD's is never anywhere similar to how grub writes or even how booting from a LiveCD reads it.

Ubuntu and grub (after boot up) have no knowledge of the physical order of the HHD's. So this problem is unavoidable.

On the other hand, grub at boot up  knows the order in the bios and orders the HDD's according to the Bios.


> I have Ubuntu 8.10 on hd1,0/sdb1.
I just installed Kubuntu 8.10 on hd2,0/sdc1

Are you sure? Accordingly to the informations you posted, I believe that Ubuntu is sda1 and Kubuntu is sdb1. This is how I see it

-----------Bios--Grub(at boot) -- Linux -- Grub(after boot)--------- UUID
Kubuntu:-- 1 ----  (hd0,0) -------sdb1 ----------  ??  --------- ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
Ubuntu--:-- 2 ---- (hd1,0) -------sda1 ---------- ??  ---------- 32dd3252-53b9-4647-b538-95793e7a55e2

> title Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash 
> As you can see the Ubuntu is shown as hd0,0. If I select that it starts loading with the Kubuntu splash but login is Ubuntu. I used Super Grub to boot from and edit the Ubuntu drive to hd1,0 and it loads with the Ubuntu splash and goes to the Ubuntu login.

(hd0,0) at boot up is your Kubuntu partition. So if you use (hd0,0) in menu.lst, the kernel from Kubuntu is loaded and you see the Kubuntu splash.  But the kernel line  has  root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2, which is the Ubuntu partition. So the kernel loads the filesystem on your ubuntu partition and the Ubuntu login is displayed.

(hd1,0) at boot up is the Ubuntu partition. So if you use (hd1,0) in menu.lst, the kernel from Ubuntu is loaded and you see the Ubuntu splash. The UUID in the kernel line stills belongs to Ubuntu and the Ubuntu login appears.

---

### Post by 73ckn797 on 2008-11-16
> **meierfra. said:**
> As far as I can see, everything is working the way it is supposed to.

Ubuntu and grub (after boot up) have no knowledge of the physical order of the HHD's. So this problem is unavoidable.

That has been obvious but creates confusion. I have learned to adjust to this but it still is an irritant. I am still a newbie.

> **meierfra. said:**
> On the other hand, grub at boot up  knows the order in the bios and orders the HDD's according to the Bios.

It was very late and I did give some slightly incorrect info.
The actual BIOS order is:
Hard drive physical order in BIOS:
IDE Channel 0 Master = Hitachi 250Gib No OS format ext3 (PATA)
IDE Channel 0 Slave  = ------
IDE Channel 2 Master = WD 160Gib Ubuntu 8.10 (SATA1 channel) (on Mobo)
IDE Channel 2 Slave  = WD 40Gib No OS ntfs (PATA w/SATA adapter on SATA2 channel)
IDE Channel 3 Master = Maxtor 160Gib Kubuntu 8.10 (SATA3 channel)
IDE Channel 3 Slave  = CD/DVD (SATA4 channel)

The order listed from GParted is:
/dev/sda = IDE Channel 2 Master = WD 160Gib Ubuntu 8.10 (SATA)
/dev/sdb = IDE Channel 3 Master = Maxtor 160Gib Kubuntu 8.10 (SATA)
/dev/sdc = IDE Channel 2 Slave  = WD 40Gib No OS ntfs (PATA w/SATA adapter)
/dev/sdd = IDE Channel 0 Master = Hitachi 250Gib No OS format ext3 (PATA)

As you see and pointed out, Ubuntu reads a different order. Grub keeps writing sda as hd0,0 (which is logical) but in reality it will not boot unless I change it to hd1,0. Is that where the grub actually is residing and so reads that way? That would make sense then.


> **meierfra. said:**
> Are you sure? Accordingly to the informations you posted, I believe that Ubuntu is sda1 and Kubuntu is sdb1. This is how I see it

-----------Bios--Grub(at boot) -- Linux -- Grub(after boot)--------- UUID
Kubuntu:-- 1 ----  (hd0,0) -------sdb1 ----------  ??  --------- ce6c2aec-04dd-4729-aeb8-0ea4fec8ca5d
Ubuntu--:-- 2 ---- (hd1,0) -------sda1 ---------- ??  ---------- 32dd3252-53b9-4647-b538-95793e7a55e2

(hd0,0) at boot up is your Kubuntu partition. So if you use (hd0,0) in menu.lst, the kernel from Kubuntu is loaded and you see the Kubuntu splash.  But the kernel line  has  root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2, which is the Ubuntu partition. So the kernel loads the filesystem on your ubuntu partition and the Ubuntu login is displayed.

(hd1,0) at boot up is the Ubuntu partition. So if you use (hd1,0) in menu.lst, the kernel from Ubuntu is loaded and you see the Ubuntu splash. The UUID in the kernel line stills belongs to Ubuntu and the Ubuntu login appears.

You are correct and I stand corrected.

Again, it can become confusing at times and I see many posts from even newer users that install to systems with multiple drives. It is probably my using 4 HDD's that is creating this confusion with myself! Knowing my system does allow me to quickly correct these sort of issues.

Wondering if there is a bug is due to the way drives are read so differently. I do like the uuid usage and, as mentioned, eliminate the hd0,0 references all together.

---

### Post by meierfra. on 2008-11-16
> Grub keeps writing sda as hd0,0 (which is logical) but in reality it will not boot unless I change it to hd1,0. 

You have to distinguish between the grub which is running during boot up and the grub which is running after you successfully  booted  into (K)ubuntu.
The grub at boot up sees the drives according to the boot order in the bios.  The grub in (K)ubuntu  creates its own order (which often  agrees with "fdisk -l")

In your case  grub during boot up sees sda as (hd1,0) and grub in (K)ubuntu sees  sda as (hd0,0).

Of course this is confusing and creates problems.  But it is not a bug.   

> Hard drive physical order in BIOS:


In addition to the physical order, do your bios allow you to set a boot order?  That is, which drive  to boot from,  and if that one fails, which one to try next, and so on?

Grub during boot up, orders the drive according to the boot order in the bios, not according to the physical order.

---

### Post by 73ckn797 on 2008-11-16
> **meierfra. said:**
> In addition to the physical order, do your bios allow you to set a boot order?  That is, which drive  to boot from,  and if that one fails, which one to try next, and so on?

Grub during boot up, orders the drive according to the boot order in the bios, not according to the physical order.


Yes it does and I played around and re-ordered it which completely changes how the system boots.

Thanks for the info. I helps me a lot. When I get this I will probably find something else to be confused with  :).

---

