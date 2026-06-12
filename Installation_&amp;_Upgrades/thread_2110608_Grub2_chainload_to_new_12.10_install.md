---
title: "Grub2 chainload to new 12.10 install"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by ZepTepi on 2013-01-30
I have been using Debian for years and have "squeeze" working on a system with 6 physical hard drives using grub2 as loader.

I changed BIOS to have hd5 as boot drive and installed 12.10 using several partitions. ( This is the way I have installed for many years so I am very familiar with partitioning etc ) 

When procedure came to grub installation I specified /dev/sdf MBR as target.

The new Ubuntu booted fine. So I reverted BIOS back to normal and proceded to configure the Debian grub via /etc/grub.d/40_custom but was unsuccessful. The Ubuntu grub.cfg contains a lot of unfamiliar entries and graphics related entries.

I therefor decided to chainload the Ubuntu grub2 from my Debian Grub2, no success !

I have searched for help and tried many things but have come to a brick wall.

Any help or suggestions would be greatly appreciated.

Thanks,  Bob   -  BC Canada

---

### Post by oldfred on 2013-01-30
Best to see what is where:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

Whichever drive is set as boot drive is always hd0. So sometimes you have to change chain entries to other drives as order may change.

---

### Post by ZepTepi on 2013-01-30
Thanks for your prompt reply. The last line of your post about changing drives jogged my memory - I had seen it during my searches. I didn't quite understand the syntax so I went on. Here are the last few lines of the 40_custom file I created;

menuentry 'CHAINLOAD' {
    insmod part_msdos
    set root=(hd5,5)
    drivemap -s hd0 hd5
    chainloader (hd5)+1
}

It seems to work, do you see anything that I should change ?

Where can I find info on "devicemap" command ??

Thanks again for your help

---

### Post by oldfred on 2013-01-30
The drivemap command is more for Windows systems. Old versions of Windows were hard coded like the device used by Ubuntu until Ubuntu switched to using UUIDs. I think Windows 7 uses something like a UUID so it may not be required.

If devicemap, I saw with an older  version of grub that they obsoleted it and the search line is used to enumerate systems. But if just a hard codes set root then it just has to be correct. I often have issues as I left one SATA port empty and my flash drives may be sdb or sdf which changes all the other drives around.

I still have some entries like these, I like the spacer ( blank menuentry) also:

```
menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

menuentry "Chainload Other Systems Grub Legacy Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

```But I use this type more now as documented better by cavsfan in link above:

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}


```

---

