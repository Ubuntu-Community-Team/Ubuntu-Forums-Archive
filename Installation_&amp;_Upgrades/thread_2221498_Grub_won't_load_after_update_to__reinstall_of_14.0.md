---
title: "Grub won't load after update to / reinstall of 14.04"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by tobanw on 2014-05-02
I dual boot Windows 8 and Ubuntu (64-bit) on a UEFI booting ultrabook (Toshiba Z930) with secure boot disabled. Everything was fine in 13.10, but after the update to 14.04, I was getting this error on boot, followed by the grub rescue prompt:
```
error: symbol 'grub_term_highlight_color' not found
```

I have a live USB running 64-bit 14.04, so I installed boot-repair on that (from ppa:yannubuntu) and ran it (a few times), but it finished with an error: [http://paste.ubuntu.com/7321842/](http://paste.ubuntu.com/7321842/). (Also, upon launching boot-repair, I get a message saying it will install packages from 13.10.)

I had no luck after much searching and trying, so I just reinstalled 14.04 (I have a separate home partition on sda7, root is sda6). I followed the same method I used to initially install Ubuntu 13.04 (specifically, I selected sda2 as device for bootloader installation). But I'm still having the same problem. Now the error preceding the grub rescue prompt is
```
error: no such device: 4acd1e08-8d71-424c-8a98-353007d892e7
```
Boot-repair still finishes with an error: [http://paste.ubuntu.com/7373731](http://paste.ubuntu.com/7373731) is the most recent try. Since 13.04 installed fine, and the upgrade to 13.10 worked, there must be something in 14.04 that's breaking it.

I tried the first answer here [http://askubuntu.com/questions/449680/upgrading-from-13-10-to-14-04-broke-grub](http://askubuntu.com/questions/449680/upgrading-from-13-10-to-14-04-broke-grub) but got an error (looks like it wants to use BIOS/MBR but I have UEFI/GPT setup):
```
root@ubuntu:/# grub-install /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

Here's the output of 'sudo parted -l':
```
Model: ATA TOSHIBA THNSNF25 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  473MB   472MB   ntfs            Basic data partition  hidden, diag
 2      473MB   746MB   273MB   fat32           Basic data partition  boot
 3      746MB   880MB   134MB   ntfs            Basic data partition  msftres
 4      880MB   69.2GB  68.4GB  ntfs            Basic data partition  msftdata
 5      69.2GB  69.6GB  367MB   ntfs                                  hidden, diag
 6      69.6GB  104GB   34.4GB  ext4                                  msftdata
 7      104GB   243GB   139GB   ext4                                  msftdata
 8      243GB   250GB   6442MB  linux-swap(v1)
 9      250GB   256GB   6442MB                  Basic data partition


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 31.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  31.5GB  31.5GB  primary  fat32        boot, lba
```

I don't even see the device id from the error message:
```
ubuntu@ubuntu:~$ sudo blkid 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="27d915f7-101a-4431-a487-6c84e0199c58" TYPE="ext3" 
/dev/sda1: LABEL="System" UUID="1874AF3A74AF1A10" TYPE="ntfs" 
/dev/sda2: UUID="6EAF-D376" TYPE="vfat" 
/dev/sda3: UUID="68B4B0BDB4B08ED6" TYPE="ntfs" 
/dev/sda4: LABEL="TI30940300B" UUID="01CE44E98DCA09A0" TYPE="ntfs" 
/dev/sda5: UUID="1688FF7788FF53A9" TYPE="ntfs" 
/dev/sda6: UUID="0aa66c1e-127c-44cc-9c2e-9609f94742cb" TYPE="ext4" 
/dev/sda7: UUID="87d577a5-198f-4ae0-8ae2-e022e8c2173c" TYPE="ext4" 
/dev/sda8: UUID="6e88bec1-00d0-4971-b5e8-0001b791b540" TYPE="swap" 
/dev/sdb1: LABEL="KINGSTON" UUID="0D0C-E4EF" TYPE="vfat" 
```

Any help is deeply appreciated!

---

### Post by enzideout on 2014-05-02
have you tried doing "dpkg-reconfigure grub-pc"? There is another thread here that has other solutions to try. [http://ubuntuforums.org/showthread.php?t=2218362](http://ubuntuforums.org/showthread.php?t=2218362)

---

### Post by oldfred on 2014-05-02
+1 on enzideout's link

If Boot-Repair or grub is asking for a bios_grub partition, then you are in BIOS mode not UEFI mode.
Be sure to boot in UEFI mode if system is UEFI.

---

### Post by tobanw on 2014-05-02
I just double checked the 'setup' on boot, and the boot mode is set to UEFI.

I saw the "dpkg-reconfigure grub-pc" method, but I can't boot in to run it. I'm currently stuck in a live USB. Is there a way I run it from the live session?

---

### Post by oldfred on 2014-05-02
You need to chroot into your install. 
I think Boot-Repairs full uninstall and reinstall of grub in advanced options is a chroot. And that may also work as a full reinstall of grub.

Or you can chroot and then run the dpkg command instead of reinstall of grub. 
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by tobanw on 2014-05-02
I'm trying to chroot and run the dpkg command. I followed drs305's instructions: mounted the normal partition and the other directories, chroot-ed into the mounted normal partition, and checked the internet connection. Then I tried:

```
root@ubuntu:/# dpkg-reconfigure grub-pc
dpkg-query: package 'grub-pc' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub-pc is not installed
```

drs305's instructions may not be up to date for UEFI. Is my system not using 'grub-pc', but 'grub-efi'?

---

### Post by oldfred on 2014-05-02
You probably do have to mount efi partition as that is where grub-efi(UEFI boot) will install.

If in BIOS mode then grub-pc (BIOS boot) needs a bios_grub partition, but uses that automatically.

It looks like this includes the extra mount of the efi partition.

[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by tobanw on 2014-05-02
I mounted the efi partition (sda2) as in your link, then chroot-ed and ran 'dpkg-reconfigure grub-pc', but I got the exact same message ('grub-pc' not installed).

Should I be running dpkg-reconfigure on grub-efi instead?

Thanks for all your help thus far!

---

### Post by oldfred on 2014-05-02
If you have UEFI boot which I think you do then yes, run grub-efi instead, but that is not its real name. 

see posts 129, 130 & 138.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)

Does this then work?
sudo dpkg-reconfigure grub-efi-amd64

Does this show your grub files or does it have to be a different command as grub-efi or grub-efi-amd64 as you do not have grub-pc?
 sudo debconf-show grub-pc

I do not have UEFI so cannot test myself.

---

### Post by tobanw on 2014-05-02
OK, I followed the method in post #130 [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977/") (and also mounted the efi partition, sda2). Here's the grubs I have installed:

```
root@ubuntu:/# dpkg-query -l 'grub*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                     Version                   Architecture              Description
+++-========================================-=========================-=========================-=================================================================
un  grub                                     <none>                    <none>                    (no description available)
ii  grub-common                              2.02~beta2-9              amd64                     GRand Unified Bootloader (common files)
un  grub-coreboot                            <none>                    <none>                    (no description available)
un  grub-doc                                 <none>                    <none>                    (no description available)
ii  grub-efi                                 2.02~beta2-9              amd64                     GRand Unified Bootloader, version 2 (dummy package)
ii  grub-efi-amd64                           2.02~beta2-9              amd64                     GRand Unified Bootloader, version 2 (EFI-AMD64 version)
ii  grub-efi-amd64-bin                       2.02~beta2-9              amd64                     GRand Unified Bootloader, version 2 (EFI-AMD64 binaries)
un  grub-efi-ia32                            <none>                    <none>                    (no description available)
un  grub-efi-ia64                            <none>                    <none>                    (no description available)
un  grub-emu                                 <none>                    <none>                    (no description available)
un  grub-ieee1275                            <none>                    <none>                    (no description available)
un  grub-legacy                              <none>                    <none>                    (no description available)
un  grub-legacy-doc                          <none>                    <none>                    (no description available)
un  grub-linuxbios                           <none>                    <none>                    (no description available)
un  grub-pc                                  <none>                    <none>                    (no description available)
un  grub-xen                                 <none>                    <none>                    (no description available)
un  grub-yeeloong                            <none>                    <none>                    (no description available)
un  grub2                                    <none>                    <none>                    (no description available)
ii  grub2-common                             2.02~beta2-9              amd64                     GRand Unified Bootloader (common files for version 2)

```

So I don't have grub-pc and it appears that grub-amd-64 is the droid I'm looking for.

```
root@ubuntu:/# dpkg-reconfigure grub-efi-amd64
Installing for x86_64-efi platform.
Installation finished. No error reported.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Adding boot menu entry for EFI firmware configuration
done

```

Rebooted, but to no avail. Still getting grub rescue. Tried boot-repair again; no help... [http://paste.ubuntu.com/7381784/](http://paste.ubuntu.com/7381784/)

chroot-ed back into sda6 with everything mounted as before. Here are the outputs that post #138 gave:

```
root@ubuntu:/# debconf-show grub-efi-amd64
  grub2/device_map_regenerated:
* grub2/linux_cmdline:
* grub2/linux_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:

root@ubuntu:/# debconf-show grub-efi

root@ubuntu:/# debconf-show grub-pc
  grub-pc/mixed_legacy_and_grub2: true
  grub2/kfreebsd_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/install_devices:
  grub-pc/install_devices_failed: false
  grub-pc/kopt_extracted: false
  grub-pc/timeout: 10
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_disks_changed:
  grub-pc/disk_description:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/partition_description:
  grub-pc/hidden_timeout: true
  grub2/device_map_regenerated:
* grub2/linux_cmdline_default: quiet splash

root@ubuntu:/# efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0005,0004,0001,0000,0003,0002
Boot0000* USB Memory    ACPI(a0341d0,0)PCI(14,0)USB(0,0)
Boot0001* HDD/SSD    ACPI(a0341d0,0)PCI(1f,2)ATAPI(0,0,0)
Boot0002* LAN2    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b79ef465,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0
Boot0003* LAN1    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b79ef465,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000
Boot0004* Windows Boot Manager    HD(2,e1800,82000,e34ed14d-1c71-11e2-a8e1-e8e0b79ef465)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...9................
Boot0005* ubuntu    HD(2,e1800,82000,e34ed14d-1c71-11e2-a8e1-e8e0b79ef465)File(\EFI\ubuntu\grubx64.efi)

```
And the /boot/efi directory (warning: tons of entries in the Microsoft and toshiba directories):
```
root@ubuntu:/# ls -lR /boot/efi/
/boot/efi/:
total 12
-r-xr-xr-x 1 root root  512 Oct 25  2013 BOOTSECT.BAK
drwxr-xr-x 8 root root 4096 Apr 30  2013 EFI
drwxr-xr-x 2 root root 4096 Apr 25 13:25 grub

/boot/efi/EFI:
total 24
drwxr-xr-x 2 root root 4096 Oct 28  2013 Boot
drwxr-xr-x 2 root root 4096 Apr 30  2013 grub
drwxr-xr-x 2 root root 4096 Apr 30  2013 linuxmint
drwxr-xr-x 3 root root 4096 Oct 22  2012 Microsoft
drwxr-xr-x 3 root root 4096 Oct 22  2012 toshiba
drwxr-xr-x 2 root root 4096 Apr 24 11:57 ubuntu

/boot/efi/EFI/Boot:
total 1452
-rwxr-xr-x 1 root root 1354480 Jul 25  2012 bkpbootx64.efi
-rwxr-xr-x 1 root root  127488 Oct 28  2013 bootx64.efi

/boot/efi/EFI/grub:
total 120
-rwxr-xr-x 1 root root 122880 Apr 30  2013 grubx64.efi

/boot/efi/EFI/linuxmint:
total 1452
-rwxr-xr-x 1 root root     125 Apr 30  2013 grub.cfg
-rwxr-xr-x 1 root root  122880 Apr 30  2013 grubx64.efi
-rwxr-xr-x 1 root root 1357480 Apr 30  2013 shimx64.efi

/boot/efi/EFI/Microsoft:
total 4
drwxr-xr-x 40 root root 4096 Oct 28  2013 Boot

/boot/efi/EFI/Microsoft/Boot:
total 4664
-rwxr-xr-x 1 root root   49152 Apr 23 21:48 BCD
-rwxr-xr-x 1 root root   40960 Oct 22  2012 BCD.LOG
-rwxr-xr-x 1 root root       0 Oct 22  2012 BCD.LOG1
-rwxr-xr-x 1 root root       0 Oct 22  2012 BCD.LOG2
drwxr-xr-x 2 root root    4096 Oct 22  2012 bg-BG
-rwxr-xr-x 1 root root 1354480 Jul 25  2012 bootmgfw.efi
-rwxr-xr-x 1 root root 1601880 Sep 29  2013 bootmgr.efi
-rwxr-xr-x 1 root root   65536 Oct 25  2013 BOOTSTAT.DAT
-rwxr-xr-x 1 root root    4247 Aug 22  2013 boot.stl
drwxr-xr-x 2 root root    4096 Oct 22  2012 cs-CZ
drwxr-xr-x 2 root root    4096 Oct 22  2012 da-DK
drwxr-xr-x 2 root root    4096 Oct 22  2012 de-DE
drwxr-xr-x 2 root root    4096 Oct 22  2012 el-GR
drwxr-xr-x 2 root root    4096 Oct 22  2012 en-GB
drwxr-xr-x 2 root root    4096 Oct 22  2012 en-US
drwxr-xr-x 2 root root    4096 Oct 22  2012 es-ES
drwxr-xr-x 2 root root    4096 Oct 22  2012 et-EE
drwxr-xr-x 2 root root    4096 Oct 22  2012 fi-FI
drwxr-xr-x 2 root root    4096 Oct 22  2012 Fonts
drwxr-xr-x 2 root root    4096 Oct 22  2012 fr-FR
drwxr-xr-x 2 root root    4096 Oct 22  2012 hr-HR
drwxr-xr-x 2 root root    4096 Oct 22  2012 hu-HU
drwxr-xr-x 2 root root    4096 Oct 22  2012 it-IT
drwxr-xr-x 2 root root    4096 Oct 22  2012 ja-JP
drwxr-xr-x 2 root root    4096 Oct 22  2012 ko-KR
drwxr-xr-x 2 root root    4096 Oct 22  2012 lt-LT
drwxr-xr-x 2 root root    4096 Oct 22  2012 lv-LV
-rwxr-xr-x 1 root root 1493344 Aug 22  2013 memtest.efi
drwxr-xr-x 2 root root    4096 Oct 22  2012 nb-NO
drwxr-xr-x 2 root root    4096 Oct 22  2012 nl-NL
drwxr-xr-x 2 root root    4096 Oct 22  2012 pl-PL
drwxr-xr-x 2 root root    4096 Oct 22  2012 pt-BR
drwxr-xr-x 2 root root    4096 Oct 22  2012 pt-PT
drwxr-xr-x 2 root root    4096 Oct 22  2012 qps-ploc
drwxr-xr-x 4 root root    4096 Oct 22  2012 Resources
drwxr-xr-x 2 root root    4096 Oct 22  2012 ro-RO
drwxr-xr-x 2 root root    4096 Oct 22  2012 ru-RU
drwxr-xr-x 2 root root    4096 Oct 22  2012 sk-SK
drwxr-xr-x 2 root root    4096 Oct 22  2012 sl-SI
drwxr-xr-x 2 root root    4096 Oct 22  2012 sr-Latn-CS
drwxr-xr-x 2 root root    4096 Oct 25  2013 sr-Latn-RS
drwxr-xr-x 2 root root    4096 Oct 22  2012 sv-SE
drwxr-xr-x 2 root root    4096 Oct 22  2012 tr-TR
drwxr-xr-x 2 root root    4096 Oct 22  2012 uk-UA
drwxr-xr-x 2 root root    4096 Oct 22  2012 zh-CN
drwxr-xr-x 2 root root    4096 Oct 22  2012 zh-HK
drwxr-xr-x 2 root root    4096 Oct 22  2012 zh-TW

/boot/efi/EFI/Microsoft/Boot/bg-BG:
total 152
-rwxr-xr-x 1 root root 77152 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77152 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/cs-CZ:
total 200
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/da-DK:
total 200
-rwxr-xr-x 1 root root 75616 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75616 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/de-DE:
total 208
-rwxr-xr-x 1 root root 78688 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 78688 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/el-GR:
total 208
-rwxr-xr-x 1 root root 79712 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 79712 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 46432 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/en-GB:
total 144
-rwxr-xr-x 1 root root 73568 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 73568 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/en-US:
total 192
-rwxr-xr-x 1 root root 73568 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 73568 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/es-ES:
total 200
-rwxr-xr-x 1 root root 77152 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77152 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/et-EE:
total 152
-rwxr-xr-x 1 root root 74592 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 74592 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/fi-FI:
total 200
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/Fonts:
total 13072
-rwxr-xr-x 1 root root 3694080 Jun  2  2012 chs_boot.ttf
-rwxr-xr-x 1 root root 3876772 Jun  2  2012 cht_boot.ttf
-rwxr-xr-x 1 root root 1984228 Jun  2  2012 jpn_boot.ttf
-rwxr-xr-x 1 root root 2371360 Jun  2  2012 kor_boot.ttf
-rwxr-xr-x 1 root root  168212 Jun  2  2012 malgun_boot.ttf
-rwxr-xr-x 1 root root  165764 Jun  2  2012 malgunn_boot.ttf
-rwxr-xr-x 1 root root  134508 Jun  2  2012 meiryo_boot.ttf
-rwxr-xr-x 1 root root  132888 Jun  2  2012 meiryon_boot.ttf
-rwxr-xr-x 1 root root  154896 Jun  2  2012 msjh_boot.ttf
-rwxr-xr-x 1 root root  152892 Jun  2  2012 msjhn_boot.ttf
-rwxr-xr-x 1 root root  146228 Jun  2  2012 msyh_boot.ttf
-rwxr-xr-x 1 root root  142124 Jun  2  2012 msyhn_boot.ttf
-rwxr-xr-x 1 root root   36020 Aug 22  2013 segmono_boot.ttf
-rwxr-xr-x 1 root root   77088 Aug 22  2013 segoen_slboot.ttf
-rwxr-xr-x 1 root root   77404 Aug 22  2013 segoe_slboot.ttf
-rwxr-xr-x 1 root root   47452 Aug 22  2013 wgl4_boot.ttf

/boot/efi/EFI/Microsoft/Boot/fr-FR:
total 208
-rwxr-xr-x 1 root root 78688 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 78688 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/hr-HR:
total 152
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/hu-HU:
total 208
-rwxr-xr-x 1 root root 78176 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 78176 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/it-IT:
total 200
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/ja-JP:
total 180
-rwxr-xr-x 1 root root 67424 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 67424 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42848 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/ko-KR:
total 180
-rwxr-xr-x 1 root root 66912 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 66912 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42848 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/lt-LT:
total 152
-rwxr-xr-x 1 root root 75616 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75616 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/lv-LV:
total 152
-rwxr-xr-x 1 root root 75104 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75104 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/nb-NO:
total 200
-rwxr-xr-x 1 root root 75104 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75104 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/nl-NL:
total 200
-rwxr-xr-x 1 root root 77664 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77664 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/pl-PL:
total 200
-rwxr-xr-x 1 root root 77664 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77664 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/pt-BR:
total 200
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/pt-PT:
total 200
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45920 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/qps-ploc:
total 192
-rwxr-xr-x 1 root root 73568 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 73568 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/Resources:
total 28
-rwxr-xr-x 1 root root 18272 Aug 22  2013 bootres.dll
drwxr-xr-x 2 root root  4096 Oct 22  2012 en-US
drwxr-xr-x 2 root root  4096 Oct 22  2012 fr-FR

/boot/efi/EFI/Microsoft/Boot/Resources/en-US:
total 12
-rwxr-xr-x 1 root root 11616 Aug 22  2013 bootres.dll.mui

/boot/efi/EFI/Microsoft/Boot/Resources/fr-FR:
total 12
-rwxr-xr-x 1 root root 11504 Aug  1  2012 bootres.dll.mui

/boot/efi/EFI/Microsoft/Boot/ro-RO:
total 152
-rwxr-xr-x 1 root root 75616 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75616 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/ru-RU:
total 196
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 44896 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/sk-SK:
total 152
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sl-SI:
total 152
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sr-Latn-CS:
total 152
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sr-Latn-RS:
total 152
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sv-SE:
total 200
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76128 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/tr-TR:
total 200
-rwxr-xr-x 1 root root 75104 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75104 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45408 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/uk-UA:
total 152
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76640 Aug 22  2013 bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/zh-CN:
total 172
-rwxr-xr-x 1 root root 63840 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 63840 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42336 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/zh-HK:
total 172
-rwxr-xr-x 1 root root 63832 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 63840 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42336 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/zh-TW:
total 172
-rwxr-xr-x 1 root root 63840 Aug 22  2013 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 63840 Aug 22  2013 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42336 Aug 22  2013 memtest.efi.mui

/boot/efi/EFI/toshiba:
total 4
drwxr-xr-x 39 root root 4096 Oct 22  2012 Boot

/boot/efi/EFI/toshiba/Boot:
total 4148
-rwxr-xr-x 1 root root   28672 Oct 22  2012 BCD
-rwxr-xr-x 1 root root   20480 Oct 22  2012 BCD.LOG
-rwxr-xr-x 1 root root       0 Oct 22  2012 BCD.LOG1
-rwxr-xr-x 1 root root       0 Oct 22  2012 BCD.LOG2
drwxr-xr-x 2 root root    4096 Oct 22  2012 bg-BG
-rwxr-xr-x 1 root root 1354480 Jul 25  2012 bootmgfw.efi
-rwxr-xr-x 1 root root 1350896 Jul 25  2012 bootmgr.efi
-rwxr-xr-x 1 root root   65536 Oct 22  2012 BOOTSTAT.DAT
-rwxr-xr-x 1 root root    4186 Jun 26  2012 boot.stl
drwxr-xr-x 2 root root    4096 Oct 22  2012 cs-CZ
drwxr-xr-x 2 root root    4096 Oct 22  2012 da-DK
drwxr-xr-x 2 root root    4096 Oct 22  2012 de-DE
drwxr-xr-x 2 root root    4096 Oct 22  2012 el-GR
drwxr-xr-x 2 root root    4096 Oct 22  2012 en-GB
drwxr-xr-x 2 root root    4096 Oct 22  2012 en-US
drwxr-xr-x 2 root root    4096 Oct 22  2012 es-ES
drwxr-xr-x 2 root root    4096 Oct 22  2012 et-EE
drwxr-xr-x 2 root root    4096 Oct 22  2012 fi-FI
drwxr-xr-x 2 root root    4096 Oct 22  2012 Fonts
drwxr-xr-x 2 root root    4096 Oct 22  2012 fr-FR
drwxr-xr-x 2 root root    4096 Oct 22  2012 hr-HR
drwxr-xr-x 2 root root    4096 Oct 22  2012 hu-HU
drwxr-xr-x 2 root root    4096 Oct 22  2012 it-IT
drwxr-xr-x 2 root root    4096 Oct 22  2012 ja-JP
drwxr-xr-x 2 root root    4096 Oct 22  2012 ko-KR
drwxr-xr-x 2 root root    4096 Oct 22  2012 lt-LT
drwxr-xr-x 2 root root    4096 Oct 22  2012 lv-LV
-rwxr-xr-x 1 root root 1263856 Jul 25  2012 memtest.efi
drwxr-xr-x 2 root root    4096 Oct 22  2012 nb-NO
drwxr-xr-x 2 root root    4096 Oct 22  2012 nl-NL
drwxr-xr-x 2 root root    4096 Oct 22  2012 pl-PL
drwxr-xr-x 2 root root    4096 Oct 22  2012 pt-BR
drwxr-xr-x 2 root root    4096 Oct 22  2012 pt-PT
drwxr-xr-x 2 root root    4096 Oct 22  2012 qps-ploc
drwxr-xr-x 4 root root    4096 Oct 22  2012 Resources
drwxr-xr-x 2 root root    4096 Oct 22  2012 ro-RO
drwxr-xr-x 2 root root    4096 Oct 22  2012 ru-RU
drwxr-xr-x 2 root root    4096 Oct 22  2012 sk-SK
drwxr-xr-x 2 root root    4096 Oct 22  2012 sl-SI
drwxr-xr-x 2 root root    4096 Oct 22  2012 sr-Latn-CS
drwxr-xr-x 2 root root    4096 Oct 22  2012 sv-SE
drwxr-xr-x 2 root root    4096 Oct 22  2012 tr-TR
drwxr-xr-x 2 root root    4096 Oct 22  2012 uk-UA
drwxr-xr-x 2 root root    4096 Oct 22  2012 zh-CN
drwxr-xr-x 2 root root    4096 Oct 22  2012 zh-HK
drwxr-xr-x 2 root root    4096 Oct 22  2012 zh-TW

/boot/efi/EFI/toshiba/Boot/bg-BG:
total 152
-rwxr-xr-x 1 root root 77040 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77040 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/cs-CZ:
total 200
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/da-DK:
total 200
-rwxr-xr-x 1 root root 75504 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75504 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/de-DE:
total 208
-rwxr-xr-x 1 root root 78576 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 78576 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/el-GR:
total 208
-rwxr-xr-x 1 root root 79600 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 79600 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 46320 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/en-GB:
total 144
-rwxr-xr-x 1 root root 73456 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 73456 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/en-US:
total 192
-rwxr-xr-x 1 root root 73456 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 73456 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/es-ES:
total 200
-rwxr-xr-x 1 root root 77040 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77040 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/et-EE:
total 152
-rwxr-xr-x 1 root root 74480 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 74480 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/fi-FI:
total 200
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/Fonts:
total 13072
-rwxr-xr-x 1 root root 3694080 Jun  2  2012 chs_boot.ttf
-rwxr-xr-x 1 root root 3876772 Jun  2  2012 cht_boot.ttf
-rwxr-xr-x 1 root root 1984228 Jun  2  2012 jpn_boot.ttf
-rwxr-xr-x 1 root root 2371360 Jun  2  2012 kor_boot.ttf
-rwxr-xr-x 1 root root  168212 Jun  2  2012 malgun_boot.ttf
-rwxr-xr-x 1 root root  165764 Jun  2  2012 malgunn_boot.ttf
-rwxr-xr-x 1 root root  134508 Jun  2  2012 meiryo_boot.ttf
-rwxr-xr-x 1 root root  132888 Jun  2  2012 meiryon_boot.ttf
-rwxr-xr-x 1 root root  154896 Jun  2  2012 msjh_boot.ttf
-rwxr-xr-x 1 root root  152892 Jun  2  2012 msjhn_boot.ttf
-rwxr-xr-x 1 root root  146228 Jun  2  2012 msyh_boot.ttf
-rwxr-xr-x 1 root root  142124 Jun  2  2012 msyhn_boot.ttf
-rwxr-xr-x 1 root root   36020 Jun  2  2012 segmono_boot.ttf
-rwxr-xr-x 1 root root   77088 Jun  2  2012 segoen_slboot.ttf
-rwxr-xr-x 1 root root   77404 Jun  2  2012 segoe_slboot.ttf
-rwxr-xr-x 1 root root   47452 Jun  2  2012 wgl4_boot.ttf

/boot/efi/EFI/toshiba/Boot/fr-FR:
total 208
-rwxr-xr-x 1 root root 78576 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 78576 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/hr-HR:
total 152
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/hu-HU:
total 208
-rwxr-xr-x 1 root root 78064 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 78064 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/it-IT:
total 200
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/ja-JP:
total 180
-rwxr-xr-x 1 root root 67312 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 67312 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42736 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/ko-KR:
total 180
-rwxr-xr-x 1 root root 66800 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 66800 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42736 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/lt-LT:
total 152
-rwxr-xr-x 1 root root 75504 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75504 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/lv-LV:
total 152
-rwxr-xr-x 1 root root 74992 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 74992 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/nb-NO:
total 200
-rwxr-xr-x 1 root root 74992 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 74984 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/nl-NL:
total 200
-rwxr-xr-x 1 root root 77552 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77552 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/pl-PL:
total 200
-rwxr-xr-x 1 root root 77552 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 77552 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/pt-BR:
total 200
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/pt-PT:
total 200
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45808 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/qps-ploc:
total 192
-rwxr-xr-x 1 root root 73456 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 73456 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/Resources:
total 28
-rwxr-xr-x 1 root root 18160 Jul 25  2012 bootres.dll
drwxr-xr-x 2 root root  4096 Oct 22  2012 en-US
drwxr-xr-x 2 root root  4096 Oct 22  2012 fr-FR

/boot/efi/EFI/toshiba/Boot/Resources/en-US:
total 12
-rwxr-xr-x 1 root root 11504 Jul 25  2012 bootres.dll.mui

/boot/efi/EFI/toshiba/Boot/Resources/fr-FR:
total 12
-rwxr-xr-x 1 root root 11504 Aug  1  2012 bootres.dll.mui

/boot/efi/EFI/toshiba/Boot/ro-RO:
total 152
-rwxr-xr-x 1 root root 75504 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 75504 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/ru-RU:
total 196
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 44784 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/sk-SK:
total 152
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/sl-SI:
total 152
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/sr-Latn-CS:
total 152
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/sv-SE:
total 200
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76016 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/tr-TR:
total 200
-rwxr-xr-x 1 root root 74992 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 74992 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 45296 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/uk-UA:
total 152
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 76528 Jul 25  2012 bootmgr.efi.mui

/boot/efi/EFI/toshiba/Boot/zh-CN:
total 172
-rwxr-xr-x 1 root root 63728 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 63728 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42224 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/zh-HK:
total 172
-rwxr-xr-x 1 root root 63728 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 63728 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42224 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/toshiba/Boot/zh-TW:
total 172
-rwxr-xr-x 1 root root 63728 Jul 25  2012 bootmgfw.efi.mui
-rwxr-xr-x 1 root root 63728 Jul 25  2012 bootmgr.efi.mui
-rwxr-xr-x 1 root root 42224 Jul 25  2012 memtest.efi.mui

/boot/efi/EFI/ubuntu:
total 2600
-rwxr-xr-x 1 root root     126 May  1 11:07 grub.cfg
-rwxr-xr-x 1 root root  119296 May  2 16:17 grubx64.efi
-rwxr-xr-x 1 root root 1178240 May  1 11:07 MokManager.efi
-rwxr-xr-x 1 root root 1355736 May  1 11:07 shimx64.efi

/boot/efi/grub:
total 4
-rwxr-xr-x 1 root root 3751 Apr 25 13:25 grub.cfg


```

---

### Post by oldfred on 2014-05-02
I am running out of ideas.

Can you boot with Supergrub. It bypasses the installed and just boots, not sure how well with UEFI versions. It did find all my BIOS installs.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Or from Boot-Repair advanced mode uninstall/purge grub and totally reinstall grub-efi.
If you can boot with Supergrub you can do the same uninstall/purge & reinstall from inside your install.

And it may need the purge and possibly some other manual deletion of grub files or folders. It may be some conflict between left over old version that did not totally get overwritten with new version. 

All my notes are for grub-pc, I think you an just use grub-efi in place of grub-pc in these instructions if you do boot into your system.

 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by tobanw on 2014-05-02
OK, I'll try supergrub. In the meantime, I added some more diagnostics to my last post. I noticed a linux mint entry in the efi directory; I wonder if that's causing trouble as you hinted at.

---

### Post by oldfred on 2014-05-02
I think the Windows sub-directories are all the various languages it supports. Windows needs bootmgfw.efi and BCD.

Ubuntu uses grubx64.efi or shimx64.efi and grub.cfg.

Some copy grub or shim to the Boot directory to replace bootx64.efi and then boot hard drive not other entries instead of UEFI shell.
       [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.

 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

Out of curiosity what is in the grub.cfg files? If not using Mint you can just delete that folder in the efi partition. But I doubt if that is the issue. I might fully backup efi partition before making any changes.

---

### Post by tobanw on 2014-05-02
```
ubuntu@ubuntu:/mnt/boot/efi/EFI/ubuntu$ cat grub.cfg
search.fs_uuid 0aa66c1e-127c-44cc-9c2e-9609f94742cb root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by oldfred on 2014-05-02
Am I looking at the correct pastebin for you? This UUID does not match?
/dev/sda6        4acd1e08-8d71-424c-8a98-353007d892e7   ext4

---

### Post by tobanw on 2014-05-02
OK, I see that in my first paste. In my second paste (also in my original post, but the link was wrong--I just fixed it), there are no instances of that UID, and sda6 is listed as

```
/dev/sda6        0aa66c1e-127c-44cc-9c2e-9609f94742cb   ext4
```

In my latest [http://paste.ubuntu.com/7381784/](http://paste.ubuntu.com/7381784/) it has the same UID for sda6, but also has 2 mentions of it on lines 233,235 which is the source of sda2/grub/grub.cfg.

While reinstalling 14.04, **I did expand sda6 and shrink sda7, hence it got a new UID** and grub seems to be looking for the old ID and throwing the 'no such device' error.

---

### Post by oldfred on 2014-05-02
Usually changing partition sizes does not change UUID, but deleting & recreating them will.
Change grub.cfg to have correct UUIDs.

---

### Post by tobanw on 2014-05-03
I tried installing supergrubdisk to a usb stick, but it won't boot: I can see the device in the boot menu when I press F12, but it just goes to grub rescue. The usb stick seems to work fine otherwise. I'm gonna try making it again using a friend's windows pc later on today.

I corrected the UUID's in /sda2/grub/grub.cfg, but it still goes to grub rescue with the 'no such device: 4acd1e...' error. I searched the efi directory for "4acd1e..." :
```
ubuntu@ubuntu:/mnt/boot/efi/EFI$ grep -r "4acd1e" ./*
Binary file ./Boot/bootx64.efi matches
```
I wonder if the problem lies in this binary file. I'm gonna look into what you suggested: replacing bootx64.efi with grubx64.efi.

I tried this, but it didn't work: [http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

I tried reinstalling again, but that didn't help. I noticed that it  changed the UUIDs again, and I did not change any partitions this time.

Ran boot-repair after that: [http://paste2.org/d3Ea0cV5](http://paste2.org/d3Ea0cV5) . Still finishes with an error.

---

### Post by tobanw on 2014-05-03
I got it! In /dev/sda2/EFI, I copied the contents of the 'ubuntu' directory into the 'Boot' directory as outlined here: [http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470). Then I deleted bootx64.efi and renamed grubx64.efi as bootx64.efi. System booted up into grub. Thanks so much oldfred!

Should I run "dpkg-reconfigure grub-efi-amd64" to configure it properly for the next update? Or boot-repair? I worry that I'll have boot problems when I next update.

---

### Post by oldfred on 2014-05-03
Glad you figured out something that worked. You might want to add that to grub bug report as a valid work around.
All this has been just suggestions on my part, as I really did not know.

Does this work with grub-efi or grub-efi-amd64?

these are the grub-pc commands
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc

This shows boot partition on my BIOS install:
 sudo grub-probe -t device /boot/grub

---

### Post by tobanw on 2014-05-03
Have a look. Should I run dpkg-reconfigure grub-efi-amd64 now?

```
toban@shiba:~$ sudo debconf-show grub-pc
[sudo] password for toban: 
  grub-pc/partition_description:
  grub2/kfreebsd_cmdline:
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/disk_description:
  grub-pc/kopt_extracted: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/hidden_timeout: true
  grub2/device_map_regenerated:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/linux_cmdline_default: quiet splash
  grub2/linux_cmdline:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices:
  grub-pc/timeout: 10
  grub-pc/postrm_purge_boot_grub: false


toban@shiba:~$ sudo debconf-show grub-efi


toban@shiba:~$ sudo debconf-show grub-efi-amd64
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/linux_cmdline_default: quiet splash
  grub2/linux_cmdline:


toban@shiba:~$ dpkg-query -l 'grub*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
un  grub                    <none>           <none>           (no description available)
ii  grub-common             2.02~beta2-9     amd64            GRand Unified Bootloader (common files)
un  grub-coreboot           <none>           <none>           (no description available)
un  grub-doc                <none>           <none>           (no description available)
un  grub-efi                <none>           <none>           (no description available)
ii  grub-efi-amd64          2.02~beta2-9     amd64            GRand Unified Bootloader, version 2 (EFI-AMD64 vers
ii  grub-efi-amd64-bin      2.02~beta2-9     amd64            GRand Unified Bootloader, version 2 (EFI-AMD64 bina
un  grub-efi-ia32           <none>           <none>           (no description available)
un  grub-efi-ia64           <none>           <none>           (no description available)
un  grub-emu                <none>           <none>           (no description available)
un  grub-ieee1275           <none>           <none>           (no description available)
un  grub-legacy             <none>           <none>           (no description available)
un  grub-legacy-doc         <none>           <none>           (no description available)
un  grub-linuxbios          <none>           <none>           (no description available)
un  grub-pc                 <none>           <none>           (no description available)
un  grub-xen                <none>           <none>           (no description available)
un  grub-yeeloong           <none>           <none>           (no description available)
un  grub2                   <none>           <none>           (no description available)
ii  grub2-common            2.02~beta2-9     amd64            GRand Unified Bootloader (common files for version 

toban@shiba:~$ sudo grub-probe -t device /boot/grub
/dev/sda6

```

---

### Post by oldfred on 2014-05-03
On my BIOS based system it shows this which is my hard drive with grub in the MBR:
* grub-pc/install_devices: /dev/disk/by-id/ata-SSD_G2_series_64GB_10000000000000000251

First I am surprised the command with grub-pc worked since you are UEFI.
Second it is not showing where. 
And I have seen several UEFI installs with multiple hard drives and an efi partition on each drive. So then how is grub knowing which drive to use to reinstall? Or is it just the fstab entry on /boot/efi?

So then with UEFI the dpkg reconfig may not have anything to reset?
If it was me I would try it as I want to understand things, but it is up to you.

---

### Post by tobanw on 2014-05-03
'dpkg-reconfigure grub-efi-amd64' ran smoothly and my system still boots. Looks like I'm in the clear now; maybe next time I'll wait a bit longer before upgrading in case of bugs.

---

