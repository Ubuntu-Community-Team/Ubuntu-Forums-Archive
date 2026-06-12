---
title: "can not boot"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by ccl4 on 2008-07-10
hello,
i have problem with grub when i turn on my comuputer, (i have ubuntu and windows vista). it shows >        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

 and as followed the re installition of grub it shows > Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.l
st "... failed

Error 22: No such partition

so what should i do??? please help****

---

### Post by matthewbpt on 2008-07-10
Seems alot of people are having grub troubles today!
What hard drive and partition do you have Ubuntu installed on? It seems that GRUB is looking for the boot menu in the wrong partition or something like that =S
Looking in the grub manual ([http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)) it says the following about error 22:
> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

---

### Post by ccl4 on 2008-07-10
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
129 heads, 4 sectors/track, 454344 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000a6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4    14336027     7168012    7  HPFS/NTFS
/dev/sda2   *    14336028   131555747    58609860    7  HPFS/NTFS
/dev/sda3       131555748   225304691    46874472    f  W95 Ext'd (LBA)
/dev/sda4       225304692   234441503     4568406   82  Linux swap / Solaris
/dev/sda5       131555752   196440683    32442466    7  HPFS/NTFS
/dev/sda6       196440688   225304691    14432002   83  Linux

please help!!!

---

### Post by logos34 on 2008-07-10
> **ccl4 said:**
>  /dev/sda6       196440688   225304691    14432002   83  Linux

That's root.  Grub sees it as '(hd0,5)'.

Maybe you ran the wrong partition #:
> Running "embed /boot/grub/e2fs_stage1_5 (hd0,**6**)"... failed (this is not fatal)...

Try:

> sudo grub

grub> **find /boot/grub/stage1**
(this should output 'hd0,5')
grub> **root (hd0,[COLOR=Blue]5[/COLOR])**
grub> **setup (hd0)**
grub> **quit**

---

### Post by SkonesMickLoud on 2008-07-10
Grub names drives and partitions starting with 0.  So the way grub sees it, your sda6 is actually (hd0,5).

---

### Post by logos34 on 2008-07-10
> **SkonesMickLoud said:**
> So the way grub sees it, your sda6 is actually (hd0,5).

I just said that.

---

### Post by ccl4 on 2008-07-10
> grub> find /boot/grub/stage1
 (hd0,6)

what is wrong????.....:(

---

### Post by logos34 on 2008-07-10
ok, somethings screwy, because there's only one partition listed in fdisk that can possibly be root, and that's sda6, which grub should see as 'hd0,5'.  There is no 'hd0,6'/sda7....in fact there's not even space for it, since the partitions listed take up the entire disk.

Try running [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") from the live cd--maybe the partition table is wrong and needs fixing.

system>admin>software sources>enable **universe** repo

sudo apt-get install testdisk

sudo testdisk

Read the documentation and [this page]("http://www.users.bigpond.net.au/hermanzone/p21.html") first.

Or try Super Grub Disk--maybe it can boot ubuntu.

Or restore the vista bootloader and then use EasyBCD to dual boot.

---

