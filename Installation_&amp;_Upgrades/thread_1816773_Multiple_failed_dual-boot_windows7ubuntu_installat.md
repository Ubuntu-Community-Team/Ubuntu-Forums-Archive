---
title: "Multiple failed dual-boot windows7/ubuntu installationsons"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by zhz on 2011-08-02
Hi,I had a Windows 7  installation and I decided to install ubuntu 11.04
I tried several times but every time soon or later something with grub goes wrong.Most times I get the error "no such partition",once it just halted after "verifying DMI ... " .I fixed windows mbr with 
"bootsect /nt60 C:" and then tried to reinstall grub with boot-repair .It showed no errors but after reboot I get "no such partition" again.
My scheme is something like :
/dev/sda1 -> the windows 7 system partition NTFS
/dev/sda2 -> partition for windows programs etc NTFS
/dev/sda3 -> partition for files(images/music/videos) NTFS
/dev/sda4 -> extended partition
          /dev/sda5 -> / (root directory) ext4
          /dev/sda6 -> /home              ext4
          /dev/sda7 -> swap                 
          /dev/sda8 -> /boot              ext4

And I chose /dev/sda8 for device for installation of boot loader.

---

### Post by MAFoElffen on 2011-08-02
> **zhz said:**
> Hi,I had a Windows 7  installation and I decided to install ubuntu 11.04
I tried several times but every time soon or later something with grub goes wrong.Most times I get the error "no such partition",once it just halted after "verifying DMI ... " .I fixed windows mbr with 
"bootsect /nt60 C:" and then tried to reinstall grub with boot-repair .It showed no errors but after reboot I get "no such partition" again.
My scheme is something like :
/dev/sda1 -> the windows 7 system partition NTFS
/dev/sda2 -> partition for windows programs etc NTFS
/dev/sda3 -> partition for files(images/music/videos) NTFS
/dev/sda4 -> extended partition
          /dev/sda5 -> / (root directory) ext4
          /dev/sda6 -> /home              ext4
          /dev/sda7 -> swap                 
          /dev/sda8 -> /boot              ext4

And I chose /dev/sda8 for device for installation of boot loader.
Just passing through, but saw this and had to comment.  Whats blaring out at my is the "number" of partitiions...

Correct me if I'm wrong, but:
Rule of thumb- Limit of 4 logical partitions, additional can be set as extended partitions. I think (initially) I see 8 partitions with 2 of them as extended?  

What is going to "help people help you" here is to run and post the output from the Boot Info Script in my Sig Line...

---

### Post by oldfred on 2011-08-02
Having a separate /boot on standard desktop complicates things. It is better just to have /, /home & swap. Often instructions on fixing grub2's boot loader in the MBR leave off the extra command to mount /boot or just add it as a footnote. Some tools may not work with that extra partition also.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

---

### Post by Blasphemist on 2011-08-02
I also never use a boot partition so I'd delete that. I don't use a /home partition but there is nothing wrong with that. Pending seeing more from boot info script results, I'd delete the boot partition, put the swap at the end of the disk and choose during the installation to do the partitioning manually. That is the "something else" option on the disk allocation screen in the install.

Grub should install do sda and not a partition. That will put it in the mbr. There are other distros that commonly use a boot partition but that is quite uncommon in the ubuntu universe.

---

