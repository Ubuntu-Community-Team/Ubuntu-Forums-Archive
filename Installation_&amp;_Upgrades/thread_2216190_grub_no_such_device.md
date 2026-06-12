---
title: "grub no such device"
date: 2014-04-10
forum: Installation &amp; Upgrades
---

### Post by chrisacurry on 2014-04-10
Have a Ubuntu / Win7 dual boot that's been working for quite some time.

After a random period of time, the system will shut down.  This appears to (also randomly, since most of the time it reboots) screw up the boot information.  Previously, I've reinstalled both os's (twice now), but this time I'd like to see if I can repair the actual installations so I don't have to do the full process again.

Error I'm receiving upon boot-up:

error: no such device: a944d046-e35d-4438-8caf-90834a2c6b25
grub rescue> _

I've lurked several other people's problems with the same error request-for-help thread and tried several things.  None of them has worked.  The last thing I tried was using Boot-Repair.  Here's the pastebin link with my drive information:

[http://paste.ubuntu.com/7231463/](http://paste.ubuntu.com/7231463/)

When responding, please keep in mind that I'm a software engineer, but a total noob when it comes to linux boot information.  I can run commands and provide reasonable output, but I've got exactly NO experience fixing MBRs.

Thanks for your time!

---

### Post by Luke M on 2014-04-10
You have grub installed on two drives, so maybe your BIOS boot order got changed somehow and you're booting from a different drive now.

---

### Post by oldfred on 2014-04-10
Abnormal shutdown can cause file corruption whether Windows or Linux.
If Windows then you may need to run chkdsk and on ext formatted partitions run fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

It does look like your BIOS promoted flash drive to sda which often can cause install or other issues. Best to double check which drive is sda and which is sdb every time you reboot.
sudo fdisk -lu

It also looks like you have a newer system as it says you booted Boot-Repair in UEFI mode, but both installs are in BIOS mode. Best to always work in BIOS mode.
Your drive sdc1 is not showing boot files? Is it hibernated or needing chkdsk, as then Linux will not mount it. But Boot-Repair usually mentions that NTFS file system is unsave (or hibernated).

I also do not like that Boot-Repairs auto fix with multiple drives will install grub2's boot loader to every MBR. You want to keep grub only on Linux hard drive's MBR and have Windows boot loader on Windows drive when each system is on a separate hard drive. You can use Boot-Repair's advanced mode to manually choose an operating system and install its boot loader to that drive. But if it does not see Windows boot files it will not work.

I have not seen the issue with newer systems that are UEFI capabile, but some older systems had BIOS and hard drive in IDE mode and very large / (root) systems have issues where some files near beginning of drive and others near end of drive cause issues. See line 387 where some files are far into drive.
Often better to have a smaller / and separate /home or data partition(s). I like 20 or 25GB for /.

---

### Post by chrisacurry on 2014-04-10
> **Luke M said:**
> You have grub installed on two drives, so maybe your BIOS boot order got changed somehow and you're booting from a different drive now.

Un-doubtably this is the result of my trying to fix it via boot-repair.  I ran a grub-install fix and installed grub to /dev/sdb1.

I went through the pastebin info to try to see where you saw the dual grub installs and re-installed on /dev/sdc.

Rebooted.

It passed the previous error (indicating that, yes, /dev/sdc was my original boot partition and what was screwed up), but then errored out when trying to find something else.

I assume that something went wrong with even the reinstallation of grub.  I'm going to just trash it all and start over.  Will do the typical windows install -> ubuntu install.

Thanks for trying.  I'll try to track down the intermittent crash that's causing the boot problems and get it fixed before it becomes a problem again.

Thanks.

---

### Post by Luke M on 2014-04-10
I still think you're probably booting from the wrong drive. What happens when you boot from the drive with ubuntu on it (sdb)?

---

