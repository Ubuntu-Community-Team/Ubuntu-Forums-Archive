---
title: "Partitions Not Recognized?"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by saw7988 on 2008-09-17
Hello,

Currently on my laptop I have Windows XP and Ubuntu 6.06 (not sure but I know it's in the 6's) installed on my laptop in separate partitions. I forget how much space I gave to each, but Windows has something like 80-95% of the hard drive.

Anyway, I tried installing Ubuntu 7.04 off of a live CD, but when I get to the partitioning stage it just shows "dev/sda" without any partitions, and the only option I have is to create a new partition table which will erase everything. I also tried using GParter, but it just shows 1 partition "unallocated" of 93 Gb and says I need to create a disklabel to do anything, which will erase the HD.

A friend told me it might be some compatibility problem because it's an old version or something, so I tried downloading and installing 8.04, but I get the exact same results.

I would think it would at least show the Windows partition because it's working fine and I'm posting this message right now in Windows.

Help would be greatly appreciated. Thanks in advance.

---

### Post by Pumalite on 2008-09-17
Try editing your boot line (of the Live CD) and add all_generic_ide at the end.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by saw7988 on 2008-09-17
Hey Pumalite thanks for the response. However, I don't quite understand what you mean. Where is this line that I add "all_generic_ide" to the end of?

---

### Post by Sef on 2008-09-17
> Hey Pumalite thanks for the response. However, I don't quite understand what you mean. Where is this line that I add "all_generic_ide" to the end of?


Have you read the page in the link provided?  If you have and don't understand it, please let us know where you start having problems understanding.

---

### Post by saw7988 on 2008-09-17
I'm not sure what they mean by intercepting the GRUB countdown to get to the menu. I never see a 3 second countdown between the time my computer boots to the time the Ubuntu CD loads. However I tried pressing escape at the main menu (the menu that has try out ubuntu/install ubuntu/etc) and it takes me to some command line mode that has a prompt saying "boot:" asking me to enter a kernel name I believe. I also found a string of options that is editable from pressing F6 at the main menu. Are either of these what that article is talking about?

---

### Post by james2b on 2008-09-18
To fix this try this tool; [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) ,which can be run from XP or a from a CD like such as this handy rescueCD; [http://www.osdisc.com/cgi-bin/view.cgi/products/linux/systemrescuecd](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/systemrescuecd)

---

### Post by saw7988 on 2008-09-18
Hi,

I tried out that TestDisk utility. It does recognize that I have partitions but there is a warning, which might be the cause of my problems...??

Here's the output I get from asking it to analyze my partition structure:


TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 100 GB / 93 GiB - CHS 12921 240 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 11295 239 63  170795457 [IBM_PRELOAD]
 2 P Linux Swap           11295 105  1 11430  89 63    2040255

Warning: Bad starting head (CHS and LBA don't match)
 3 P Linux                11430  90  1 12921  14 63   22539195

Warning: Bad starting head (CHS and LBA don't match)
Space conflict between the following two partitions
 1 * HPFS - NTFS              0   1  1 11295 239 63  170795457 [IBM_PRELOAD]
 2 P Linux Swap           11295 105  1 11430  89 63    2040255




*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition



Any suggestions??? I really need to get this working. Thanks for all your help.

---

