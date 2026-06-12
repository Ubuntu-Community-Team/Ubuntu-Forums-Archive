---
title: "Confused by partitions - dual boot Windows 8 and Ubuntu 12.10"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by punk4rock on 2013-01-11
I'm trying to install Ubuntu 12.10 alongside Windows 8.

I get to the partition part of the installation and there are about 7 partitions already there! 

I've attached a screenshot from my phone.

Where do I put my Ubuntu install? There are like 3 NTFS partitions...

Many thanks for your help :)

---

### Post by oldfred on 2013-01-11
You need to use Windows MMC to shrink your main Windows install to make room for Linux. Ubuntu cannot use Windows partitions for any system partitions. With gpt you do not have to worry about primary partitions as they all are the same with gpt partitioning.
Reboot Windows after shrink to let it update itself and run chkdsk.

In UEFI/BIOS be sure to turn off secure boot & fast boot.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vitial for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work, but Boot-Repair can create a correct entry:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Ubuntu's default install is / (root) and swap. You may want additional partitions for /home and/or a NTFS data partition. If you put most data in a shared data partition you probably do not need the separate /home.

---

### Post by darkod on 2013-01-11
You don't have any free space (unallocated) on the disk. You need unallocated space to create the linux partitions in it. How you create it is your choice. If shrinking the win8 partition it's best to use windows Disk Manageent and reboot few times after it's done.

Also make sure you read about win8 and 12.10 dual boot first, there are some issues and procedures to follow.

For example this is similar thread where oldfred posted useful links:
[http://ubuntuforums.org/showthread.php?t=2103908](http://ubuntuforums.org/showthread.php?t=2103908)

---

### Post by punk4rock on 2013-01-11
EDIT: I partitioned the drive and installed Ubuntu 12.10 but.... now GRUB2 won't load... when I restart it skips to a purple screen and loads straight into 12.10 (with absolutely no option to boot into Windows 8)

I followed the UEFI settings so I'm not too sure what's causing this.

---

### Post by oldfred on 2013-01-11
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by punk4rock on 2013-01-12
> **oldfred said:**
> Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

This is the link: [URL="http://paste.ubuntu.com/1523232/"]http://paste.ubuntu.com/1523232/
[/URL] 
Thanks :)

---

### Post by oldfred on 2013-01-12
Grub2's os-prober has a bug that it does no create a correct chain load entry. But you do not even have the incorrect one's? When only one system is detected, it will not show the grub menu. Perhaps they have started to fix the issue but only stopped the incorrect entries?

Boot-Repair should still add the correct chain entries or you can manually add them. Bug report has examples of manual entries or we can help you if you do not use Boot-Repair.

Boot-Repair has  options to add the Boot-Retries. Also some UEFI only Boot Windows and Boot repair renames & backs up some of the files to make it work. Probably best for you to back up the entire efi partition first.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by punk4rock on 2013-01-12
Thanks for your reply.

Sorry if I'm being dense; are you suggesting I use boot repair (recommended repair)?

---

### Post by oldfred on 2013-01-12
Yes, It will find the Windows efi entry and add a Windows efi chain load boot stanza to 25_custom. Then you should be able to boot either Windows or Ubuntu.

---

### Post by punk4rock on 2013-01-13
> **oldfred said:**
> Yes, It will find the Windows efi entry and add a Windows efi chain load boot stanza to 25_custom. Then you should be able to boot either Windows or Ubuntu.
 
Worked like a charm! Thank you so much oldfred :D
 
Typing this on Windows 8 :)

---

### Post by oldfred on 2013-01-13
What!? Windows 8. This is a Ubuntu forum. 

Glad you got it working. :)

---

