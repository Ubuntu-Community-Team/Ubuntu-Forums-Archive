---
title: "Warning in gparted for efi system partition"
date: 2023-11-26
forum: Installation &amp; Upgrades
---

### Post by duncanbayliss on 2023-11-26
Hi all,

It seems I've crooked the EFI boot loader after a premature shutdown of fdisk. I am now unable to boot Kubuntu past emergency mode.To attempt recovery I restored a recent default backup of system files with Timeshift.

I've tried boot repair twice. Both instances failed, but for apparently different reasons. Firstly couldn't find grub, then nvram locked. 
This is the result of the 2nd attempt.

[https://paste.ubuntu.com/p/bxSXkqwXCT/](https://paste.ubuntu.com/p/bxSXkqwXCT/)

Also there is a warning in gparted for the efi system partition.

[I]"Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for fat32 file system support: dosfstools, mtools."

[/I]Is there any hope or have I completely messed up? I would really appreciate any help
 
Thanks Duncan

---

### Post by yancek on 2023-11-27
There are a number of recent threads here at the forums regarding the error "nvram is locked" and no single solution at the problem seems to vary by vendor. Have you tried a filesystem check with fsck on the Kubuntu partition from a live usb?

How do you get the gparted error you mention?  Are you using a 'live' Linux usb with gparted on it or the gparted iso?  If you have a 'live' Ubuntu/Kubuntu usb, you can install the referenced dos tools and use them, just don't reboot.

---

### Post by duncanbayliss on 2023-11-27
I ran fsck on my Kubuntu partition nvme0n1p2 from a live usb. All good

```
ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p2
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p2: clean, 651889/30498816 files, 17507065/121965056 blocks
```

I then ran it on efi boot partition nvme0n1p1

```
ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p1
fsck from util-linux 2.37.2
fsck.fat 4.2 (2021-01-31)
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
```
 
 And so did
 
```
ubuntu@ubuntu:~$ sudo fsck -a /dev/nvme0n1p1
fsck from util-linux 2.37.2
fsck.fat 4.2 (2021-01-31)
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.

*** Filesystem was changed ***
Writing changes.
/dev/nvme0n1p1: 12 files, 2590/130811 clusters
```

 Yes I'm using a live ubuntu usb 22.04 at the moment I can though get to a maintenance or grub prompt on  my install. If I install the dos tools and don't reboot. How will I know if it helps? 
 
 Thanks Duncan

---

### Post by tea for one on 2023-11-28
> **duncanbayliss said:**
> 
Also there is a warning in gparted for the efi system partition.
Unable to read the contents of this file system
Now that you have fixed the "dirty bit" on the ESP, I would leave the live session and see if Kubuntu boots?

Corruption in the ESP can sometimes interfere with the boot process.
While you were in the live session, did you backup your personal data?

---

