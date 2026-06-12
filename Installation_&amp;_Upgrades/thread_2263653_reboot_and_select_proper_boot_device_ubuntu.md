---
title: "reboot and select proper boot device ubuntu"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by vlad19 on 2015-02-02
ubuntu 14.04




   Hello.
 I took the advice on this topic [http://ubuntuforums.org/showthread.php?t=1821980&p=11136267#post11136267](http://ubuntuforums.org/showthread.php?t=1821980&p=11136267#post11136267) and here is my link to the problem [http://paste.ubuntu.com/10015850/](http://paste.ubuntu.com/10015850/)
 I hope for your help.

---

### Post by ajgreeny on 2015-02-02
The next to final paragraph of your boot-info results says it all:-
> =================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag). Do you want to continue? 

You will need to either start again from scratch and make sure you add a small partition of 100 - 200MB formatted to fat32 and given the boot flag but no mountpoint, so I wonder if you were confused when making the partitions and did not properly allocate the small fat32 partition when you installed.
An EFI partition can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is OK), and must have the following attributes: 

[LIST]
[*]*Mount point:*  /boot/efi  (remark: no need to set this mount point when using the  manual partitioning, the Ubuntu installer will detect it automatically) 

[*]*Size:* minimum 100Mib. 200MiB recommended. 

[*]*Type:* FAT32 

[*]*Other:* needs a "boot" flag. 

[/LIST]



You appear to have Windows Vista installed and I think that will not boot with a UEFI system at all, and only on a GPT partition table, which you have, if it is 64bit.  It certainly was not found by grub.  Is your vista 64bit?

You may need to start again and carefully read through the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") first which gives all the details of how to best deal with your system, the partitions needed, how to turn off secure boot, and many other things related to UEFI and GPT.

---

