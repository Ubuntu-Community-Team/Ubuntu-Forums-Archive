---
title: "EFI Booting not Automatic"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by hatcher-hobby on 2014-08-28
I am currently using elementaryOS (ubuntu 12.04 base) as my primary distro. I have been trouble free for some time but have had to use F9 to boot the system since I first installed the OS. If I do not use F9 to boot from a EFI file, the system will find nothing and reboot  in a loop. I have secure boot disabled, EFI with CSM enabled in BIOS and legacy disabled as well. I have attempted to update grub numerous times but nothing has fixed the issue.

I now ask for help from the community.

Thanks

---

### Post by ubfan1 on 2014-08-28
What output do you get from  sudo efibootmgr -v    ?
That should list the boot order list, and the bootloader paths.
Usually, something will be obviously wrong, but you could add a "fallback" bootloader (grubx64.efi with non-secure boot) to /EFI/Boot/bootx64.efi.    Thats grubx64.efi renamed as bootx64.efi.  The grub.cfg file may stay in /EFI/ubuntu.  This bootx64.efi is the removable media bootloader, but is sometimes tried when other failures occur.

---

### Post by hatcher-hobby on 2014-08-28
running sudo efibootmge -v gives me 

```
BootCurrent: 0000
Timeout: 5 seconds
```

My current boot folder structure is laid out as follows
/boot/
/boot/grub/
/boot/efi/EFI/elementary/grubx64.efi

Since the cmd didnt list anything, Im gonna assume something is wrong.

---

### Post by fantab on 2014-08-28
> ...EFI with CSM enabled in BIOS and legacy disabled as well

AFAIK CSM and legacy modes are same.
If CSM is enabled then EFI boot is not possible... hence you have to use f9.
Post the ***Bootinfo summary*** which [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool creates... just note down the url to the file and post it here.

---

### Post by hatcher-hobby on 2014-08-28
As you requested good sir...

[http://paste2.org/L5KDwxjI](http://paste2.org/L5KDwxjI)

---

### Post by ubfan1 on 2014-08-28
Looks like you are in UEFI mode,since there is no MBR, but you don't seem to have any bootloaders to try loaded into nvram.  What machine do you have?  Some are critically short of nvram, and might have failed to add the paths.  efibootmgr has the capability to add a bootloader, and to adjust the boot order.  I've never done it myself, but just read the man pages (man efibootmgr).  However, if the nvram is lacking, maybe that won't work.  First, I'd suggest copying the grubx64.efi bootloader to the bootx64 like:
sudo cp /boot/efi/EFI/elementary/grubx64.efi /boot/EFI/Boot/bootx64.efi
Now it just might boot, or at least get into grub.  If you get into grub, but don't get a menu, just a command line, you are probably missing the grub.cfg file in the EFI partition.  Usually, that's in /EFI/ubuntu/grub.cfg, and grubx64.efi will find it from wherever it is run, but don't know about elementary OS.  Anyway, the grub.cfg file there is just a 3 liner which brings in the grub.cfg from /boot/grub/grub.cfg.  Here's what it should look like:
search.fs_uuid ec133adb-6cbd-4be0-b108-adcf846a855c root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

Try that, it doesn't take any nvram at all, and if it fails, then try the efibootmgr to add the grubx64.efi boot entry.

---

### Post by LostFarmer on 2014-08-28
to add efi path to the comps nvram: 
```
sudo efibootmgr -c -d /dev/sda -p 1 -w -L  elementary -l /efi/elementary/grubx64.efi
``` NOTE: -p** 1**  -w ==1 is ONE ,**  -i** /efi/== -i is a small L



after you do that post
```
sudo efibootmgr -v
``` 

Will likely need to set the elementary entry active and put it as first boot entry, but need it entry number first.

[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by fantab on 2014-08-28
> **hatcher-hobby said:**
> As you requested good sir...

[http://paste2.org/L5KDwxjI](http://paste2.org/L5KDwxjI)


```
parted -l: 
Model: ATA MKNSSDAT240GB (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
 
Number  Start   End     Size    File system     Name  Flags
1      1049kB  99.6MB  98.6MB  fat32                 boot
2      99.6MB  223GB   223GB   ext4                  **msftdata**

3      223GB   240GB   17.0GB  linux-swap(v1)


```

Firstly, using Gparted remove 'msftdata' flag from the second or /dev/sda2 ext4 partition. 
'msftdata'=microsoftdata, but since its a Linux it should not be on Ext4 partition.

Shut down and reboot from HDD. Tell us if Ubuntu boots.
Run Boot-Repiar if you cannot boot.
Make sure the Ubuntu DVD/USB boots in EFI mode to run boot-repair: See [HERE]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").

---

### Post by hatcher-hobby on 2014-08-29
Alright, so I tried the suggested solutions such as adding the .efi file using efibootmgr cmd as well as removing the msftdata flag for my ext4 partition.
I tried to create a few different paths to the nvram but nothing worked.

I am at a loss still.

---

### Post by LostFarmer on 2014-08-29
post output of " sudo efibootmgr -v "

---

