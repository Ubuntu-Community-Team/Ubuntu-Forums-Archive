---
title: "Can not run grub gnu after ubuntu 15.10 installed im Windows 10"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by marcel21 on 2016-02-28
Good day.After installing Linux Ubuntu 15.10 dual with Windows 10 for the first time (after turn off PC from Ubuntu), I becomed classic Grub GNU page, where is it possible to choose operating system. Then I choose Windows boot manager. After restart, I does not become grub GNU, Windows 10 is starting. I used boot-repair in live ubuntu with this message:[http://paste.ubuntu.com/15236697](http://paste.ubuntu.com/15236697). I tried to turn off fast turn off iin Windows.Nothing help.Please help me with this, thank you.

---

### Post by ubfan1 on 2016-02-28
From the report, line 1296, looks like there was a filesystem problem, and the grub bootloaders got removed in the repair.  Your boot order will try to boot Ubuntu before windows, but fails since no bootloaders are found.  Reinstall grub-efi-amd should fix the problem, but not sure what caused it.  There should be lots of other threads about reinstalling grub, just make sure it's the UEFI instructions you are following, not the legacy grub.

---

### Post by marcel21 on 2016-02-28
Hello, I reinstalled grub-efi-amd , doesnt help. I followed this instructions:

[http://superuser.com/a/376471](http://superuser.com/a/376471)

It is better to reinstall Ubuntu?

---

### Post by ubfan1 on 2016-02-28
A reinstall would be the simplest thing, but maybe first rerun the boot-repair report to see if the Ubuntu bootloaders got put into /EFI/ubuntu on the sda1 EFI partition.  If they are not there, go for the reinstall.

---

### Post by marcel21 on 2016-02-29
Here is report from boot-repair after reinstall grub-efi-amd:

[http://paste.ubuntu.com/15241120/](http://paste.ubuntu.com/15241120/)

Thank you for help.

---

### Post by marcel21 on 2016-02-29
I see some problems in boot-repair report, but I dont now how to fix it. Help me.

---

### Post by westie457 on 2016-02-29
Hi somehow the 'efi boot' partition has got corrupted and now has the 'dirtybit' set. In this case Windows tool should be used.

First boot into Windows and try this. [http://superuser.com/questions/518634/running-chkdsk-on-a-disk-partition-without-a-drive-letter](http://superuser.com/questions/518634/running-chkdsk-on-a-disk-partition-without-a-drive-letter)

Try re-installing Grub, if it still fails try this. [http://www.pcreview.co.uk/threads/dirty-bit-chkdsk.3170077/](http://www.pcreview.co.uk/threads/dirty-bit-chkdsk.3170077/) adapting the commands to point to the efi-partition.

Again try re-installing Grub.

If after running the above it still fails post another boot-report please.

---

### Post by marcel21 on 2016-02-29
> **westie457 said:**
> Hi somehow the 'efi boot' partition has got corrupted and now has the 'dirtybit' set. In this case Windows tool should be used.First boot into Windows and try this. [http://superuser.com/questions/518634/running-chkdsk-on-a-disk-partition-without-a-drive-letter](http://superuser.com/questions/518634/running-chkdsk-on-a-disk-partition-without-a-drive-letter)Try re-installing Grub, if it still fails try this. [http://www.pcreview.co.uk/threads/dirty-bit-chkdsk.3170077/](http://www.pcreview.co.uk/threads/dirty-bit-chkdsk.3170077/) adapting the commands to point to the efi-partition.Again try re-installing Grub.If after running the above it still fails post another boot-report please.Thank you, but I dont now which post in stack overflow is right to use. Is it CHCKDISK?

---

### Post by marcel21 on 2016-02-29
I can not run Assign on partition: its not possible to select volume. Also in Disk manager, there are not actions on Linux partition. Hm, very confused.

---

### Post by marcel21 on 2016-02-29
Also I can only update-grub without errors on my sda [http://askubuntu.com/a/88432](http://askubuntu.com/a/88432). I can not run grub-install (Could not find EFI ... error). I also get error grub-install: failed to get cannonical path of '/cow'. I think, there is couple of problems here.

---

### Post by marcel21 on 2016-02-29
Hello guys, my new paste-bin:

[http://paste.ubuntu.com/15243961/](http://paste.ubuntu.com/15243961/)

Is it ok?

I updated grub, and then run boot-repair with advanced options, with repair efi files option.

My linux partition and grub are running.

---

### Post by ubfan1 on 2016-02-29
I see a problem with the EFI partition.  The original EFI partition was sda1, and it only contained the Microsoft bootloaders, but now it is totally empty, but it still has the "boot" flag (problem 1).  Ubuntu installed its bootloaders into sda7, which also had the Microsoft bootloaders (a backup?), and that's apparently what's used to boot Ubuntu.  However, Ubuntu's /etc/fstab mount of the EFI partition still uses the UUID of the sda1 (problem 2).    If you can fix the filesystem on sda1, you should be able to just copy everything from sda7 to sda1 and be OK.  Might take repeated runs of chkdsk to fix the problems in sda1.  OR, change the boot flag to sda7 (remove it from sda1) and edit the fstab file for the UUID on the EFI mount.  But there may be other places with sda1 wired in, so better try the copy sda7 to sda1 first.

---

### Post by oldfred on 2016-02-29
The /cow error is from trying to install to live installer, which is not writeable.
This is the issue.
> Locked-ESP detected.

Usually chkdsk from Windows or fsck from Ubuntu can clear dirty bit.
       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)
Or which I think is really same program as dosfsck:

 sudo fsck.vfat -t -a /dev/sda1

If either Windows nor fsck works, then the brute force fix, is to fully backup the ESP - efi system partition. Not large, but you need all of the Windows files.
Then use gparted to delete sda1, create new sda1, FAT32 formatted with boot flag. Restore backup data and confirm Windows still boots. 
Then grub UEFI install should work.

---

### Post by marcel21 on 2016-03-01
Firstly, I have question. In gnu grub manager, Windows boot manager is on /dev/sda1. However, Windows starts correctly in Windows Boot UEFI loader, not in Windows boot manager. Windows boot manager returns only refresh the GRUB. I think its ok. Is it ok? And Ubuntu works fine, grub is starting, for me ok.
I wait for next instructions, or I will use previous instructions?

---

### Post by omar37 on 2016-03-01
hi, ubuntu 14.04 is the best ,very stable and long term support (2019),i had 15.10 installed before and.......lot of problems, sorry for my bad english.
good luck

---

### Post by oldfred on 2016-03-01
Re-read ubfan1's post. You really should not have efi boot files in two partitions. 
But some vendors put their recovery boot files in a separate FAT32 partition that does not have boot flag. Somehow they also are able to boot from it.

But both Windows UEFI boot (not recovery boot) and Ubuntu UEFI boot files should all be in one FAT32 formatted partition with boot flag. And it looks like your ESP - efi system partition is sda1.
You need to verify all files are in sda1.

---

### Post by marcel21 on 2016-03-02
> **oldfred said:**
> Re-read ubfan1's post. You really should not have efi boot files in two partitions. 
But some vendors put their recovery boot files in a separate FAT32 partition that does not have boot flag. Somehow they also are able to boot from it.

But both Windows UEFI boot (not recovery boot) and Ubuntu UEFI boot files should all be in one FAT32 formatted partition with boot flag. And it looks like your ESP - efi system partition is sda1.
You need to verify all files are in sda1.

In /dev/sda7 I have: Boot, bootmgr, EFI, OneKey, Version.txt
In /dev/sda1 I have: BOOT, BOOTSECT.BAK, EFI, FSCK0000.REC, FSCK0001.REC, FSCK0002.REC, FSCK0003.REC

What would be next step? Copy from sda7 to sda1?

---

### Post by oldfred on 2016-03-02
The fsck files are from NTFS' file check program and said you had issues with that partition.
Boot and EFI should be folders with files in them.

The recovery partition boot files may have same bootmgr, but BCD would be different. And then it has different files to boot into a vendor recovery or repair type functions (but Not Microsoft Windows recovery).

Have you placed boot flag only on sda1? And see if system boots with files that are there?

---

### Post by marcel21 on 2016-03-03
> **oldfred said:**
> The fsck files are from NTFS' file check program and said you had issues with that partition.
Boot and EFI should be folders with files in them.

The recovery partition boot files may have same bootmgr, but BCD would be different. And then it has different files to boot into a vendor recovery or repair type functions (but Not Microsoft Windows recovery).

Have you placed boot flag only on sda1? And see if system boots with files that are there?

I dont now how to make it, place boot flag only on sda1. Is there any manual/tutorial, or is it simple? 

Thank.

---

### Post by oldfred on 2016-03-03
You can set boot flag with gparted, disks, or command line.
In Windows it is the set active command as Windows calls the boot partition the active partition.

In gparted right click on a partition:
[http://www.dedoimedo.com/computers/gparted.html#mozTocId143113](http://www.dedoimedo.com/computers/gparted.html#mozTocId143113)

---

### Post by marcel21 on 2016-03-22
> **oldfred said:**
> You can set boot flag with gparted, disks, or command line.
In Windows it is the set active command as Windows calls the boot partition the active partition.

In gparted right click on a partition:
[http://www.dedoimedo.com/computers/gparted.html#mozTocId143113](http://www.dedoimedo.com/computers/gparted.html#mozTocId143113)

Hello 

here is picture from gparted:

[ATTACH=CONFIG]267928[/ATTACH]

I dont have boot flag on dev/sda7 (its hidden), but on dev/sda1 it is. Windows 10 is not booting from dev/sda1.

For now, I must copy everything from dev/sda7 to dev/sda1 ???? And after I must remove dev/sda7 ????

Thank you for next answers.

---

### Post by ubfan1 on 2016-03-22
Yes, just copy everything in sda7 to sda1, keeping the directory structure.  But there still seems to be a problem, I don't see the /EFI/Boot/grubx64.efi  or the /EFI/ubuntu/grubx64.efi in the report for sda7.  Maybe the report is old and they got added after it was made.  The shimx64.efi still requires that grubx64.efi be in the same directory as far as I know, so I don't know how you have been running grub.  No need to delete the sda7 after the copy, it is the backup copy, just in case something happens to the primary sda1.

---

