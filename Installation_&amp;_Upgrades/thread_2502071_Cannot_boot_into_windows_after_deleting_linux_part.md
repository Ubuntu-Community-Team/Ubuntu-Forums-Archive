---
title: "Cannot boot into windows after deleting linux partition"
date: 2024-11-01
forum: Installation &amp; Upgrades
---

### Post by catsareawesome424242 on 2024-11-01
I have been dual booting my PC with an old installation or Linux mint for quite a while and wanted to change to kubuntu. 
My way of unistaling Linux mint was to format it's whole hard drive and I now understand it was not my best move. After that I had the error no such device; unknown filesystem entering rescue mode while trying to boot my PC.
I installed Kubuntu 24.04 and it is working but I still can't boot up windows. 
I always used the legacy mode in the bios, I can see the drive with the windows startup file in the boot priority but selecting it gives me the same unknown filesystem error. 
I do not have a grub screen on startup and the pc boots Kubuntu directly 

I have the boot-repair pastebin
I tried booting the pc with a boot-repair usb key but stopped my effort at the error message  GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
[https://paste.ubuntu.com/p/dRBgTThsND/](https://paste.ubuntu.com/p/dRBgTThsND/)

thanks in advance for the help

---

### Post by grahammechanical on 2024-11-01
I have not read the boot repair report.

> I do not have a grub screen on startup and the pc boots Kubuntu directly

If we only have Linux on the machine we do not see a Grub boot menu. It is only when we are dual booting that we get a Grub boot menu. Kubuntu does not know that you also have Windows on that machine.

Do you have two drives? Was the Windows drive disconnected at the time Kubuntu was installed? If so, boot into Kubuntu and open the terminal and run

```
sudo update-grub
```

and watch the printout and see if Windows is detected. If it is you should now get a Grub boot menu with a option to boot Windows.

Are both Windows and Kubuntu installed in legacy mode. When we install in legacy mode on a drive that has the GPT partitioning scheme we need a partition that is flagged as bios-boot. This is where the boot files will go.

The Boot Repair report contains a lot of information. It takes AI to understand what everything in that report means. I have a limited natural intelligence that has not been trained to understand the Boot Repair report. I am having to work things out myself.

So, I ask questions. One natural intelligence communicating with another natural intelligence. I am also aware that throughout human history natural intelligence has proved to be not very intelligent. So, there we are.

Regards

---

### Post by catsareawesome424242 on 2024-11-01
I have 3 disk drive. 1. is a nvme with windows installation  2: a partitioned file containing linux 3: storage for windows 

```

sudo update-grub
Sourcing file `/etc/default/grub' 
Generating grub configuration file ... 
Found linux image: /boot/vmlinuz-6.8.0-48-generic 
Found initrd image: /boot/initrd.img-6.8.0-48-generic 
Found linux image: /boot/vmlinuz-6.8.0-41-generic 
Found initrd image: /boot/initrd.img-6.8.0-41-generic 
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi 
Warning: os-prober will be executed to detect other bootable partitions. 
Its output will be used to detect bootable binaries on them and create new boot entries. 
Adding boot menu entry for UEFI Firmware Settings ... 
done
```

unless I am mistaken, it doesnt seems to see windows.

also, I used the see all my windows files but now the drives 1 and 3 seems to be unmounted, I dont know if this means anything

---

### Post by oldfred on 2024-11-01
I am not sure even an AI could figure out how you got the configuration you have.
And as such will be difficult to maintain.

Your sda is gpt, and NVMe & sdb are old MBR.
The only place for MBR anymore is if you want to boot Windows in old BIOS boot mode as Windows requires BIOS with MBR. Windows has required UEFI with gpt partitioning installs by vendors since 2012. So not sure how will BIOS mode Windows drivers are maintained. Basic systems will still work, but UEFI recommended.

Ubuntu will install in either UEFI or BIOS boot mode from either MBR or gpt partitioned drives. It really should require gpt for UEFI boot & gpt if BIOS and no Windows on same drive. I started using gpt with Ubuntu one one gpt drive and XP on MBR drive in 2010. All drives since then when reformatted or purchased have been gpt.

Both Windows & Ubuntu install in boot mode UEFI or BIOS that install flash drive is booted in. One time boot menu for most install media will have both options although some may make a BIOS only or UEFI only boot flash drive.

Ubuntu installs grub boot to first drive as defined by UEFI/BIOS. Microsoft installs its boot files to drive set as default in UEFI/BIOS? Not sure how it is seen and only a few cases like yours have boot on one drive & install on another drive. Users with that configuration often do not know Windows boot partition on another drive is essential to boot process and eventually erase it breaking Windows.

Best for those with multiple drives to do clean installs. If two similar drives have each install on separate drive. If one faster like NVMe or SSD, then systems on faster drive & data on slower drives.

Long term best to start over with all gpt partitions and UEFI installs.
Temporarily, I would move Windows boot files from sdb1 to nvme0n1p1. Make sure boot flag is on nvme0n1p1.  You may need to do Windows repairs to get configuration correct. Windows normally has in BIOS mode separate Boot partition & main (c: drive) drive partition.  But boot files can be in c: drive if boot flag & MBR, & BCD are all in order. 
Make sure Windows then boots ok.

Grub may want to install to "first" drive. If NVMe drive is first, then you do not want to overwrite the Windows boot loader, so need to specify grub install to another drive. Best but not required to install to same drive as Ubuntu drive.

Since BIOS, you can use Boot-Repair in Advanced mode to install a Windows type (syslinux) BIOS boot loader to MBR of NVMe drive. And use gparted to move boot flag to NVMe drive's first partition. That may be all you need, but you may need BCD or other Windows repairs which only can be done with a Windows repair/recovery drive.

---

### Post by catsareawesome424242 on 2024-11-01
> **oldfred said:**
>  Your sda is gpt, and NVMe & sdb are old MBR 
The old linux installation was on ths sda. I reformated it before installing kubuntu

> **oldfred said:**
>  Users with that configuration often do not know Windows boot partition  on another drive is essential to boot process and eventually erase it  breaking Windows[./QUOTE]
To my defense, that drive was used exclusively for linux, I could not access it while booting in windows mode 

[QUOTE=oldfred;14211443] Best for those with multiple drives to do clean installs. If two similar  drives have each install on separate drive. If one faster like NVMe or  SSD, then systems on faster drive & data on slower drives.
If i understand the best course of action would be to backup my files and start from scratch and install both windows and ubuntu on the NVMe. This is pretty much what I had in mind but I was wondering if an easy fix existed.

> **oldfred said:**
>   Long term best to start over with all gpt partitions and UEFI installs. 
Because my kubutu install is on the sda which is already gpt, would it be safe to format the other two drive to gpt so this is dealt with before installing. (after backing up my data ofc)

> **oldfred said:**
>   Grub may want to install to "first" drive. If NVMe drive is first, then  you do not want to overwrite the Windows boot loader, so need to specify  grub install to another drive. Best but not required to install to same  drive as Ubuntu drive. 
I am kinda lost here, I would want both windows and ubuntu installation on the NVMe drive, ideally have the Grub on the same drive as Ubuntu but in this case I would still need to put it on another drive ? 

> **oldfred said:**
>  Temporarily, I would move Windows boot files from sdb1 to nvme0n1p1.  Make sure boot flag is on nvme0n1p1.  You may need to do Windows repairs  to get configuration correct. Windows normally has in BIOS mode  separate Boot partition & main (c: drive) drive partition.  But boot  files can be in c: drive if boot flag & MBR, & BCD are all in  order. 
Make sure Windows then boots ok. 
Is there a reason to do so if I do a clean install ?

last question, if I install from scratch is there any difference between installing Linux or Windows first ?
This is a lot for me, your help is very much appreciated

---

### Post by tea for one on 2024-11-01
> **oldfred said:**
> Long term best to start over with all gpt partitions and UEFI installs.
This is the best advice for a future robust computing experience
Also, each OS on a separate disk is easier to manage 
Each OS can boot independently of the other

Backup your data
Install your preferred OS on your nvme disk
Install your second OS on /dev/sda
Both in UEFI mode with gpt
Only have target disk accessible when installing
It doesn't matter which OS to install first (because other disks have been removed)

Although each disk will have a boot manager, grub can be organised to boot both systems if required in the future

---

### Post by catsareawesome424242 on 2024-11-01
Thanks!

---

### Post by oldfred on 2024-11-02
No need for temporary fix, if doing new installs.

I always gpt partition new or totally reconfigured drives and include an ESP - efi system partition on every drive, even those planned currently as data only drives. And if very large data drive, I like a small Linux install with some repair utilities, but not all my standard list of applications. Just for emergency boot without needing my external drives which all have full installs, also.

I try to keep the ESP on the Linux drive as the boot for all installs on that drive. Ubuntu defaults to "first" drive, and that is ok for most if drives all are internal. Only advantage of ESP & install on same drive is when "first" drive is corrupted and then no install boots. But then repair flash drive(s) for each install would be required. But Linux normally cannot fix Windows & Windows cannot fix Linux, so repair flash drives always required, anyway. Its just having at least one bootable system allows download of other repair tools if needed.

---

