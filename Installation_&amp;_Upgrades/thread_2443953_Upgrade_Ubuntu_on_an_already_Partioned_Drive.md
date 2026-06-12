---
title: "Upgrade Ubuntu on an already Partioned Drive"
date: 2020-05-22
forum: Installation &amp; Upgrades
---

### Post by sabbarth on 2020-05-22
Hello , i have a laptop with 3 partions on the drive. 

1 partition for Ubuntu 18.04
1 partition for Windows 
1 partition that i keep all my files music etc 


Is there a way to clean install 20.04 without having to wipe the drive and partition it all over again ? Or should I just upgrade to 20.04 without a clean install ?

---

### Post by oldfred on 2020-05-22
Make sure you have good backups of both Ubuntu, Windows & all your data. Any major system change can go awry.

But if you use Something Else, it should give the option to choose current / (root) as new / partition. If you reformat as ext4 it erases everything in /. Only if you use one of the other install options that say erase entire drive or use LVM which erases drive, may you lose Windows & data. You can choose not to reformat (a dirty install) and it will overwrite all standard settings (that you may have changed) with defaults but any data you have added remains. But that may also keep lots of old stuff that should be housecleaned.

Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by CelticWarrior on 2020-05-22
Yes, you can reuse the existing partitions for a clean, not upgrade, installation. Make sure you have a good backup of everything you want to keep, of course.
Choose "something else" and then select the needed partitions: The "1 partition for Ubuntu 18.04" is likely the root ("/") partition so select it as such and tick format. Then, assuming you have a UEFI installation as you should have in any UEFI hardware, don't forget to select the ESP (EFI partition) as well and again as such but DO NOT tick format for this one. You're all set.

---

### Post by dino99 on 2020-05-22
If your 18.04 is clean (no ppa / external sources), then you can edit /etc/apt/sources.list  and changing the entries for focal (that's what i do most of the time)
If you have installed ppa/external source(s), then first disable them, then downgrade to the genuine version, and do the sources.list changes.

Finally update/upgrade (i make that manually into synaptic, in that order: tools (apt.dpkg) , language (gcc,python,...) , system (dbus, ibus, systemd,...), the apps/libs
At the end , run autoclean/autoremove to clean the system, and reboot.
If that way seems too techy, then go for a clean install ):P

---

### Post by sabbarth on 2020-05-22
Yes Dino99 , i will do it the way oldfred and CelticWarrior described since i am not an experienced user of linux. 

Thank you guys for your help and immediate replies !!!!

---

### Post by sabbarth on 2020-05-22
> **CelticWarrior said:**
> Yes, you can reuse the existing partitions  for a clean, not upgrade, installation. Make sure you have a good  backup of everything you want to keep, of course.
Choose "something else" and then select the needed partitions: The "1  partition for Ubuntu 18.04" is likely the root ("/") partition so select  it as such and tick format. Then, assuming you have a UEFI installation  as you should have in any UEFI hardware, don't forget to select the ESP  (EFI partition) as well and again as such but DO NOT tick format for  this one. You're all set.


Unfortunately my laptop is an old one so i don't have a UEFI partition. So I guess i just won't have to select the ESP during installation , right ?

---

### Post by yancek on 2020-05-22
It's pretty simple to see if you have anything UEFI on the computer, just run:  sudo parted -l and if it does not show any EFI partition then there isn't one.  Just do a basic install and do not create an EFI partition.  You just need to make sure you select the correct filesystem partition designated by / and follow the instructions suggested   above.  If you are going to be posting questions that involve a windows OS, it is best to indicate which you are using since microsoft has been licensing operating systems for 35 years and this leads to guessing as in this thread.

---

### Post by sabbarth on 2020-05-22
> **yancek said:**
> It's pretty simple to see if you have anything UEFI on the computer, just run:  sudo parted -l and if it does not show any EFI partition then there isn't one.  Just do a basic install and do not create an EFI partition.  You just need to make sure you select the correct filesystem partition designated by / and follow the instructions suggested   above.  If you are going to be posting questions that involve a windows OS, it is best to indicate which you are using since microsoft has been licensing operating systems for 35 years and this leads to guessing as in this thread.


You are right Yancek , i thought i had posted the windows version on my first post. 

I am using windows 10 , the laptop is an old dell latitude e6230. 

I run  sudo parted -l  and there is no EFI partition . 


Thank you for your help !!!

---

### Post by TheFu on 2020-05-22
If Windows boots without UEFI, then so should Linux.
If Windows boots with UEFO, then so should Linux.

For the most accurate help, run the **boot-info** program and post the resulting URL here. Then there wouldn't be any questions about what your system has or doesn't have. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sabbarth on 2020-05-22
> **TheFu said:**
> If Windows boots without UEFI, then so should Linux.
If Windows boots with UEFO, then so should Linux.

For the most accurate help, run the **boot-info** program and post the resulting URL here. Then there wouldn't be any questions about what your system has or doesn't have. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


TheFu, this is the resulting URL from the boot - info 

[http://paste.ubuntu.com/p/HKWt8Ffr7r/](http://paste.ubuntu.com/p/HKWt8Ffr7r/)

---

### Post by TheFu on 2020-05-22
Looks like 6 partitions to me. Incorrect information is a good way to end up with a destroyed system.  

```
fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0xcbba9623
      Boot     Start       End   Sectors   Size Id Type
sda1  *         2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
sda2         1026048 169371647 168345600  80.3G  7 HPFS/NTFS/exFAT
sda3       169371648 358197247 188825600    90G 83 Linux
sda4       358199294 976771071 618571778   295G  5 Extended
sda5       358199296 381634559  23435264  11.2G 82 Linux swap / Solaris
sda6       381636608 976771071 595134464 283.8G  7 HPFS/NTFS/exFAT
```

The disk is MBR, not GPT, so that means Windows is installed in legacy mode.  The flash drive you booted to run boot-info booted in UEFI mode, so your hardware is capable, but since everything is legacy BIOS mode, I'd keep it that way. You'll miss out on some good stuff that EFI provides, but it isn't worth the hassle for most people to reinstall Windows.

At the very bottom of the output in the URL, it says that.  Boot-repair is pretty good at handling non-UEFI, legacy boot on MBR partition tables. It says:
```
Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda3 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix     

Confirmation request before suggested repair: __________________________________

LegacyWindows detected. **The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.**
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________

**Please set your BIOS in Legacy mode in order to start your Ubuntu 18.04.4 LTS, then type command [sudo update-grub] in order to add the Windows entry to your GRUB menu.**

```

That's what I would suggest too, but oldfred is really the expert here. Wait for his response, if you can.  I haven't dual booted in about 15 yrs. Got tired of MSFT trashing my Linux boot.

---

### Post by oldfred on 2020-05-22
You show BIOS/MBR, but have UEFI hardware.
So you have to be careful to select BIOS boot on installer or it may try to install in UEFI boot mode.

Besides good backups, make sure you have a Windows repair/recovery disk or the installer with repair console.
Windows 10 is not as easy to dual boot in BIOS mode.
Grub only boots working Windows, so when it updates & turns on fast start up or needs chkdsk grub will not boot it. You then have to temporarily install a Windows boot loader, fix Windows, and then reinstall grub.  Or use Windows flash drive & Ubuntu live installer to restore MBR's.

With UEFI, it is like having two MBR as each boot loader is in separate folders & UEFI will offer to boot any install. So when grub does not boot Windows, you can directly boot from UEFI menu and often then just turn off fast start up or f8 into repair console and fix Windows. Or UEFI has a lot less hassle dual booting with Windows 10.

---

### Post by sabbarth on 2020-05-22
So what would you suggest the best option is  ? 

Backup all my files and do a fresh install of Ubuntu and Windows on UEFI mode ? 

The reason i have installed BIOS/MBR versions is that when I installed UEFI version of windows and then tried to partition the drive so that I could install Ubuntu , after the installation of Ubuntu the system kept crashing the whole time. Giving me blue screens etc. 

I tried all the walkthrough solutions i could find on the internet but none of them helped me solve the problem. 


Guys once again thank you very much for taking the time and answering my questions , you are all very helpfull !!

---

