---
title: "new installation does'n boot"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by tickbehrouz on 2014-03-03
Hello everyone. I've encountered a problem and I really appreciate your help.
I have a 3TB hdd with a bios based motherboard and I have tried to install ubuntu (and a bunch of other disto's) on it.
My GPT based partitions are as follows:

1. 1 MB free automatically allocated by Gparted.
2. 10MB partition not formatted, with grub-bios flag on.
3.   1GB partition ext2, not used during the installation. I plan to use this partition to install a separate grub to play with!
4.   3GB partition for swap area.
5, 6, 7, 8, 9. each one 500 GB partition ext4 or NTFS for storage area.
10. 100GB partition ext4, for /home directory.
11. 100GB partition ext4 for / directory.
the remaining is unpartitioned.

My problem is that when I install ubuntu (12.4 and 13.10) everything is fine. But after the installation when I reboot and try to boot from this hdd, it says:
error : unknown filesystem.
and grub rescue appears.
I have tried Debian And CentOs too, but they even doesn't make to rescue prompt. They just show a line as "GRUB" and after that not else happens.
Sorry for the lengthy post! and thanks for your help

---

### Post by oldfred on 2014-03-03
Generally better to have / (root) near the beginning of the drive. There was a bug on large drives supposedly fixed but still better with the new very large drives to have / nearer start of drive.

Does BIOS see drive correctly? Some BIOS have issues with very large drives as they did not plan on that. Is drive set in AHCI mode, not IDE?

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

   But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

With grub2 you do not need a separate grub partition like you may have used with grub legacy. But just use the main install's grub to manage all bootable systems.

---

### Post by tickbehrouz on 2014-03-03
thanks for the reply. 
I bug you mentioned is about grub or something else?
I really like to have the data partition on the first sectors because it gives me the ability to change the size of partitions that I am going to install on them. However if I have no other choice I have to do that, but I try to search before doing that.
For now I thinks it's better to give the boot repair tool a try.
thanks.
I will add new updates to the thread.

---

### Post by tickbehrouz on 2014-03-04
it seem the problem is solved but I have not pinpointed the cause!
I installed ubuntu on my usb flash and using the grub-install, installed the grub on my disk.
I don' know why but it works this time!

---

