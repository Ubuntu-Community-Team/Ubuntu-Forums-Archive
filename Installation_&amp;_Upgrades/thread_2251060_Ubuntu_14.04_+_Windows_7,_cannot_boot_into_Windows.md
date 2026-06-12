---
title: "Ubuntu 14.04 + Windows 7, cannot boot into Windows"
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by dunn-stephen on 2014-11-01
I have spent a day trying every suggestion I can find and using the ArchWiki tutorial. No luck. Here's the situation:


I have Ubuntu 14.04 LTS installed on `/dev/sdb` (installed first). I have Windows 7 installed onto `/dev/sda` (installed 2nd from a USB stick). `/dev/sda1` contains the "SYSTEM_RESERVED" 100mb partition. `/dev/sda2` contains Windows. Grub cannot identify Windows 7, and I cannot get a chainloader to work. 


Here is what I've tried:


1. boot-repair (I get an error `"No GPT detected, install a small bios partition..."` which I did with gparted and still had no luck, even after flagging bios_grub and it being detected.)
2. `sudo os-prober; sudo update-grub;` (also sudo update-grub2)
3. Adding manual entries to `/etc/grub.d/40_custom` (many many variations):

```

        if [ "${grub_platform}" == "efi" ]; then
           menuentry "Microsoft Windows Vista/7/8/8.1 UEFI-GPT" {
           insmod part_gpt
           insmod chain
           set root='(hd0,gpt5)'
           chainloader /EFI/Microsoft/Boot/bootmgfw.efi
          }
        fi

```

I have tried `chainloader +1`, many insmod variants, etc. Essentially I always get `"file not found"` or `"command not found"` or `"EFI not found"` no matter what path I try. (So yes, I can see the Microsoft Windows entry when I boot into grub.)


It might also help to know that when I start the computer, it says `"Press F2 to enter UEFI BIOS Setup"`.

```

 sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL


    NAME   FSTYPE   SIZE MOUNTPOINT    LABEL
    sda           232.9G               
    &#9500;&#9472;sda1 ntfs     100M               System Reserved
    &#9492;&#9472;sda2 ntfs   232.8G               
    sdb           111.8G               
    &#9500;&#9472;sdb1 vfat      94M /boot/efi     
    &#9492;&#9472;sdb2 ext4   111.7G /             
    sdc           931.5G               
    &#9492;&#9472;sdc1 ext4   931.5G /media/backup Backup
    sdd             1.4T               
    &#9492;&#9472;sdd1 ntfs     1.4T               BigDunn

```


Could someone please give me a simple explanation of what's going on and how to fix it?

---

### Post by yancek on 2014-11-01
You have an efi partition on sdb1, the Ubuntu drive.  Do you see any windows boot files there?  Did you install Ubuntu using UEFI/GPT and windows in MBR?  They both need to be the same.  It would probably help if you posted the output from boot repair.  There is an option for it to create a file with the actions performed somewhere.  I don't use it myself but others here may be able to explain exactly how to do that.

---

### Post by oldfred on 2014-11-02
yancek is correct.

UEFI and BIOS are not really compatible. 
You can only dual boot from UEFI menu and may have to change UEFI/CSM settings to turn on/off UEFI or BIOS/CSM boot mode before selecting which system to boot. Some will auto switch and let you boot from the one time boot key like f12 or f10 but varies by vendor. 

Generally better to have both systems boot in UEFI mode or both in BIOS mode. But Ubuntu will boot from a gpt partitioned drive in either UEFI or BIOS boot mode if you have correct supporting partitions. You have to have an efi partition for UEFI boot or a bios_grub partition for BIOS boot. If you have both partitions, Boot-Repair can convert your UEFI install to BIOS or vice-versa. It uninstalls grub-pc (BIOS) and installs grub-efi-amd64 (UEFI).

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

