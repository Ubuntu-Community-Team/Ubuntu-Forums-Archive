---
title: "Cannot boot, UUID does not exist."
date: 2022-07-20
forum: Installation &amp; Upgrades
---

### Post by ds047 on 2022-07-20
Ubuntu does not boot, and I get an error saying the UUID does not exist, but in GParted the UUID of my Ubuntu partition matches it. I used boot repair and it generated the following report. [https://paste.ubuntu.com/p/6CXjnjSfzX](https://paste.ubuntu.com/p/6CXjnjSfzX).

How can I fix this?

Thank you.

---

### Post by deadflowr on 2022-07-20
There is no hard drive showing in the boot-info report.
Only the installer media.

Did the hard drive disconnect somehow?
I'd probably start by checking that a hard drive is still (or even) listed in the UEFI/BIOS settings.

---

### Post by ds047 on 2022-07-20
The hard drive is still listed in the BIOS, as well as GParted. In the Dell BIOS I needed to manually select the boot64.efi file, and I tried to check if it was still there/selected and it is.

---

### Post by oldfred on 2022-07-20
Did fwupdate run an update to UEFI?
That would reset many UEFI settings to defaults.
Check if RAID turned back on, and change to AHCI again.
Also check all the other settings.

My older motherboard did not have any auto updates, so I had to manually update UEFI. But then had 7 settings to redo.

---

### Post by ds047 on 2022-07-20
I am unsure if UEFI was updated, but it seems that most of my settings are not changed, however RAID was turned on and I changed it back to AHCI but it still does not boot. I ran boot repair again and here is the report. It says I have Windows installed in the MBR but I do not, the Kali install is correct. Just before this issue occurred, I was upgrading from 20.04  to 22.04

[https://paste.ubuntu.com/p/Rk8r7B9jgP/](https://paste.ubuntu.com/p/Rk8r7B9jgP/)

Thank you!

---

### Post by oldfred on 2022-07-20
It looks like UEFI Secure Boot was turned on. Turn it off in UEFI settings. 
I do not have Windows and an UEFI update turned "Windows Secure Boot" on in UEFI on my MSI motherboard.

You also have two ESP p1 & p2.
You can only have one ESP per drive. Remove esp,boot flags with gparted from p1. 

The current UEFI entries all are looking for a GUID/partUUID that does not exist. 
You need to totally reinstall grub. Use Boot-Repair's advanced mode and choose Ubuntu & drive.

It looks like you are using an older Boot-Repair.
You should always have a live installer for current version of every system you have installed. 
And good backups to another device/drive. Especially before any major change.

Once you boot, or maybe the reinstall will update grub menu.
sudo update-grub

That will remove the Windows entry as you do not have Windows.

You also have exFAT on p3.
Best not to use Windows formats when you only have Linux. Linux tools only can fix a few minor issues in Windows.
You normally need Windows to fix NTFS or exFAT issues.
Also exFAT does not have journal, so not best for larger partitions.

---

### Post by tea for one on 2022-07-20
Did you install Kali in UEFI mode?

[COLOR="#0000FF"]Line 98[/COLOR] - nvme0n1p1	: is---ESP,	fstab-has-bad-efi (Kali on partition 1)
[COLOR="#0000FF"]Line 101[/COLOR] - nvme0n1p5	: is---ESP,	fstab-has-goodEFI (Ubuntu 22.04 on partition 5)

---

### Post by ds047 on 2022-07-25
Hi,
Thank you for your help,I have managed to boot into Ubuntu after fixing grub with Boot-Repair.

With regards to the exFAT partition, I intend to have a windows install and a secondary OS for work and study stuff that require Windows and VMware is not an option(some software can detect it is a VM and refuse to run), thus the partition is intended to be used in both Ubuntu and Windows. Is there a better alternative that you recommend?

---

