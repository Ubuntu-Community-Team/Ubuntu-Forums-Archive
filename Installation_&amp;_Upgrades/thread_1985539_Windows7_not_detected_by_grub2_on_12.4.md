---
title: "Windows7 not detected by grub2 on 12.4"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by lostinspace2011 on 2012-05-23
I just did a fresh installation of Windows7 and Ubuntu 12.4 on a new GPT drive. First I installed Windows which created 3 partitions as shown below.

Then I installed Ubuntu 12.4 (64bit) and created a further 3 partitions:

```
Disk /dev/sdc: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A4063C92-5D8B-4689-B3C4-D7C2F24AEC1A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       409602047   195.1 GiB   0700  Basic data partition
   4       409602048       410126335   256.0 MiB   8300  Linux filesystem
   5       410126336       418514943   4.0 GiB     8200  Linux swap
   6       418514944       976773134   266.2 GiB   0700  Linux filesystem
```The update-grub scripts seems to be calling the os-prober command, however this does not detect the Windows installation. I tried adding the configuration to grub2 manually, however this didn't work either.

I added this to /etc/grub.d/20_windows7

```
#! /bin/sh -e

cat << EOF
menuentry "Microsoft Windows 7 Professional 2/2" {
set root=(hd2,2)
chainloader +1
}

menuentry "Microsoft Windows 7 Professional 2/3" {
set root=(hd2,3)
chainloader +1
}
EOF
```Any pointers on what I can do this fix this ? Are there any command I can run to get grub2 to auto-detect the Windows installation ?

---

### Post by darkod on 2012-05-23
I think EFI boot is still little bit tricky to do on dual boot.

This post by oldfred can give you lots of info:
[http://ubuntuforums.org/showpost.php?p=11509699&postcount=2](http://ubuntuforums.org/showpost.php?p=11509699&postcount=2)

I haven't used EFI personally.

---

### Post by oldfred on 2012-05-23
With UEFI you are not really supposed to chain load like with the old BIOS/MBR configuration.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
> Since each OS or vendor can maintain its own files within the EFI  SYSTEM PARTITION without affecting the other, multi-booting using UEFI  is just a matter of launching a different UEFI application corresponding  to the particular OS's bootloader. This removes the need for relying on  chainloading mechanisms of one bootloader to load another to switch  OSes. 
 ** **



Someone posted this on how to rename your boot menu item, but each UEFI vendors' implementation seems to be different.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


---

### Post by darkod on 2012-05-23
I forgot to mention, don't forget to confirm the windows efi files are on the EFI partition at all.

If I've got it correctly, one bug in grub2 and EFI dual boot was to overwrite the windows boot files. Without them you wouldn't be able to boot windows I guess.

---

### Post by lostinspace2011 on 2012-05-25
I am not trying to chainload with EFI. What I was trying to  do is to chainload Windows directly and keep EFI out of the equation. Right now however EFI is the only working option of booting windows.

Also for some strange reason Windows seems to have overwritten the grub boot loader as I no longer able to boot Ubuntu. Grub doesn't even load. Is it possible what Windows would do this. It also seems that Windows wants to be the first option in my BIOS boot order. From time to time it changes the order and placed Windows first. This may be related to the installation of updates.

---

### Post by oldfred on 2012-05-26
If you do not want UEFI, you cannot have gpt partitioning and still use Windows. Ubuntu does not care. I use gpt with BIOS without any issue.

Windows only boots from gpt drives in UEFI mode. So if you want to boot in BIOS/MBR with Windows you have to totally reformat totally to MBR(msdos) and select to install in BIOS,  AHCI or legacy depending on what your version calls it.

You should get something like this, not sure if grub or ubuntu in your efi partition.

find /boot/efi -name "*efi"
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

Someone also posted this from their verison:

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 



---

