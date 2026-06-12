---
title: "installing grub2 with lvm"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by p.elsie2 on 2018-11-06
After replacing a bad hard drive, upgrading, and some other changes, I'd like to go back to booting to LVM partitions. 

With the install CD, at some point, I got grub installed on sda, with a root partition on gpt5 that I'd eventually like to get rid of. 

On sdb, there's grub2 from before, and it has the lvm module, and it's looking for an LVMID that no longer exists. 

I'd like to make sda look like sdb, but with the right LVMID. This is what boot-info prints at the top:

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    132729680 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt5)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for 
    (lvmid/ATq80J-CW3s-Hora-y3KC-rCB5-Ao4j-XcY3n2/chtzmM-5LPO-9BrS-tlqY-GU6s-xQ
    d2-rFlt5O)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt diskfilter lvm biosdisk
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdc.

I've spent a lot of time trying to make sense of the grub tools - but it seems like the install CD just magically does things that the scripts don't and I find that frustrating. In my latest attempt to fix this, I did a chroot into my LVM root and ran this:

# grub-install /dev/sda --modules 'fshelp ext2 part_gpt diskfilter lvm biosdisk'
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: error: embedding is not possible, but this is required for RAID and LVM install.

...and then to learn more, I tried this:

# grub-install /dev/sdb --modules 'fshelp ext2 part_gpt diskfilter lvm biosdisk'
Installing for i386-pc platform.
Installation finished. No error reported.

After that, boot-info shows that it did update grub on sdb, and I guess maybe I can just configure the BIOS to boot that disk first. But what should I do if I really need sda (and sdc) to look the same as sdb?

---

### Post by oldfred on 2018-11-06
If using gpt with BIOS boot you need to have a tiny 1 or 2MB unformatted partition with the bios_grub flag (if using parted tools).
If using gdisk code is ef02 for the grub required partition.
It can be anywhere withing first 2TB of the drive, but normally should be one of the first partitions. LVM will use most of drive.

---

### Post by p.elsie2 on 2018-11-10
Thanks, but I want to install to MBR on /dev/sda, just like the Ubuntu install disk did to /dev/sdb. All my disks are GPT partitioned and none of them have any tiny unformatted partitions. 

My question are:

1) why won't grub-install install the lvm module to sda like the install CD did to sdb?
2) how is the installer CD doing it?
3) when installing grub, how does it decide which partition it will look to for /boot/grub? Does it look in /etc/fstab of my chroot? Can I override it?

I think my questions are academic at this point, because at this point, I might just copy the MBR from /dev/sdb to /dev/sda using dd. But it seems like someone should know the answers and that it might be helpful to have them documented somewhere.

---

### Post by oldfred on 2018-11-10
Have never installed with LVM, and it was years ago I did a server install, just to see the difference with Ubiquity and non-gui install.
Now they have a gui Subiquity installer.

Generally with desktop on the partitioning screen you choose drive to install grub2's boot loader. 
But if just using defaults desktop normally defaults to sda or first drive if newer NVMe drive(s).

---

