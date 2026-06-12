---
title: "Installer says no operating system detected"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by steve217 on 2015-08-24
Hi,

I'm trying to install Ubuntu on my laptop so I can dual boot it with Windows 7 (came pre-installed). The installer says that there is no operating system detected. I read some other threads about this problem and have tried partitioning the drive on Windows (outside of the Ubuntu Installer) and I was able to accomplish that using MiniTool Partition Wizard. That didn't help with the error message though. I checked the BIOS and saw that the secure boot was already disabled and I changed Quick Boot to Diagnostics Boot. That didn't help either. I started reading about fixparts and ran it on my computer and got the message saying "GPT signatures detected on the disk, but no 0xEE protective partition!" and I'm not sure if I should be deleting that... I don't want to mess up my computer...

Any help?

---

### Post by Bucky Ball on 2015-08-24
Welcome. Please select 'Something Else' when you get to the partitioning section of the install, NOT 'Alongside' or anything else. Windows must be out of hibernation mode (boot to Windows and switch hibernation off) and you need to switch secure boot off in the BIOS prior to installing. You must install Ubuntu in EFI mode if Windows is installed in EFI. 

Quickboot needs to be OFF as this has something to do with hibernation. It may get switched off when you boot to Windows and switch off hibernation. Don't know, don't use it. 

I would avoid tweaking anything else for fear of making this more confusing and difficult to fix. You shouldn't need to be doing much except de-hibernating Windows, switching off secureboot and installing Ubuntu in EFI mode if required (which it probably is). 'Something Else' when you get to partitioning and create the partitions yourself.

---

### Post by sudodus on 2015-08-24
Welcome to the Ubuntu Forums :-)

Have you turned of ***Fast startup***  and ***Hibernation*** in Windows (via the Control Panel)?

If there are still problems, maybe Windows created 'dynamic partitions' which cannot be managed by linux. I don't know much about it, but I think other people here at the Ubuntu Forums can give more detailed advice about 'dynamic partitions' and other problems with Windows.

---

### Post by steve217 on 2015-08-24
Secure boot is disabled.
I don't think my BIOS has a quick boot option.
I turned off Hibernation using the command "[FONT=verdana][COLOR=#323232]**powercfg -h off**[/COLOR][/FONT]" in an elevated command prompt.
I also went into the BIOS and chose the option to Boot UEFI only, but then I got taken to the Ubuntu Installation on the USB Drive instead of Windows 7. I tried choosing the other devices on the list to boot from, but none of them took me to Windows 7. So I re-enabled the 'Boot from both Legacy and UEFI' option and was able to get into Windows 7 again.

Oh and the installer was still giving me the 'no detected operating system' message.
Does that information help? I'm going to look into 'dynamic partitions' now.

Update:
I went ahead and deleted the GPT signatures. Now I just get the error: "0xee partition doesn't start on sector 1"
I checked the Ubuntu installer again. I'm still getting the error message 'no operating system detected', but this time when I click 'Something else' I can see my hard drive and the free space.
What do I do now?

---

### Post by sudodus on 2015-08-24
Fast boot / quick boot / fast startup is a feature in Windows.

You must turn off *both* hibernation and fast startup in Windows. Otherwise UEFI will boot directly into Windows. You do that via Windows's control panel:

All apps -- Windows system -- Control panel -- System and security -- Power options -- Choose what the power button does

scroll down and untick (they should be 'off')

- Turn on fast startup
- Hibernate

---

### Post by oldfred on 2015-08-24
Was this a Windows 8 UEFI system, that you then installed Windows 7 in BIOS mode?
Probably better to install Windows 7 in UEFI mode, but its default seems to be BIOS and you have to copy to flash drive and move some boot files around to let it boot in UEFI mode.

Windows does not correct convert a gpt partitioned drive to MBR(msdos) partitioned drive. It leaves the backup gpt partition table at end of drive. Then Linux tools see both MBR & gpt and do not know what to do, so assume you want to totally repartition/reformat as it is incorrect.

You need to use fixparts to remove the backup gpt partition table info to make it MBR, but then have the 4 primary partition limit and have to use one primary partition as the extended partition so you can make more logical partitions.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Not sure where your partitions are at now.
Post this from live installer's terminal.
      
 sudo parted /dev/sda unit s print

---

### Post by steve217 on 2015-08-24
> **sudodus said:**
> Fast boot / quick boot / fast startup is a feature in Windows.

You must turn off *both* hibernation and fast startup in Windows. Otherwise UEFI will boot directly into Windows. You do that via Windows's control panel:

All apps -- Windows system -- Control panel -- System and security -- Power options -- Choose what the power button does

scroll down and untick (they should be 'off')

- Turn on fast startup
- Hibernate

I can't find the ticks you are talking about. This is the screen when I click Power Options:

[IMG]https://cdn.pbrd.co/images/7Y6yMiy.png[/IMG]

And this is the screen I get when I click the 'Choose what the power buttons do' option (third one down on the top-left of the screen):

[IMG]https://cdn.pbrd.co/images/7Y9OmBl.png[/IMG]

The way I've been changing the UEFI/Legacy option is by going to the BIOS and I've been able to boot into my flash drive for the Ubuntu Installer by hitting F12.

> **oldfred said:**
> Was this a Windows 8 UEFI system, that you then installed Windows 7 in BIOS mode?
Probably better to install Windows 7 in UEFI mode, but its default seems to be BIOS and you have to copy to flash drive and move some boot files around to let it boot in UEFI mode.

Windows does not correct convert a gpt partitioned drive to MBR(msdos) partitioned drive. It leaves the backup gpt partition table at end of drive. Then Linux tools see both MBR & gpt and do not know what to do, so assume you want to totally repartition/reformat as it is incorrect.

You need to use fixparts to remove the backup gpt partition table info to make it MBR, but then have the 4 primary partition limit and have to use one primary partition as the extended partition so you can make more logical partitions.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Not sure where your partitions are at now.
Post this from live installer's terminal.
      
 sudo parted /dev/sda unit s print

I noticed in the BIOS that it says 'Preinstalled OS License: Win8 STD DPK TPG' . I'm not sure what that's about. I got the laptop with Windows 7 on it from my school. Sorry, I didn't know about that.

I was looking up how to check if Windows 7 was installed in EFI or BIOS and I tried looking at the setupact.log file. It says 'Detected boot environment: BIOS' which indicates that it has been installed on the BIOS (Legacy BIOS) if I'm correct. So you were right about that.

I opened FixParts and pressed 'Y' to remove the stray GPT data. I wanted to try the Ubuntu Installer again so I went into the BIOS, changed the boot mode to Legacy this time, and then booted from the flashdrive, and the installer finally says that it detects Windows 7. Am I okay to continue now?

This is the log I get after running the command:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s printModel: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start       End         Size        Type     File system  Flags
 1      373848615s  976768064s  602919450s  primary  ntfs         boot



```

Here is a picture of what I see after clicking the 'Something else' option:

[IMG]https://cdn.pbrd.co/images/7YcoXuf.png[/IMG]

---

### Post by oldfred on 2015-08-24
You only have the one NTFS partition. Standard installs use all 4 primary partitions.
School must have done their own install of just Windows 7 in one partition, as even default install of Windows is normally 2 partitions.

I tend to prefer smaller system partitions for both Windows & Linux and larger data partitions. If sharing data with Windows then a separate NTFS data partition is often a good idea. But Windows only works well if NTFS partition has 30% free inside the NTFS partition so always leave lots of space in it or regularly houseclean. Windows tends to download lots of stuff and few houseclean. Then when it gets slow they blame Windows. But usually buy another Windows and notice how much faster it is.

---

### Post by steve217 on 2015-08-24
So can I install Ubuntu while in Legacy boot mode?

And are you saying I should create three new partitions:
1. root /
2. swap
3. data that I will share between Windows & Linux

---

### Post by aymen3 on 2015-08-24
Perhaps the download is corrupt?

---

### Post by yancek on 2015-08-24
A 20-25GB partition for root (/) for system partitions, 2-4GB for swap (size is up to you) and use the rest of the free space for your data partition, format it ntfs and the / partition ext4 format.  Make sure you do NOT click the check box in the format column for the windows partition.

---

### Post by oldfred on 2015-08-24
If using shared data partitions, you can have /(root) as 20 or 25GB, but must then save data into the data partitions.
I have a 25GB partition and use about 13GB now and that includes /home which normally has both hidden user configurations as well as all data.

---

### Post by sudodus on 2015-08-25
> **steve217 said:**
> I can't find the ticks you are talking about. This is the screen when I click Power Options:

...

It seems that menu has changed from Windows Technical Preview (which I have), so I can't help you find it in your system. I hope you can turn off everything in Windows that 'smells of hibernation' yourself or with help from other people. It seems the discussion is progressing, so I'm not too worried about that.

---

