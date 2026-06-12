---
title: "Installing  Ubuntu on an existing Ubuntu partition"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by happyytilton on 2015-05-03
How do you install Ubuntu to an existing Ubuntu partition. Appears to be no option to install to a specified partition, from the "Live" install disk.

**System:**
Dell 1705
Intel Core 2 Duo @ 1,8Ghz
nVidia 7900[SIZE=3]
Broadcom BCM 4311[/SIZE] wireless carc
2G ram
160 HDD

**Partitions (NTFS):**
C- XPPro
E- Documents
R- XP Recovery
V- Video

**Partitions (Linux):**
sda7- Linux Mint 17.1
sda8- Swap
sda9- Ubuntu 14.10

**The way Linux shows the partitions from the terminal:**
Device Boot          Start         End                 Blocks                  Id  System
/dev/sda1   *                63    62910539      31455238+     7  HPFS/NTFS/exFAT - "*[COLOR=#0000ff]C: Windows XPPro[/COLOR]*"
/dev/sda2        62910540    146898359    41993910       7  HPFS/NTFS/exFAT - "*[COLOR=#0000ff]E: My Documents[/COLOR]*"
/dev/sda3       146898421   312580095    82840837+     f  W95 Ext'd (LBA)
/dev/sda5       146898423   188715554    20908566       17  Hidden HPFS/NTFS - "[COLOR=#0000ff]*R: Recovery*[/COLOR]"
/dev/sda6       188715618   209680379    10482381       7  HPFS/NTFS/exFAT - "*[COLOR=#0000ff]V: Video[/COLOR]*"
/dev/sda7       209680384   268254065    29286841       83  Linux - "[COLOR=#0000ff]*Mint 17.1*[/COLOR]"
/dev/sda8       308393984   312580095      2093056       82  Linux swap / Solaris
/dev/sda9       268255232   308383743    20064256       83  Linux - "[COLOR=#0000ff]*Ubuntu 15.04*[/COLOR]"

I would like to be able to install Ubuntu 14.04.2LTS to the /dev/sda9 partition and still have the "triple boot" capability that I have now.

**In other words, the disk should ask:**
What partition would you like to install to?
**And give the options of:**
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda8
/dev/sda9
And let me decide which partition to format and install to.

Originally I had the 14.04Trusty on the /dev/sda9 partition, in a [COLOR=#b22222]**triple boot**[/COLOR] config and all worked really well until I opted for the 14.10 upgrade (what a mistake)! That installation failed/broke!!!
Ubuntu 14.10 would not shutdown/restart nomally.... It would hang in the shutdown process and I had to do a hard shutdown/restart to reach the OS boot menu (I think that's called a GRUB???).
"Win XPPro" and "Linux Mint 17.1" will sutdown/restart to the OS boot menu normally.... Only Ubuntu 14.10 on the /dev/sda9 partition, gives problems.
Next I installed Ubuntu 15.04, after going into Windows and deleting the /dev/sda9 partition, which created an "unallocated space" of ~20GB.
I was then able to do the Ubuntu 15.04 install to the unallocated space, but something is wrong with that install too (can't make installs from the "Software Mgr"... justs hangs).

**Bottom line here:**
I just want to go back to Ubuntu 14.04LTS on the /dev/sda9 partition, in a [COLOR=#b22222]**triple boot**[/COLOR] system, and be done with it... **Lesson learned!!!**

---

### Post by grahammechanical on 2015-05-03
> Appears to be no option to install to a specified partition, from the "Live" install disk.

Oh, yes there is. It is called Something Else. Click that and the partitioner will run and we can select any partitions we want to install Ubuntu onto.

1) select the sda9 partition and click enter
2) change Use As to Ext4
3) tick to format
4) at Mount Point select /
5) click OK

When back at the partition selection screen confirm that the Grub boot loader is going to be installed where you want it installed. Default is sda and click Install Now and away you go.

You already have a swap partition. The installer will automatically use the existing swap partition.

Regards.

---

### Post by happyytilton on 2015-05-03
Tried the "Something Else" before, but was unsure about the boot loader.
I'll give that a try, the way you said and let you know back as to how it worked.

---

### Post by yancek on 2015-05-03
During the installation you will see an option for "Device for bootloader installation".  If you want Ubuntu in charge of booting all three systems, select /dev/sda.  If you want Mint, then select to install the bootloader to the partition on which you are installing Ubuntu.

---

### Post by happyytilton on 2015-05-05
Just a note to let both of you know that the install was successful.
Did it just the way you said, **grahammechanical**.
And thanks to, **yancek**, for the explanation on the boot loader... I was unsure about how that worked... Now I know!
Will mark this as, **SOLVED**.

---

