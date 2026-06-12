---
title: "grub-efi-amd64-signed Fails to Install"
date: 2020-01-10
forum: Installation &amp; Upgrades
---

### Post by Yogi2 on 2020-01-10
**MY COMPUTER**[INDENT]Model: Msi GL72 7QF
 Processor: Intel i7-7700HQ; 2.8GH
 RAM: 16GB DDR4
 GPU: nVidia GTX960M, Optimus enabled
 SSD: 500GB, GPT UEFI
 OS: Windows10 Insider Preview; Mageia7; (Ubuntu 18.04.3 LTS)

Secure boot and fast boot: disabled
[/INDENT]
  [HR][/HR]
 When I installed Ubuntu alongside the other two OS's, I received the following error message during the installation process:

> The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.

The Ubuntu Ubiquity installer apparently crashes before completing the install, but not before it writes to the ESP partition in spite of the message:

```
[root@localhost mnt]# ls -l
total 20
drwxrwxrwx 3 root root 4096 Aug 22 02:30 '$WINDOWS.~SY'/
drwxrwxrwx 3 root root 4096 Dec 31 21:28  boot-repair/
drwxrwxrwx 4 root root 4096 May 15  2019  boot-sav/
drwxrwxrwx 8 root root 4096 Jan  9 00:12  EFI/
drwxrwxrwx 4 root root 4096 May 29  2019 'System Volume Information'/
[root@localhost mnt]# cd EFI
[root@localhost EFI]# ls -l
total 24
drwxrwxrwx 4 root root 4096 Dec 31 23:09 Boot/
drwxrwxrwx 2 root root 4096 Nov 29 17:28 mageia/
drwxrwxrwx 4 root root 4096 Nov  1 16:58 Microsoft/
drwxrwxrwx 4 root root 4096 Nov  1 16:58 MSI/
drwxrwxrwx 4 root root 4096 Nov  1 16:58 refind/
drwxrwxrwx 3 root root 4096 Jan  9 00:12 ubuntu/
[root@localhost EFI]# cd ubuntu
[root@localhost ubuntu]# ls -l
total 3724
-rwxrwxrwx 1 root root     108 Jan 10  2020 BOOTX64.CSV*
drwxrwxrwx 2 root root    4096 Jan  9 00:12 fw/
-rwxrwxrwx 1 root root   75992 Jan  9 00:12 fwupx64.efi*
-rwxrwxrwx 1 root root     126 Jan 10  2020 grub.cfg*
-rwxrwxrwx 1 root root 1116024 Jan 10  2020 grubx64.efi*
-rwxrwxrwx 1 root root 1269496 Jan 10  2020 mmx64.efi*
-rwxrwxrwx 1 root root 1334816 Jan 10  2020 shimx64.efi*
[root@localhost ubuntu]# 

```

I want load Ubuntu (Grub) via the Windows Boot Device Manager, and 'ubuntu' is in fact listed as an option but it will not boot - the OS install did not complete.  At this point in time I deleted the partition targeted for Ubuntu because it's broken. The /dev/sda2 ESP partition was checked using *fsck *and *chkdsk *and has no reported problems.  What is the best way to successfully install Ubuntu in this case?

---

