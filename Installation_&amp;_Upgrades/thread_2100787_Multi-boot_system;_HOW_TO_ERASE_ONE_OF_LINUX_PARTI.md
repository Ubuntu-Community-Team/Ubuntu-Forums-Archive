---
title: "Multi-boot system; HOW TO ERASE ONE OF LINUX PARTITIONS"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by LinuxDomi on 2013-01-02
I have provided a screenshot of my partition layout in gparted.

I currently have one NTFS partition, then a extended which constitutes of 3 LINUX partitions - ubuntu, gnomebuntu and mint 14, then a shared FAT32 storage partition and then a swap par.

For some reason the gnomebuntu partition won't boot up. The second screenshot shows the code that comes up when trying to boot into it.

So, is there a way to remedy this or do I have to erase the partition?

If I have to erase the partition, is there a way to do it that doens't screw up grub because a couple of moths ago I erased a Linux partition and my systemn wouldn't boot - it wouldn't even boot into a live CD - the HDD was completely broken - I had to run a small distro that loads into RAM and erase the linux partitions so I wouldn't risk that again.

I also know the MBR overwrite method in windows after which I can erase the Linux par. but then I can't access the other two.

So, can anyone shed light on this? :)

---

### Post by oldfred on 2013-01-02
I might try fsck to see if there is some repairable corruption. Not sure which partition is which so change example with sdb1 to sdaY where Y is your partition number.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

The MBR only has one boot loader. So usually whichever system is installed last is the one in the MBR. And that system will be the one that is first in the grub menu. If you can boot then that is not the one in the MBR.

Just to document system and to be able to make repairs relatively easily, you should have this.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

