---
title: "Volume Label"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by Ronco Pizatto on 2014-09-23
I previously entered the following statements to define my partitions and give then volume labels.

/dev/sda1: UUID="01CFC2409A87A4B0" TYPE="ntfs" 
/dev/sda5: LABEL="DATA02" UUID="312D-1112" TYPE="vfat" 
/dev/sda6: LABEL="Ubuntu" UUID="7e574ea5-bdb4-4d68-b35d-db639ec10e94" TYPE="ext4" 
/dev/sda7: UUID="e447aaed-0850-47e6-9ffd-5f8f1917d74a" TYPE="swap" 
/dev/sda8: LABEL="DATA01" UUID="9BBA-A670" TYPE="vfat" 

All worked well but I forgot where I put them.
I would like to edit these staements to change my volume labels for my data partitions.

I looked at fstab but not there. Is there a config file that uses such statements?

Thanks.

---

### Post by oldfred on 2014-09-23
I try to remember to create labels with gparted when I create a new partition.

It used to be pretty obvious with Disk Utility where label is and was easy to find. 
With new Disks it is buried away.
Underneath the Volumes are several little icons. The double star/gear is more actions and you can edit label there.

Note with gpt there now are two labels. One is formatted label like in MBR and the other with gpt is an internal gpt partition label.

---

### Post by Ronco Pizatto on 2014-09-23
I tried Disk Utility and gparted but my volumes do not show up the same as in nautilus. I don't understand this since everything is functioning fine.

This is a minor problem but I am trying to learn more about volume labels and partitions.

---

### Post by tgalati4 on 2014-09-23
What label programs are on your system?

> tgalati4@Mint14-Extensa ~ $ apropos label
dosfslabel (8)       - set or get MS-DOS filesystem label
e2label (8)          - Change the label on an ext2/ext3/ext4 filesystem
findfs (8)           - find a filesystem by label or UUID
ip-addrlabel (8)     - protocol address label management
mlabel (1)           - make an MSDOS volume label
ntfslabel (8)        - display/change the label on an ntfs file system
ppmlabel (1)         - add text to a portable pixmap
swaplabel (8)        - print or change the label or UUID of a swap area


```
man dosfslabel
```

Each type of file system has its own label maker.

*tune2fs* can also make labels according to this link:  [http://www.tldp.org/HOWTO/Partition/labels.html](http://www.tldp.org/HOWTO/Partition/labels.html)

The list you provided can be created using *blkid*:

> tgalati4@Mint14-Extensa /dev $ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="A20A-9608" TYPE="vfat" 
/dev/sda2: LABEL="ACER" UUID="A22XX8492AA8XXF3" TYPE="ntfs" 
/dev/sda3: UUID="b9e5433e-791c-4c7a-b08c-XXf6820aXX4f" TYPE="ext4" 
/dev/sda4: UUID="1c9e07eb-1fXX-435f-94be-38f74c0ff1e0" TYPE="swap" 
/dev/mmcblk0p1: UUID="3239-3530" TYPE="vfat" 

---

### Post by Ronco Pizatto on 2014-09-23
I know i have the set of tools with mlabel. I may have some others but I have not edited the volume except when I set the UUID and label with the lines of code shown. I did that after using gparted to adjust volume size. (I had to give Win7 more room for excessive bloating.)

I only recently figured out that vfat has a different label editor than ext2, etc. That is an important point.

---

### Post by nerdtron on 2014-09-23
For me, easiest way to change labels on hard drives is to boot into a Live CD or USB and then unmount all paritions (of the internal hard drive) and open GParted. Now change the Label of the drives as you wish and then hit apply.

---

### Post by Ronco Pizatto on 2014-09-23
Thanks for all the good info. I apologize for making a blunder. I used the statements listed above in fstab to assign volume labels. I just looked too quickly and missed them the first time I checked fstab.

I edited fstab with different volume names and rebooted. The new volume names are now showing.

Thanks for giving me an alternate way to change volume labels.

---

### Post by sammiev on 2014-09-23
I have a bootable gparted usb stick I use to do the job.

---

### Post by Ronco Pizatto on 2014-09-23
Good idea to boot off usb or live cd.

---

