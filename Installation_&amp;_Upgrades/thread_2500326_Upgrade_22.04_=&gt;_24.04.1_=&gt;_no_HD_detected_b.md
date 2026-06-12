---
title: "Upgrade 22.04 =&gt; 24.04.1 =&gt; no HD detected by BIOS"
date: 2024-08-30
forum: Installation &amp; Upgrades
---

### Post by lendern on 2024-08-30
Hello everyone
I'm using Ubuntu on my personal computer for many years, and didn't have any noticeable issue yet
This morning, I run the upgrader to 24.04.1. Everything, went fine. I finally had the invite to reboot computer => "good, let s see what's new'

And then, the bad: my computer doesn't detect any more the harddrive, so no boot. There is no the "usual" message "no boot device" or something like that => nothing, computer opens the BIOS settings. Weird

I run a bootable USB: SSD is detected and everything is there (/home, /var/mydatas/...) :) 

This is a SSD, running Ubuntu only

Here is the gparted overview (in attachment)

I would appreciate any help to repair the boot. And also, understand what wen wrong

Here is the boot-info report: [https://paste.ubuntu.com/p/SKcXqc3n2h/](https://paste.ubuntu.com/p/SKcXqc3n2h/)

Len

---

### Post by tea for one on 2024-08-30
> **lendern said:**
> And then, the bad: my computer doesn't detect any more the harddrive, so no boot. There is no the "usual" message "no boot device" or something like that => nothing, computer opens the BIOS settings. Weird
Yes, unusual behaviour.

Line 137 - sdb
Line 143 - sdd
The report does not show any details of these disks.
Is the PC trying to boot one of these as priority?
Perhaps, power off, remove them and boot again?

---

### Post by lendern on 2024-08-30
sda is the main SSD, where Ubuntu 24.04.1 is install
sdc is the bootable USB key, used to diagnose
there is no sdb

---

### Post by oldfred on 2024-08-30
In partition table your gparted shows red ! point on ESP, sda2.
If in gparted, you click (right click?) on red icon what does it show.
That is often a corrupted file and dosfsck may fix it.

man dosfsck
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sdXY # where X is drive and Y is partition.

---

### Post by lendern on 2024-08-30
Here is the content of Red!:

[I]Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for fat32 file system support:  dosfstools, mtools.[/I]

---

### Post by tea for one on 2024-08-30
The message is probably because the EFI partition is unmounted during your live session.
If you mount the partition, the warning will not be shown.
If it's still unmounted, then it's worthwhile to check the file system (as mentioned by oldfred)

Secondly, as your UEFI settings cannot see your disk, perhaps try:-
Reset to default
Then disable Secure Boot, TPM and other security options

---

### Post by lendern on 2024-08-30
Problem is fixed: I have run boot-repair => it solved the issue

BTW, it definitely sounds like a critical bug of upgrade procedure between LTS version :/

---

