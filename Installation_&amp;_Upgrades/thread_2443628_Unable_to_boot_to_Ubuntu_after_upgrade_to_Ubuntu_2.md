---
title: "Unable to boot to Ubuntu after upgrade to Ubuntu 20.04 LTS"
date: 2020-05-18
forum: Installation &amp; Upgrades
---

### Post by avi-aus on 2020-05-18
I upgraded Ubuntu to 20.04 LTS on a machine with dual boot (Windows 10 & Ubuntu).
OS upgrade was at the last stage  showing a message related to boot security with some text.

At that point I couldn't progress further.

After rebooting the machine I couldn't boot to Ubuntu (windows 10 boot is OK)

I changed my EFI setting to disable boot security but still couldn't boot from the Grub menu and recover also failed.

I started Ubuntu from USB and attempted re-installation which found a missing boot partition.

I ran the boot-repair tool from Ubuntu loaded from a USB with the tool's report at [https://paste.ubuntu.com/p/w29vy4kdYy/](https://paste.ubuntu.com/p/w29vy4kdYy/)

My question is based on the report from the boot-repair tool should I go ahead with the tool recommendation or do something else to repair and enable booting to Ubuntu?

Note that my Windows 10 boot works OK from Grub and it looks like my upgraded Ubuntu partition is OK  

[COLOR=#000000]Any help would be greatly appreciated,[/COLOR]
[COLOR=#000000]Regards![/COLOR]

---

### Post by yancek on 2020-05-18
>  OS upgrade was at the last stage  showing a message related to boot security with some text

You should post that message here   as there is no other way for members here to know what it is?

> My question is based on the report from the boot-repair tool should I go  ahead with the tool recommendation or do something else to repair and  enable booting to Ubuntu?
 

No, don't do that.  First, in boot repair from lines 8-20 you see information and files in the EFI partition for both windows and ubuntu.  That's all good.  Lines 52-58 show your Ubuntu is installed on partition 6 of the drive.  Beginning on line 88 of boot repair, you show information for efibootmgr.  You show Linpus Lite as first in boot order as well as current boot.  Do you still actually have Linpus Lite installed?  Beginning at line 202, you see the content of the grub.cfg file on the EFI partition which is pointing to the grub.cfg file on the system partition (partiiton 6).  The grub.cfg file on the Ubuntu system partition is the file which has the actual Grub menu you see on screen.  Boot repair generally includes the contents of this file in its output but it is not present in yours.  Not sure if the installation of Grub failed or it is some other problem.  Posting the error you mentioned above would be helpful.  Another thing you can do is boot the Ubuntu on the usb and mount the Ubuntu partition: /dev/nvme0n1p6   and check to see if the necessary Grub file (including grub.cfg) are there.

Before doing that, take a look at line 93 of boot repair.  This shows the option to boot Ubuntu and you should access your BIOS firmware and change the boot option there to set Ubuntu (Boot0001*) to first boot priority there and see if that helps.

---

### Post by avi-aus on 2020-05-18
The Ubuntu upgrade did not end with an error, it simply paused on the message regarding the need to provide security boot password with the [OK] at the end.
At that point pressing [Enter] did not continue the process.
In hindsight  may be [tab] would help but I pressed [ctl-c] which most likely ended the process prematurely.

The Linpus Lite is first in boot because I changed the boot order to boot from the USB so I can load Ubuntu from the USB.

Once Ubuntu loaded from the USB I can see the Grub files on the Ubuntu partition (see attached ) and the date is from yesterday the day I performed the upgrade.

Thanks

---

### Post by yancek on 2020-05-18
Did you go into the BIOS and change the boot option to  Ubuntu Boot0001*?
Post the contents of the grub.cfg file you are showing in your post above?

---

### Post by avi-aus on 2020-05-18
The BIOS entries are pointing to the same destination ( I attached a photo ).
Is that might be another unrelated issue if I want to change the order and go directly to Windows or Ubuntu?

I also attached the grub.cfg as a zip file

Thanks

---

### Post by oldfred on 2020-05-18
```
BootOrder: 0003,0001,0002,0000,2001,2002,2003
Boot0000* Windows Boot Manager	HD(1,GPT,896c368c-516a-495c-b50c-55fc8026b930,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* ubuntu	HD(1,GPT,896c368c-516a-495c-b50c-55fc8026b930,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* Windows Boot Manager	HD(1,GPT,896c368c-516a-495c-b50c-55fc8026b930,0x800,0x82000)/File(\EFI\ubuntu\[COLOR=#ff0000]g[/COLOR][COLOR=#ff0000]rubx64.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...m................
Boot0003* Linpus lite	HD(1,MBR,0xc522c,0x800,0x777000)/File(\EFI\Boot\grubx64.efi)RC

```

Your second Windows entry 0002 has the boot of grub. With early UEFI that was a work around for Windows that would not boot Ubuntu. But it does not really work with Windows 10. Updates overwrite it. Grub only boots working Windows and a Windows update also turns on fast start up which then prevents grub from booting Windows.

Use efibootmgr to see entries (should be same as above from Boot-Repair and then use efibootmgr to remove entry.
You probably should also remove 0003 also.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

If you have UEFI Secure Boot on and installer wants to install a proprietary driver for video or WiFi then you have to provide security key as Ubuntu cannot verify proprietary drivers are safe, but a user can a key. Best to just have UEFI secure boot off.

---

### Post by avi-aus on 2020-05-19
As suggested by @oldfred I disabled the Windows [COLOR=#000000]fast start up and also removed Boot002 ( the old Windows entry).

I still can't start Ubuntu from the Grab menu which I think is related to the fact that the Ubuntu upgrade didn't fully ended properly
As I mentioned in my previous post

Note that my 'Lenovo Setup Utility' still shows the same EFI entries as shown in my previous attached photo (and all items have the same 'SAMSUNG  MZVLB5...' destinations)

[/COLOR][COLOR=#000000]The Ubuntu upgrade did not end with an error, it simply paused on the message regarding the need to provide security boot password with the [OK] at the end.[/COLOR]
[COLOR=#000000]At that point pressing [Enter] did not continue the process.[/COLOR]
[COLOR=#000000]In hindsight may be [tab] would help but I pressed [ctl-c] which most likely ended the process prematurely.

Note also that if I attempt to _repair_ the installation by booting Ubuntu from the USB and starting re-installation I get a popup window with a message '**No EFI System Partition was found...**' (see attached  photo )

[/COLOR][COLOR=#000000]Is there a way to 'repair' the current upgraded Ubuntu or worst case what do I need to do to install anew Ubuntu on the same partition  of the current inaccessible Ubuntu.
Thanks [/COLOR]

---

### Post by oldfred on 2020-05-19
Try Boot-Repair's advanced mode.
Choose install & drive & also install latest kernel.
That may or may not be enough of an update to boot. You may then still need some cleanup/repairs.

I wonder if some new issue. Ubiquity used to only install to first drive, usually sda, or first NVMe drive.
I installed NVMe drive and install of 20.04 worked and booted from NVMe drive's ESP. I also have an ESP on sda drive.
But just tried to do  a simple install-grub without specifying ESP/UEFI and it said it could not find the efi partition. 

This did not work.
 sudo grub-install
But this did? Maybe because this reads mount of esp in NVMe drive in fstab?
fred@Z170N-focal:~$ sudo grub-install --efi-directory=/boot/efi
[sudo] password for fred: 
Installing for x86_64-efi platform.
Installation finished. No error reported.

---

### Post by avi-aus on 2020-05-20
Just to make sure that I select the preferred options suggested, I attached the various options shown on the boot-repair GUI (jpg for each tab)

Any advice on which one to select will be much appreciated. 

I am also cautious about the option 'separate/boot/efi partition' in the grub-location tab, should I deselect it?  I don't want to impact the windows boot.

Thanks

---

### Post by oldfred on 2020-05-20
Ubuntu & Windows normally share one ESP - efi system partition. They have different folders.
I would check to uninstall & reinstall grub options and newest kernel.
Only if you manually edited grub settings, may you want to back those up or remember those. But reinstall will reset everything to defaults. 

Install of grub will make "ubuntu" entry default boot entry. But with UEFI you can always go into UEFI boot menu and select the Windows entry. 
Grub will only boot working Windows, so when Windows turns fast start up back on or needs chkdsk, you have to directly boot Windows. Still best to have Windows repair disk in case major repairs needed.

---

### Post by avi-aus on 2020-05-22
I tried to grub-install with a few variations but it failed to execute.

I followed these steps

```
sudo fdisk -l

Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: SAMSUNG MZVLB512HAJQ-000L2              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 71CC76EF-8E07-4372-8A8F-2F9CB8013ED6

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  476532735 475965440   227G Microsoft basic data
/dev/nvme0n1p4 945737728  998166527  52428800    25G Microsoft basic data
/dev/nvme0n1p5 998166528 1000214527   2048000  1000M Windows recovery environment
/dev/nvme0n1p6 476532736  945737727 469204992 223.8G Linux filesystem

Partition table entries are not in disk order.


ubuntu@ubuntu:~$ sudo blkid
/dev/nvme0n1p1: LABEL="SYSTEM_DRV" UUID="A20B-FE9F" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="896c368c-516a-495c-b50c-55fc8026b930"
/dev/nvme0n1p3: LABEL="Windows" UUID="3E120CCA120C88DB" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e0d798b0-def1-4614-9c66-5acfd7b4c440"
/dev/nvme0n1p4: LABEL="LENOVO" UUID="D4B43793B43776D8" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0e3d7dcd-7594-4c5a-9bc9-f01ffc96eddc"
/dev/nvme0n1p5: LABEL="WINRE_DRV" UUID="46CA0E87CA0E7409" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="c89e22fc-8129-420b-8b59-66a55f03e871"
/dev/nvme0n1p6: UUID="40b8ea6a-5078-4bb3-97c1-945dd585cc3f" TYPE="ext4" PARTUUID="4e8ff545-e9e7-4ba0-b3ee-498996cbab33"
/dev/sda1: LABEL="UBUNTU 20_0" UUID="2438-1546" TYPE="vfat" PARTUUID="000c522c-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="2b4cfee5-fef0-4566-b341-e7df6e208d03"

sudo mkdir /mnt/ubuntu

sudo mount /dev/nvme0n1p6 /mnt/ubuntu

sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/nvme0n1

Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.


buntu@ubuntu:~$ sudo grub-install --efi-directory=/mnt/ubuntu/boot/efi
Installing for i386-pc platform.
grub-install: error: install device isn't specified.


buntu@ubuntu:~$ sudo grub-install --efi-directory=/mnt/ubuntu/boot/efi nvme0n1p6
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
```


Note that /mnt/ubuntu/boot/efi  folder is empty

My questions are:
Which device or disk I need to provide to the grub-install command? Is it the Linux partition /dev/nvme0n1p6 , the EFI partition /dev/nvme0n1p1 or the disk nvme0n1 ?
What is the full grub-install command that you think I can run?

---

### Post by wildmanne39 on 2020-05-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by yancek on 2020-05-22
> I tried to grub-install with a few variations but it failed to execute.
 

You haven't posted the commands you did try so it is not possible to point out any errors.  Did you use the commands suggested by oldfred in post 8, the ones he said worked?  Installing to the device rather than the partition would be the correct method and should put Grub files on both the EFI and system partition.

---

### Post by oldfred on 2020-05-22
You have an UEFI system with UEFI install of Windows.
But are trying to install the BIOS boot version of grub.
For BIOS on gpt you need the bios_grub partition. But you do not want the BIOS boot anyway.

How you boot install media, UEFI or BIOS, is then how it installs. You always want to boot in UEFI mode.
You should have two options in UEFI boot menu to boot flash drive. One "UEFI:flash" and other "flash" where flash will be name or label of flash drive. Some have totally different sub-menus, with all UEFI entries in one & all BIOS/Legacy/CSM in the other.

For both BIOS & UEFI you always specify the drive to install into, not a partition. With UEFI it knows & finds the ESP - efi system partition to actually place the boot files. 
With BIOS part of grub is in MBR, part is in sectors after MBR, and part is in / (root). 

See also link in my signature.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by avi-aus on 2020-05-23
It looks like I was missing the mount of EFI partition.

I followed the steps in [https://linuxsuperuser.com/reinstall-grub2-efi-bootloader-ubuntu/](https://linuxsuperuser.com/reinstall-grub2-efi-bootloader-ubuntu/) and managed to complete the grub update successfully.

After that I got the following error "Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

To fix the above I booted from liveUSB mounted the partitions as for above
and ran following:
 root@ubuntu:/# update-initramfs -u -k 5.4.0-29-generic

The above based on  [https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)

I can now boot Ubuntu with no issues.
Thanks all for the replies

---

