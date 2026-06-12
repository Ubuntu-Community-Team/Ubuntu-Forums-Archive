---
title: "Moved to SSD, Ubuntu boots, but not other OSes?"
date: 2019-08-19
forum: Installation &amp; Upgrades
---

### Post by tressie on 2019-08-19
Hi,

I had a triple boot Ubuntu, XP, Windows 7 installation going fine on mechanical hard disks.

I created 2 NTFS partitions on my new SSD with Windows 7, then did my best to clone the XP and Windows7 partitions onto these with Ubuntu's dd.

I then installed a fresh copy of Ubuntu 18.04. It found the extra partitions, and set-up a triple boot grub configuration for me.

Okay, so now Ubuntu boots fine, but XP and Windows 7 do nothing when selected at boot. I tested the partitions, repaired and re-tested them with the GUI disks utility. They appear okay.

I can now mount the XP and Windows 7 partitions, and see that all my files are there. Anytime I select either of the MS partitions at boot however, and nothing!

fdisk says the following:

$ sudo fdisk -l /dev/sda
Disk /dev/sda: 447.1 GiB, 480102899200 bytes, 937700975 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x79bcd2dd

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 368642047 368640000 175.8G  7 HPFS/NTFS/exFAT
/dev/sda2       368642048 757762047 389120000 185.6G  7 HPFS/NTFS/exFAT
/dev/sda3       757764094 937699327 179935234  85.8G  5 Extended
/dev/sda5       757764096 937699327 179935232  85.8G 83 Linux


Anyone have any idea of what I've done wrong, or able to direct me to appropriate resolution procedures?

Thanks,
T.

---

### Post by SeijiSensei on 2019-08-19
I cloned the physical drives in two laptops to similarly sized (500 GB) SSD by using ddrescue ("sudo apt install gddrescue").  They booted up exactly as the original disks did because the SSD were byte-for-byte copies of the originals.  I connected the SSD with a USB->SATA device, then ran 
```
sudo ddrescue /dev/sda /dev/sdb
```
waited a few hours, and that was it.

---

### Post by tressie on 2019-08-19
> **SeijiSensei said:**
> I cloned the physical drives in two laptops to similarly sized (500 GB) SSD by using ddrescue ("sudo apt install gddrescue").  They booted up exactly as the original disks did because the SSD were byte-for-byte copies of the originals.  I connected the SSD with a USB->SATA device, then ran 
```
sudo ddrescue /dev/sda /dev/sdb
```
waited a few hours, and that was it.

Hi SeijiSensei,

Thanks very much for reading my post, and for the much valued response.

Yep, I might need to start over with ddrescue, but I'm a day into it thus far. I also cloned the 2 MS partitions onto far smaller partitions on the SSD with dd, which I think may have contributed to the problem, certainly to their failing the GUI 'drives' utility test.

Lemmy keep that one as a back-up solution for now, and see if anyone else can suggest a precise cause for the MS partitions not booting, overnight.

Thanks again,
T.

---

### Post by tressie on 2019-08-19
Here's a quick thought:

Since having 'repaired' the XP and Windows 7 partitions with the Ubuntu GUI 'disks' tool, I haven't made any changes to the Ubuntu installation. It's conceivable that grub is still trying to multi-boot into partitions that it has prior, defective information about.

Rather than redo the entire Ubuntu install, subsequent to having another try at cloning the partitions, perhaps I should first try to re-install the grub multi-boot functionality, in the hope that it may be better able to configure itself with the 'repaired' partitions.

What I'll have to look at then, is a re-install of grub, so for now that's my focus. Any links/ tips appreciated, but I'll let everyone know if I find a solution independently in the mean time.

T.

---

### Post by tressie on 2019-08-19
Okay, I tried fixing the grub installer, then re-installing Ubuntu, then I messed-up the partitions I was trying to boot.

To re-instate the partitions to the SSD, I used [COLOR=#000000]SeijiSensei's method with ddrescue. It also ran out of space on the new drives, and gave me 'broken' copies of the partitions.

Without resorting to a windows disk clone utility, unless there's one that is both free and trustworthy, how do I go about shrinking the XP and Windows7 partitions, from almost empty, larger HDD residence, to more compact SSD installation?

T.[/COLOR]

---

### Post by tressie on 2019-08-19
Okay, since MiniTool Partition Wizard has gone 100% pay (correct me if I'm wrong), I went with EaseUS to copy and resize the partitions. That made me nervous, and left behind non-removable junk I should have been more wary of before I installed it.

In any case, I have a functional, 3-system bootable computer now, so issue resolved.

How do i mark the thread title as resolved, I wonder?

T.

---

