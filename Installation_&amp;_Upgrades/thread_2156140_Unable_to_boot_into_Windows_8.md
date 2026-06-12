---
title: "Unable to boot into Windows 8"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by matthew5025 on 2013-06-20
I'm using a w530 with an extra mSATA 16GB SSD, and installed Ubuntu 13.04 onto the mSATA drive.
The main SSD (480GB) has Windows 8 on it with BitLocker enabled.
After performing an UEFI installation of ubuntu via a USB drive, GRUB boots directly into Ubuntu, so I ran boot-repair as per [this ]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system")post.
The pastebin results are [here]("http://paste.ubuntu.com/5784755/").
Now upon boot, I get a few options, inculding Windows 8, but upon selecting them, I get the error
```
disk hd1,gpt2 not found
```
Ubuntu boots just fine.
If anyone has any suggestions, I'll be more then willing to try them
Thanks!

---

### Post by oldfred on 2013-06-20
It does not look like you did a UEFI install, although now Boot-Repair has added efi files.

Both drives have a Windows boot loader in the protective MBR, but sdb is still MBR not gpt. Normally to boot with UEFI drive must be gpt partitioned.

       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

---

### Post by cincinnatus13 on 2013-06-20
A quick look suggests to me that it is looking at the wrong hard drive.

IIRC, it starts at 0 so since /dev/sda1 is where Windows is located the correct format for the code is 
disk hd0,gpt2
I would think hd1 is actually the ext4 partition on your second SSD and therefore it's looking to that for a boot but obviously is not getting any kind of Windows bootloader.

---

### Post by matthew5025 on 2013-06-21
> **oldfred said:**
> It does not look like you did a UEFI install, although now Boot-Repair has added efi files.

Both drives have a Windows boot loader in the protective MBR, but sdb is still MBR not gpt. Normally to boot with UEFI drive must be gpt partitioned.

       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

I don't quite get what you mean, but here's what gparted has to say about the two drives.
[IMG]http://i.imgur.com/lDsFLrf.png[/IMG]

[IMG]http://i.imgur.com/Ki6JEd3.png[/IMG]

> **cincinnatus13 said:**
> A quick look suggests to me that it is looking at the wrong hard drive.

IIRC, it starts at 0 so since /dev/sda1 is where Windows is located the correct format for the code is 
disk hd0,gpt2
I would think hd1 is actually the ext4 partition on your second SSD and therefore it's looking to that for a boot but obviously is not getting any kind of Windows bootloader.

I tried editing the command in grub before boot by pressing 'e' but still get
```
disk hd0,gpt2 not found
```

---

### Post by oldfred on 2013-06-21
Please attach screen shots with paperclip icon in Go Advanced post, not in body.
Gparted does not show anything more than BootInfo report shows and does not show whether drive is gpt or MBR. Although sometimes the graphical output is easier to see if many partitions.

If you look at line 68 in BootInfo it says for sda GUID detected. That means it is gpt(GUID) partitioned. There is not entry like that for sdb, so it is MBR(msdos). So that may contribute to the issues. Better if both drives are gpt. See more info on two drive UEFI installs in link in my signature.

---

### Post by matthew5025 on 2013-06-21
> **oldfred said:**
> It does not look like you did a UEFI install, although now Boot-Repair has added efi files.

Both drives have a Windows boot loader in the protective MBR, but sdb is still MBR not gpt. Normally to boot with UEFI drive must be gpt partitioned.

       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

> **oldfred said:**
> Please attach screen shots with paperclip icon in Go Advanced post, not in body.
Sorry about that :(

> **oldfred said:**
> Gparted does not show anything more than BootInfo report shows and does not show whether drive is gpt or MBR. Although sometimes the graphical output is easier to see if many partitions.

If you look at line 68 in BootInfo it says for sda GUID detected. That means it is gpt(GUID) partitioned. There is not entry like that for sdb, so it is MBR(msdos). So that may contribute to the issues. Better if both drives are gpt. See more info on two drive UEFI installs in link in my signature.

Anyway, I have decided to DBAN my whole computer and start afresh. Would you recommend having a EFI partition on both the WIN8 disk and the Ubuntu one, or is one enough?
Also, if you have any suggestions on how I should proceed, do share them =)

---

### Post by oldfred on 2013-06-21
System will boot from one efi partition, but I suggest an efi partition on every drive, just in case later you want to boot it separately. But with your small SSD that may not be as necessary.

Are you primarily a Windows or Ubuntu user. If Windows you may want to keep the SSD for Windows with the Intel SRT. If Ubuntu then having / (root) on the SSD makes better use of SSD, but since it is small you need all you data on rotating drive.

I have not installed Windows 8, so I do not know much about it other than all the reports posted. Probably best to let it install to your hard drive and then resize from within Windows. Then install Ubuntu. Both need to be installed in UEFI mode. And how you boot install media is how it installs.

---

### Post by matthew5025 on 2013-06-23
> **oldfred said:**
> System will boot from one efi partition, but I suggest an efi partition on every drive, just in case later you want to boot it separately. But with your small SSD that may not be as necessary.

Are you primarily a Windows or Ubuntu user. If Windows you may want to keep the SSD for Windows with the Intel SRT. If Ubuntu then having / (root) on the SSD makes better use of SSD, but since it is small you need all you data on rotating drive.

I have not installed Windows 8, so I do not know much about it other than all the reports posted. Probably best to let it install to your hard drive and then resize from within Windows. Then install Ubuntu. Both need to be installed in UEFI mode. And how you boot install media is how it installs.

Thanks for all your help! I'll try dual boot again once Windows 8.1 Beta is out.
I'll open another thread if I encounter any problems. Thanks again!

---

