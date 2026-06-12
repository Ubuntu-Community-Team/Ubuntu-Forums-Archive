---
title: "Dual boot installation, unallocated space show as unusable."
date: 2016-12-11
forum: Installation &amp; Upgrades
---

### Post by james256 on 2016-12-11
Hello,

I'm trying to dual boot an Ubuntu distribution but when I try do so the unallocated space shows up as unusable by the installer. I have read other posts and the replays say its because you can only have 4 partitions. I feel uncomfortable about messing with the partitions without advise, thank you.

[ATTACH=CONFIG]272653[/ATTACH]

---

### Post by oldos2er on 2016-12-11
Before doing anything else, please backup any sensitive data if you haven't already.

> you can only have 4 partitions If your system is using the older MBR, that is true. Can you please tell us the make/model of computer, and other hardware specs?

You would need to use the "Something else" option to install to your unallocated area of the hard disk.

---

### Post by james256 on 2016-12-12
Thanks for the reply. My data is backed up, I also made a disk image from when I got the machine. 

I am using MBR. The laptop is a dell XPS 13 9333 I'm not sure what hardware specs are relevant but the SSD is liteonit lmt-256l9m-11 msata 256gb. I am using the "something else" option, which is when I can't select the unallocated area because it says its unusable.

---

### Post by yancek on 2016-12-12
If this is an MBR system then you are limited to 4 partitions which you  already have.  The unallocated space will be useless until you remove  one of the current partitions.  The one labelled "C:" is your system partition so you need to keep that.  One of the others may be a boot partition which you would also need but it's not possible to tell from the image you posted which it might be.  I'm not sure if the image you posted shows these partitions in any order as the top window shows different than the bottom as far as order?

You could boot the Ubuntu media and open a terminal and run:  sudo fdisk -l and post the output (Lower Case Letter L in the command)

---

### Post by oldfred on 2016-12-12
Standard Windows 7 BIOS/MBR installs across all vendors seemed to use two partitions for Windows, a 100MB boot and the main or c: "drive" and then a vendor recovery and a vendor tools.
Some vendors may allow you to download tools or a few even the recovery. But best to separately create the recovery backup. My newer UEFI based Dell wanted both a Windows backup and a Dell backup and even offered then to delete the Dell recovery partition after running the backup.

That standard configuration then uses all 4 primary partitions that MBR allows. So you have to convert one primary to the Extended which works as the container for as many logical partitions as you want.

You can either do a backup of the vendor recovery or tools partition and delete it, or use fixparts to convert a primary to logical and then shrink Windows main partition and expand extended to include unallocated. The unallocated must be next to extended to be able to expand it.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by james256 on 2016-12-13
Thanks for your help, everything is done and working now.

---

