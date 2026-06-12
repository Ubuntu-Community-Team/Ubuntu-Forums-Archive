---
title: "Installation Type"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by skywayge on 2015-11-16
Hello
I'm stuck on installation type window, i cant see any partition inside the box, and when i try to click + button installation is getting crashed i tried both 14.04 and 15.10 files but the result is same

---

### Post by yancek on 2015-11-16
From the info you posted, you seem to have a computer with no current operating system on it, is that correct?  Did you verify the download of the Ubuntu iso file by doing an md5 checksum?  There are generally several options to install and the best one for control is the manual option which is referred to as something else in Ubuntu.  Which did you select.  This message is seen frequently on systems with other operating systems taking up the entire disk.

---

### Post by oldos2er on 2015-11-16
Please post your full hardware specs.

---

### Post by skywayge on 2015-11-16
> [COLOR=#000000]From the info you posted, you seem to have a computer with no current operating system on it, is that correct? Did you verify the download of the Ubuntu iso file by doing an md5 checksum? There are generally several options to install and the best one for control is the manual option which is referred to as something else in Ubuntu. Which did you select. This message is seen frequently on systems with other operating systems taking up the entire disk.[/COLOR]
currently i have windows7 which got stuck on blue screen after updating it to windows 10 in the boot options i can see windows7 button, i'm not sure that i have enough knowledge of os to do manual install but if it is necessary i will try to check the guids

> **oldos2er said:**
> Please post your full hardware specs.
[http://support.hp.com/us-en/drivers/selfservice/hp-pavilion-dm4-3100-beats-edition-entertainment-notebook-pc-series/5228963/model/5286459](http://support.hp.com/us-en/drivers/selfservice/hp-pavilion-dm4-3100-beats-edition-entertainment-notebook-pc-series/5228963/model/5286459)
i just compared MD5 and is is saying that MD5 check sums are the same

p.s. 
for additional info i'm trying to install ubuntu from usb drive(Verbatim 16GB) which i generated using following software: Universal-uSB-Installer downloaded from this guide [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
and live cd version is working without an issue wifi is working and i'm also able to browse intenret with firefox

---

### Post by grahammechanical on 2015-11-16
Is Windows 10 working or broken? And do you intend repairing windows 10 if it is broken? This comment is still valid

> This message is seen frequently on systems with other operating systems taking up the entire disk.

If we have not accepted the Erase disk and install Ubuntu option which is the only option the installer can offer in the circumstances and then try to get the installer to progress then the installer has no option but to crash as it has no where to go.

Did this machine come with Windows 8 pre-installed or was Windows 8 an upgrade from Windows 7? With Windows 7 we get a msdos partition table with a 4 primary partition limit which may be used up and may be the source of this situation. With Windows 8 and 10 pre-installed we get a GPT partition table without a limit on the number of primary partitions.

Also, you might now have what Microsoft calls dynamic disks which are a proprietary format and that could be causing this problem.

[URL="http://windows.microsoft.com/en-gb/windows-vista/what-are-basic-and-dynamic-disks"]http://windows.microsoft.com/en-gb/windows-vista/what-are-basic-and-dynamic-disks
[/URL]
There you are. Some things to investigate. Regards.

---

### Post by skywayge on 2015-11-16
> **grahammechanical said:**
> Is Windows 10 working or broken? And do you intend repairing windows 10 if it is broken? This comment is still valid



If we have not accepted the Erase disk and install Ubuntu option which is the only option the installer can offer in the circumstances and then try to get the installer to progress then the installer has no option but to crash as it has no where to go.

Did this machine come with Windows 8 pre-installed or was Windows 8 an upgrade from Windows 7? With Windows 7 we get a msdos partition table with a 4 primary partition limit which may be used up and may be the source of this situation. With Windows 8 and 10 pre-installed we get a GPT partition table without a limit on the number of primary partitions.

Also, you might now have what Microsoft calls dynamic disks which are a proprietary format and that could be causing this problem.

[URL="http://windows.microsoft.com/en-gb/windows-vista/what-are-basic-and-dynamic-disks"]http://windows.microsoft.com/en-gb/windows-vista/what-are-basic-and-dynamic-disks
[/URL]
There you are. Some things to investigate. Regards.
sorry my mistake it came with pre installed windows7 ,there was no windows8 installed

---

### Post by yancek on 2015-11-16
Boot the Ubuntu installation medium (DVD/flash drive) and open a terminal by clicking the Dash icon (the Ubuntu logo in the extreme upper left of the Desktop) and in the Search box, type terminal.  You should see an icon just below the Search box for 'terminal'.  Click on it and when it opens type: sudo parted -l (Lower Case Letter L in the command) and post the output here.  You could also enter in the termina:  sudo gparted and when the new window opens upload it here so we can see your drive/partition information.

If you originally has windows 7 installed, it still may be MBR rather than UEFI even though you updated to windows 10.  I'm not sure but posting the above output should provide enough info for someone to point you in the right direction.

---

### Post by skywayge on 2015-11-16
[http://i68.tinypic.com/16ixl4z.png](http://i68.tinypic.com/16ixl4z.png)
and also i get following error when i try to open main disk with file manager
[http://i68.tinypic.com/263ucdl.png](http://i68.tinypic.com/263ucdl.png)

---

### Post by oldos2er on 2015-11-16
Next time please just copy and paste the terminal text into a post here. If it's large please enclose it in [code tags]("http://ubuntuforums.org/misc.php?do=bbcode#code").

---

### Post by skywayge on 2015-11-16
> **oldos2er said:**
> Next time please just copy and paste the terminal text into a post here. If it's large please enclose it in [code tags]("http://ubuntuforums.org/misc.php?do=bbcode#code").
```
[FONT=arial]ubuntu@ubuntu:~$ sudo parted -l[/FONT]
[FONT=arial]Model: ATA TOSHIBA MK5076GS (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 500GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]
[FONT=arial]Disk Flags: [/FONT]

[FONT=arial]Number  Start   End    Size    Type     File system  Flags[/FONT]
[FONT=arial] 1      1049kB  210MB  209MB   primary  ntfs         boot[/FONT]
[FONT=arial] 2      210MB   477GB  477GB   primary  ntfs[/FONT]
[FONT=arial] 3      477GB   500GB  22.9GB  primary  ntfs[/FONT]
[FONT=arial] 4      500GB   500GB  113MB   primary  fat32        lba[/FONT]


[FONT=arial]Error: /dev/sdb: unrecognised disk label[/FONT]
[FONT=arial]Model: ATA SAMSUNG MZMPC032 (scsi)                        [/FONT][FONT=arial]                [/FONT]
[FONT=arial]Disk /dev/sdb: 32.0GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=arial]Partition Table: unknown[/FONT]
[FONT=arial]Disk Flags: [/FONT]

[FONT=arial]Model: Verbatim STORE N GO (scsi)[/FONT]
[FONT=arial]Disk /dev/sdc: 15.5GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]
[FONT=arial]Disk Flags: [/FONT]

[FONT=arial]Number  Start   End     Size    Type     File system  Flags[/FONT]
[FONT=arial] 1      1049kB  15.5GB  15.5GB  primary  fat32        boot, lba[/FONT]
```

---

### Post by mastablasta on 2015-11-17
[FONT=arial]Partition Table: msdos[/FONT] = means you have MBR

partitions 1-4 are all primary so that is maxed out. to proceed with install you need to do the following:
1. change one partition to secondary (in windows this can be done with mini tool partition wizard) - (secondary = extended)
2. run disk defragmenter
3. you then need to create unformatted free space using windows disk manager

the free space should be recognised by installer and all you would need to do is say install to free disk space. if not then you need to go to manual install and create root (/) and /swap (like pagefile in windows) partition

Make sure you backup before doing any partition work.

---

### Post by skywayge on 2015-11-18
> **mastablasta said:**
> [FONT=arial]Partition Table: msdos[/FONT] = means you have MBR

partitions 1-4 are all primary so that is maxed out. to proceed with install you need to do the following:
1. change one partition to secondary (in windows this can be done with mini tool partition wizard) - (secondary = extended)
2. run disk defragmenter
3. you then need to create unformatted free space using windows disk manager

the free space should be recognised by installer and all you would need to do is say install to free disk space. if not then you need to go to manual install and create root (/) and /swap (like pagefile in windows) partition

Make sure you backup before doing any partition work.
thank you for the guide but the issue is that my windows is damaged and i can't access it :)

---

### Post by mastablasta on 2015-11-19
> **skywayge said:**
> thank you for the guide but the issue is that my windows is damaged and i can't access it :)

well I see then that it's a bit of a problem in my approach. here is what you need to do:

1 - do you want to keep windows? if so, then you need to first troubleshoot that error first and solve it, but you can't do that here (try windows forums). as I know there are various recovery options that should be still available to you (recovery console, repair disk, recovery disk...). only after you solved the issue and can boot into windows you can proceed in creating dual boot safely. though in older versions I think fdisk could repartition the drive in console and chkdsk fixed any file system issues afterwards.

2 - if you DO NOT want to keep windows, then find an external driver or networked computer, boot into live Linux session and move the date there. then nuke the disk (i.e. install using the whole disk). it will all be done in about 15 mins.

I would go with option 1 - find a way to repair windows first the do my previous instructions and create dual boot. I use windows quite often and in my opinion it is still a better supported OS than Linux and has way more software available - free or proprietary.

---

