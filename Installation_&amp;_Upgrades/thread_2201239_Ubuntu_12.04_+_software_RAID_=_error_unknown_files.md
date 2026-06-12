---
title: "Ubuntu 12.04 + software RAID = error: unknown filesystem, grub rescue (UEFI)"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by anatoli2 on 2014-01-23
Hi! I'm posting here for the first time, though reading this site looking for solutions almost every day.

I'm trying to install Ubuntu 12.04.3 with soft-RAID on a IBM server with UEFI support. After the installer reboot it fails with grub error: unknown filesystem. If I put the HDDs to another machine (a generic PC without UEFI) it boots correctly. I suspect it's either an issue with the UEFI/Legacy modes or with the hardware in some way, though may be the installer failed to detect/configure something and it should be fixed manually. Here are the details.

The IBM server:
[LIST]
[*]Brand new IBM System x3100 M4, firmware v1.07, IMM v3.65 (up-to-date)
[*]Intel Xeon E3-1240v2 @ 3.4GHz
[*]8Gb ECC RAM (all memtests OK)
[*]2 x SATA 1Tb WD RE4 (WD1003FBYZ)
[*]The system has a fake-RAID, but it is disabled in the BIOS (Configure SATA as: AHCI).
[/LIST]

The generic PC:
[LIST]
[*]Asus P5KPL
[*]Intel Pentium 4
[*]4Gb RAM
[*]Same HDDs from the IBM server
[/LIST]

The intended install:
[LIST]
[*]Ubuntu 12.04.3 Alternate x64 (ubuntu-12.04.3-alternate-amd64.iso)
[*]RAID1 for /boot (100Mb)
[*]RAID1 for / (10Gb)
[*]NO LVM
[/LIST]

(The separation of /boot and / is actually for LUKS to be installed on top of the / raid array, but this is another issue)

The firmware of the IBM server supports UEFI in some awkward way: it boots install CD in Legacy/MBR and HDDs/USB Storage in UEFI with some fallback to MBR. There is no way to change it or fine-tune it somehow (or at least I didn't figure out how).

Tried both on the IBM server: image burned on a CD (installs in Legacy (MBR), partition table msdos) and on a USB memory (installs in UEFI, partition table GPT). Both produce the grub rescue error. Same install on the generic PC (or disks with the install on the IBM server moved to the generic PC) boots correctly.


Here is how I install it (from a CD, in Legacy (MBR) mode):

Expert mode, default/basic options in the first steps up to Partition disks. There I recreate an empty partition table (msdos) on both HDDs, then, after creating/setting everything, it looks this way:

```
RAID1 device #0 - 98.4 MB Linux Software RAID Array
>     #1            98.4 MB     F  ext4          /boot
RAID1 device #1 - 10.0 GB Linux Software RAID Array
>     #1            10.0 GB     F  ext4          /
SCSI1 (0,0,0) (sda) - 1.0 TB ATA WDC WD1003FBYZ-0
>     #1  primary   98.6 MB  B  K  raid
>     #2  primary   10.0 GB     K  raid
>         pri/log  990.1 GB        FREE SPACE
SCSI3 (0,0,0) (sdb) - 1.0 TB ATA WDC WD1003FBYZ-0
>     #1  primary   98.6 MB  B  K  raid
>     #2  primary   10.0 GB     K  raid
>         pri/log  990.1 GB        FREE SPACE
```

Do you want to boot your system if your RAID becomes degraded? -> Yes
No swap (there is no need for it in my case, and it should not affect the boot process).

The rest of the steps are also completed with the default options (kernel: linux-generic-lts-raring, drivers: generic/targeted (tried both), software: none).
Install the GRUB boot loader to the master boot record? -> Yes
```
Running "grub-install /dev/sda /dev/sdb"...
```

Reboot

```
error: unknown filesystem
grub rescue>
```

If I enter there (this is on the IBM server):

```
grub rescue> insmod part_msdos
grub rescue> insmod normal
grub rescue> normal
```

the system boots correctly.. sometimes.. and sometimes it just reboots seconds after the last line entered (grub rescue> normal), as if ctrl+alt+del pressed. And once I've even seen

```
unaligned pointer 0xbf099492. [hmm, 32-bit address in 64-bit install??]
Aborted. Press any key to exit.
```

When it does boot, there is a delay of some 15s after pressing enter on the last line and before it starts accessing the HDDs for the boot sequence.

Please note: all (quick and full with 7 passes) memory tests (in the BIOS and memtest86+ of the install CD) pass without errors and the same install but without raid (same /boot and / partitions on one HDD) boots correctly.

Looks like a problem related to UEFI/Legacy modes (could it be that the firmware of the IBM server tries to boot the system in UEFI mode and GRUB, expecting GPT, doesn't load msdos partition table stuff or something similar?), but I don't have enough GRUB/initramfs/kernel/UEFI knowledge to figure it out. Another possibility I see is that the firmware/IMM resident code on the IBM server (which is a hypervisor, sort of a virtual machine that runs without interruptions during the OS reboots and halts) interferes somehow with the boot process (this would be the worst, unfixable case).

Here is the BootInfo summary from boot-repair (which actually doesn't fix this problem) executed from a LiveCD in Legacy (MBR) mode (ubuntu-12.04.3-desktop-amd64.iso) on the IBM server: [http://paste.ubuntu.com/6801133/](http://paste.ubuntu.com/6801133/).

Any ideas? Any way to debug step-by-step the bootloader? Please let me know if additional information is needed. Thanks in advance!

---

### Post by oldfred on 2014-01-24
I do not know RAID, and you seem to have a special version with your server anyway.

But with UEFI the efi partition needs to be first on drive and outside or before RAID in the UEFI installs I have seen work. 
For BIOS boot and with gpt partitioned drives you have to have a bios_grub partition of 1-2MB unformatted for grub2 to install correctly.
But most RAID installs install grub boot loader to root of RAID as BIOS boots that not MBR of drive in BIOS boot mode.

       grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

---

### Post by anatoli2 on 2014-01-26
Oldfred, thanks for your response. We were actually installing everything in MBR/Legacy mode (non-EFI install cd boot, msdos partition table at "Partition disks" step, non-EFI boot after installer reboot) and the RAID we were using was the Linux software RAID (the machine's fake-raid was turned off), and was getting the error.
 
We then tried to install everything in EFI mode (install from USB booted in EFI mode), GPT partition table, EFI Boot partition (sda1/sdb1) of 200Mb at the beginning, then 200Mb /boot partition (sd[ab]2) and 10Gb / partition (sd[ab]3); the last 2 (/boot and /) mirrored in RAID1 (md0 and md1 respectively), EFI boot after installer reboot) and was getting "error: efidisk read error". We managed to fix this with LiveUSB boot (works both in EFI and in non-EFI mode) and there boot-repair with SecureBoot option turned OFF (when it asks about buggy-kernel, say No). If we leave SecureBoot on, same problem occurs. We don't know what's wrong with the SecureBoot, but we won't investigate it further. Also, we don't know if the new grubx64.efi file, that the boot-repair writes to the EFI partition, boots in SecureBoot or not. If someone has an insight into this, please add a comment.
 
We tried the solution offered in the first link you posted (the grub2 bug report) and I confirm it works, though the "efidisk read error" flashes for an instant before it starts to boot.
 
We also tried the solution of creating a grub.cfg file in the EFI partition (proposed by Andy Sayler) and it didn't work, though Andy had a slightly different setup: /boot and / on the same RAID array. We tried some obvious tweaks but with no luck. I've added our solution to the bug report.
 
Changing the title of the post to [SOLVED].
 
Nevertheless, our final configuration (LUKS on top of the md1 RAID array) is still unattained. Here is a description of the problem: [http://ubuntuforums.org/showthread.php?t=2201983](http://ubuntuforums.org/showthread.php?t=2201983).

---

### Post by oldfred on 2014-01-27
Not sure about RAID differences again.

But shim is the secure boot version of grub that includes the Microsoft signing key. And you have to have signed kernel. If you install with secure boot on, then shim & signed kernels will be used. Or with Boot-Repair booted in secure boot mode will update system to secure boot.

---

### Post by anatoli2 on 2014-01-28
Oldfred, thanks for the explanation. I didn't know about shim and signed kernel relationship. So we decided to reinstall everything once more, paying special attention to all this details.
 
We installed U12.04.3 Alternate in EFI mode, chosen linux-signed-generic-lts-raring in the kernel option, proceeded with the rest of the install as described in my last post, checked that the new entry in the firmware pointed to shimx64.efi and.. got the same error: efidisk read error, grub rescue>.
 
We then proceeded with the LiveUSB boot, checked the grub.cfg file, it had:
 
```
linux /vmlinuz-3.8.0-35-generic.efi.signed root=/dev/mapper/md1_crypt ro quiet splash $vt_handoff
 
ls -lah /boot
total 21M
drwxr-xr-x  5 root root 1.0K Jan 28 15:48 .
drwxr-xr-x 23 root root 4.0K Jan 28 15:36 ..
-rw-r--r--  1 root root 899K Dec  4 14:49 abi-3.8.0-35-generic
-rw-r--r--  1 root root 152K Dec  4 14:49 config-3.8.0-35-generic
drwxr-xr-x  4 root root  512 Dec 31  1969 efi
drwxr-xr-x  3 root root 7.0K Jan 28 15:49 grub
-rw-r--r--  1 root root 5.8M Jan 28 15:47 initrd.img-3.8.0-35-generic
drwx------  2 root root  12K Jan 28 15:22 lost+found
-rw-r--r--  1 root root 173K Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root 175K Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root 3.1M Dec  4 14:49 System.map-3.8.0-35-generic
-rw-------  1 root root 5.3M Dec  4 14:49 vmlinuz-3.8.0-35-generic
-rw-------  1 root root 5.3M Jan 28 15:36 vmlinuz-3.8.0-35-generic.efi.signed
```
 
The first conclusion: the Ubuntu installer fails to correctly configure the system in any case. We then proceeded with the boot-repair, set ON the SecureBooot. After this operation grub.cfg linux line was the same and the /boot folder contents were also the same.

Reboot, same error.
 
LiveUSB again, boot-repair with SecureBoot OFF, reboot (in the firmware the boot entry points to grubx64.efi), the system boots correctly. grub.cfg linux line is the same and the /boot folder also has the same contents.
 
Any ideas why SB is not working in any configuration? Is there any way to turn SB off during the installation or in the system (without boot-repair)? We tried to boot with grubx64 just after the installation and got the same grub rescue error.
 
Also, do you know what "efidisk read error" means and how to fix it? I like the solution proposed in the grub bug report (the patch), but though it solves the problem, this efidisk error flashes for an instant before the OS starts to boot (with boot-repair there is no such error message). The fix would be the best solution (it's possible to apply it during the installation) if we could resolve the efidisk error.
 
With respect to the RAID, I wanted to say, in response to your comment "you seem to have a special version with your server", that the built-in fake-raid was always turned off, so the RAID we were using was mdadm, the common Linux software RAID (available in the installer at Partition disks step), as if there was no fake-raid in the server at all.

---

### Post by oldfred on 2014-01-28
I thought you had a hardware RAID, but there are many types and I only have picked up some of the grub/efi install issues.

I do not know if efi disk error is from UEFI or from grub?

Have you tried a grub.cfg with just one entry - configfile in the efi partition? As in post #2?
 This was not RAID so shows just path.
 configfile (hd0,gpt8)/boot/grub/grub.cfg

   found that putting grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

---

### Post by anatoli2 on 2014-01-30
[FONT=Calibri][COLOR=#000000][SIZE=3]Oldfred,
 
Responding to your good question from where does the efidisk error come, I've downloaded grub1.99 source and it's actually an error message of grub (grub-core/disk/efi/efidisk.c:578:    return grub_error (GRUB_ERR_READ_ERROR, "efidisk read error");), and grub 2.00 doesn't have it.
 
The code between the 2 versions looks significantly different, at least in the part I was looking at, so I decided not to investigate it more than 15min. There is some sort of abstraction layer, for the main logic not to deal with the specifics of each media. The function that generates the error is one of the abstraction functions for efi disk I/O, responsible for reading sectors from an efi-type disk. Why it fails in our case, I couldn't understand from this short inspection of the code. I would prefer to compile the 2.00 version and see if it has the same problem, than to continue investing time to the v1.99.
 
We didn't try the grub.cfg at efi partition with configfile directive solution as we were already tired of reinstalling everything and rebooting this server tens of times (the reboot takes some 5 minutes due to the firmware initialization).
 
As the v2.00 is already included in quantal, and in trusty it will be 2.02 in April, I think 1.99 investigations should be closed.
 
Thank you for your help, you helped us a lot.
 
For the sake of linking related stuff for people that will probably find all these obstacles on their way to RAID + LUKS + EFI, here is a problem we found when we tried to test the RAID for automatic recovery from a single disk failure: we powered off the server, removed one disk and booted it again. The mdadm could not correctly activate the degraded arrays in spite of the bootdegraded options in mdadm config for initramfs and the kernel param, and the cryptosetup stuck for 180s waiting for the root device, then dropped to the initramfs prompt. We finally solved it and found that there are a number of open bug reports (one from 2008!!) for this issue. Here are the details: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/251164](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/251164). For the solution, check the comment #30.
 
Just two weeks and it's working.. : )
[/SIZE][/COLOR][/FONT]

---

### Post by oldfred on 2014-01-30
Thanks for update. 

I also think 12.04.4 will be out in a couple of weeks and will also have a newer grub. Not sure exactly which one as I have not installed 12.04.4 to see what has changed.

Each new version of grub has had major updates to UEFI and booting in general.

---

