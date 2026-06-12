---
title: "Grub dual boot problem with the nvme"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by digitall2 on 2018-05-13
Hi,

[COLOR=#000000][FONT=Verdana]My problem is related to installation to an SSD rather that normal HD. It results instead os SDA to "nvme".[/FONT][/COLOR]
I have read and read and tried different setups but have no clue how to fix it. 
I have done in the past dual boot of Ubuntu and Kodi (OpenELEC and LibreELEC) but now since I have a new system that has a M2 SSD Samsung EVO960 I have a hell of the problems.
I have done the Ubuntu 16 installation from a USB stick with no problems. I have repartitioned the drive accordingly and set the proper boot flag.
I have installed grub customizer and my problem is to properly boot from grub menu in Kodi

In the past, or on a normal drive, it was SDA, SDB, and so on but with the SSD there "nvme0n1, nvme0n1p1, nvme0n1p2, etc. This screws things up for me in custom40 file. Here is what I did and what I got:
```
htpc@htpc:~$ sudo blkid -c /dev/null -o list
device                        fs_type     label        mount point                       UUID
------------------------------------------------------------------------------------------------------------------------------
/dev/loop0                    squashfs                 /snap/core/4571                   
/dev/nvme0n1                                           (in use)                          
/dev/nvme0n1p1                vfat                     /boot/efi                         633C-3EBA
/dev/nvme0n1p2                ext4                     /                                 85fb1049-5c04-4c50-ac8b-3c552dcda936
/dev/nvme0n1p3                ext4        LibreELEC    (not mounted)                     c532fde5-0eeb-454c-8459-008f9fb64253
/dev/nvme0n1p4                ext4        LibreSYS     (not mounted)                     8449179d-34df-4d19-b63d-1247b4bef996

```

and

```
htpc@htpc:~$ lsblk -o name,label,partlabel,size,uuid,mountpoint
NAME        LABEL     PARTLABEL              SIZE UUID                                 MOUNTPOINT
loop0                                       86.6M                                      /snap/core/4571
nvme0n1                                    232.9G                                      
&#9500;&#9472;nvme0n1p3 LibreELEC LibreELEC            207.6G c532fde5-0eeb-454c-8459-008f9fb64253 
&#9500;&#9472;nvme0n1p1           EFI System Partition   512M 633C-3EBA                            /boot/efi
&#9500;&#9472;nvme0n1p4 LibreSYS  LibreSYS                 3G 8449179d-34df-4d19-b63d-1247b4bef996 
&#9492;&#9472;nvme0n1p2                                 21.9G 85fb1049-5c04-4c50-ac8b-3c552dcda936 /

```

My custom40 file it looks like this but it was much longer since I have tried a lot of things. Something is wrong and someone knowledgeable probably will see my mistake immediately. Sometime in first variant1 it boots but most of the times it says "hd0,4 not found". Based on the info above what should I write in the custom40 file please?
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Entertainment System1" {
  set root=(hd0,4)
  linux /KERNEL boot=/dev/nvme0n1p4 disk=/dev/nvme0n1p3 quiet
}


menuentry "Entertainment System6" {
    search --file --no-floppy --set root=633C-3EBA
    chainloader (${root})/efi/bootx64.efi
    linux /KERNEL boot=/dev/nvme0n1p4 disk=/dev/nvme0n1p3 quiet
}


menuentry "Entertainment System7" {
    search --file --no-floppy --set root=633C-3EBA
    chainloader (${root})/boot/efi/bootx64.efi
    linux /KERNEL boot=/dev/nvme0n1p4 disk=/dev/nvme0n1p3 quiet
}


menuentry "Entertainment System8" {
    set root=UUID=633C-3EBA
    chainloader (${root})/boot/efi/bootx64.efi
    linux /KERNEL boot=/dev/nvme0n1p4 disk=/dev/nvme0n1p3 quiet
}


menuentry "Entertainment System9" {
    search --set=root --LABEL LibreSYS --hint hd0,4
    linux /KERNEL boot=LABEL=LibreSYS disk=LABEL=LibreELEC
}


menuentry "Entertainment System10" {
    search --set=root --LABEL=LibreSYS --hint hd0,4
    linux /KERNEL boot=LABEL=LibreSYS disk=LABEL=LibreELEC
}


menuentry "Entertainment System12" {
    set root=633C-3EBA
    linux /KERNEL boot=UUID=8449179d-34df-4d19-b63d-1247b4bef996 disk=UUID=c532fde5-0eeb-454c-8459-008f9fb64253
}


menuentry "Entertainment System21" {
  set root=(nvme0n1,nvme0n1p3)
  linux /KERNEL boot=UUID=8449179d-34df-4d19-b63d-1247b4bef996 disk=UUID=c532fde5-0eeb-454c-8459-008f9fb64253
}


menuentry "Entertainment System22" {
  set root=(nvme0n1,nvme0n1p3)
  linux /KERNEL boot=/dev/nvme0n1p4 disk=/dev/nvme0n1p3 quiet
}


menuentry "Entertainment System23" {
  set root=(nvme0n1p1,nvme0n1p3)
  linux /KERNEL boot=/dev/nvme0n1p4 disk=/dev/nvme0n1p3 quiet
}



```

---

### Post by oldfred on 2018-05-13
Is Kodi also UEFI?
UEFI and BIOS are not compatible. Once you start booting in one boot mode, you cannot change. Or grub can only boot other systems in same boot mode.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You can also use a configfile type entry to load another grub (Still has to be same boot mode).

```
menuentry "Bionic 18.04 on sda7 configfile" {
configfile (hd0,gpt7)/boot/grub/grub.cfg 
}

```

Or you can use the configfile like in the ESP - efi system partition which uses UUID with root specified to help find UUID.
 
```
#search.fs_uuid 8809a2ba-e6e3-4caa-9786-aa3901bfdd36 root hd1,gpt10 
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt7
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
 
```

I did a second install to sdb, but it overwrote my default install in sda, so commented out first line and added back second line. I have learned to backup ESP & particularly /EFI/ubuntu folder.

---

### Post by digitall2 on 2018-05-13
Thanks "oldfred"
I do not think kodi is uefi and have no clue how to do it. Perhaps is better to install Ubuntu in legacy, without uefi, the same Kodi and it may work but I would still have no idea what to put instead of SDA and how to use the "nvme"

You wrote: "[COLOR=#000000]Or you can use the configfile like in the ESP - efi system partition which uses UUID with root specified to help find UUID."
But in my above commands and responds there are all UUID's and tried in the custom40 file but still doesn't work.[/COLOR]

---

### Post by oldfred on 2018-05-13
If Kodi not UEFI, then nothing in grub will boot it.
UEFI & BIOS write system info differently onto the hard drive for the operating system to use. 

You should be able to boot directly from UEFI boot menu. Some systems may require you to turn on/off UEFI/BIOS boot mode to match way you want to boot. Kodi would have to have its BIOS boot loader in the MBR and Ubuntu its UEFI boot loader in ESP. And if BIOS boot loader on gpt partitioned drive, you must have a bios_grub partition for grub to correctly install. UEFI on gpt has to have the ESP.

---

### Post by monkeybrain20122 on 2018-05-13
You are making life unnecessarily complicated. Instead of dualbooting with kodi and messing with uefi and grub all you need is Ubuntu, then install kodi inside Ubuntu from the repo or the ppa, then it will create an entry in GDM/lightdm where you can choose to login to a kodi session or ubuntu session when you reboot. To switch from Ubuntu to Kodi and vice versa you just need to logout and login again, no reboot necessary.

Moreover openelec and librelelec don't have great hardware support, mouse clicks are not supported for many hardware and you are told to navigate with the keyboard (no joke). Installing kodi in Ubuntu and then switch to kodi session has none of the hardware problems because it has the driver support of the Ubuntu system including proprietary graphic driver (if you use any)

---

