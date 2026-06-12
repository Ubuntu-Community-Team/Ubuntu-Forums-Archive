---
title: "Dual boot Windows 8.1 and Ubuntu Mate 14.04 HDD detection issue"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by crazzyshooter on 2015-08-13
Hello everyone,

I have recently installed windows 8.1 on my Acer laptop. I have  created 4 partitions in windows. I shranked my c: partition and gave 50GB  space for ubuntu mate 14.04 LTS OS.

**Screenshot:** [http://i.imgur.com/jKEqs7j.jpg](http://i.imgur.com/jKEqs7j.jpg)


When installing Ubuntu mate, the installer is not detecting windows partition. It showed an entire 1TB HDD. There is no "alongside" option.


  [B]Screenshot2: [URL="http://i.imgur.com/xoobL1g.jpg"]http://i.imgur.com/xoobL1g.jpg

[/URL][/B]When i tried running these commands **sudo parted -l** and **sudo fdisk -l** in terminal, i got these.

**Screenshot3: **[http://i.imgur.com/y1lrJ7F.jpg](http://i.imgur.com/y1lrJ7F.jpg)

**Screenshot4: **[http://i.imgur.com/13sjRF1.jpg](http://i.imgur.com/13sjRF1.jpg)


  I already have legacy mode enabled in BIOS so secure boot is already disabled. I've disabled fast boot in Windows 8.1.


Please help me. If you need any more information just let me know and i will post it.

---

### Post by oldfred on 2015-08-13
Windows only boots from gpt partitioned drives with UEFI. Ubuntu can boot from gpt with either UEFI or BIOS but should be in same boot mode as Windows.
Windows only boots form MBR(msdos) partitioned drives with BIOS.

But you have SFS or dynamic partitions, which is often what you get in creating more than the 4 allowed primary partitions using Windows with the 35 year old BIOS/MBR design system.
Dynamic partitions are proprietary to Windows and do not work with Linux. Windows makes it easy to create, but has no undo. They recommend full backup, create new primary partitions only and restore data.
But some third party tools may convert system, but best to houseclean as many partitions you can first. And you must have good backups anyway as a major partition restructure has risks.

       Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

            Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

    

You then also are showing a second issue. If drive was gpt and you install Windows in BIOS boot mode it converts to MBR, but does that incorrectly. It leaves the backup gpt partition table. After undoing dynamic partitions, you must undo the left over gpt data.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Would have been much better to install Windows in UEFI boot mode as then instead of a 4 partition MBR limit you have a 128 partition limit with gpt.

---

### Post by crazzyshooter on 2015-08-14
Hi oldfred,

I have a laptop which support both legacy and UEFI and i was planning to change it to UEFI. I don't care about any data as this is my new laptop. I will change it to UEFI and do the windows 8.1 installation and re-create 4 partitions from start then i will install ubuntu and get back here with a final answer.

Just want to ask a newbie question. I have a x64 system, does that mean that i already have a 64 bit UEFI? if you are unsure then is there any command/tool to check UEFI?

Thanks in advance. :)

---

### Post by crazzyshooter on 2015-08-14
Hi again,

There is another issue i am facing after enabling UEFI mode and disabling secure boot,

When i tried to boot windows 8.1 x64 with SanDisk USB, i saw this drive page(1TB unallocated space which is OK): [http://i.imgur.com/mgP7V9E.jpg](http://i.imgur.com/mgP7V9E.jpg)

I wanted to create 4 partitions so i divided into 4 and i created a primary partition(C drive) for windows OS.

Here is a screenshot: [http://i.imgur.com/deHg8hc.jpg](http://i.imgur.com/deHg8hc.jpg)

Now when i clicked next button, i got this pop up which says "The partitions on the disk selected for installation are not in the recommended order." [**Click here for more**]("http://i.imgur.com/4DgqPz0.jpg")

When i clicked OK to proceed with an installation, i got this error in just few secs: [http://i.imgur.com/YCqgHk1.jpg](http://i.imgur.com/YCqgHk1.jpg)

Not only this, i tried to boot ubuntu mate 14.04 x64 under UEFI mode and i faced this error: [http://i.imgur.com/iyu79zi.jpg](http://i.imgur.com/iyu79zi.jpg)

Under legacy mode, no problem in installation but a problem with windows partition detection when trying to install ubuntu.

Now i don't know what bios mode should i choose, legacy or UEFI? :(

Please help.

---

### Post by oldfred on 2015-08-14
You have to have gpt partitioned drive for Windows to install in UEFI mode.
And you have to boot Windows (and Ubuntu) installer in UEFI mode to install in UEFI mode.

With UEFI Windows wants extra partitions. It has to have the ESP - efi system partition (which all systems require), a system reserved & the main install. If from vendor it will also have a Windows recovery & a vendor recovery.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you installed Ubuntu in BIOS mode, then you have a grub in the MBR, and if flash drive does not boot, it defaults to hard drive, trys UEFI, then tries CSM/BIOS's MBR. And if just grub in MBR, it gives that error. 
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

I probably will not be on line for a day or two, but all I know is in link in my signature below. It is a lot but just about everything is in there.

---

### Post by crazzyshooter on 2015-08-14
Hi oldfred,

I am currently in UEFI mode. In UEFI, i can't install windows 8.1/windows 7 or Ubuntu (all x64).

How can i create gpt partitioned drive when i can't even install windows or run live ubuntu CD?

If i enable legacy mode again, will i be able to create gpt partitioned drive? if yes then later is it possible to renable UEFI and install windows and ubuntu without any problem?

Now i am stuck, my machine is totally blank(no data/no OS) with just UEFI enabled. :(

Thanks

---

### Post by oldfred on 2015-08-14
I used gpt to boot in BIOS mode since 10.10. Just built first UEFI system last fall, but almost all drives were then gpt partitioned.

But you have to be able to boot in UEFI mode.
Often better to have secure boot off, but should not be required.
If UEFI or UEFI with secure boot is on, you may have another setting to allow USB or DVD boot as that is a possible security issue, so they let you lock up system. But then you may not be able to boot a repair disk either?
From UEFI boot tab, you should have two entries for flash drive, one UEFI: name/label of flash drive and the other is just the name of flash drive which then is the CSM/BIOS boot.

---

### Post by crazzyshooter on 2015-08-14
Now i got it. Please check some screenshots of laptop bios below.

Bios Screen1: [http://i.imgur.com/dq6GWK1.jpg](http://i.imgur.com/dq6GWK1.jpg)

Bios Screen2: [http://i.imgur.com/vf1TsMe.jpg](http://i.imgur.com/vf1TsMe.jpg)

Bios Screen3: [http://i.imgur.com/R5NKk1Y.jpg](http://i.imgur.com/R5NKk1Y.jpg)

Bios Screen4(Boot Menu): [http://i.imgur.com/Mc64SJ8.jpg](http://i.imgur.com/Mc64SJ8.jpg)

This is how boot menu look whenever i try to boot via USB or DVD. UEFI option never displays on a boot menu. I think this bios doesn't fully support UEFI. :(

---

### Post by crazzyshooter on 2015-08-14
Hi oldfred,

I saw your [**post#2**]("http://ubuntuforums.org/showthread.php?t=2290583&p=13338094#post13338094") about fixparts guide and fixed this HDD detection issue.

I changed it back to legacy mode and installed a windows 8.1 first and created 4 partitions but they were not detecting when i tried to install ubuntu OS so i opened a terminal and issued these commands one by one.

```
sudo su
sudo gdisk -l /dev/sda
fixparts /dev/sda
```

All the partitions got detected when i ran ubuntu installer again.

Now i am running dual boot windows 8.1 with ubuntu mate 14.04 LTS with no issue.

Thanks oldfred for all the help. :):p

---

### Post by oldfred on 2015-08-16
Did you have to set a supervisory password? Acer seems to require that.

       [URL="http://ubuntuforums.org/showthread.php?t=2290594"]http://ubuntuforums.org/showthread.php?t=2290594

[/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

[URL="http://ubuntuforums.org/showthread.php?t=2290594"]
[/URL]

---

### Post by crazzyshooter on 2015-08-18
Hi oldfred,

Yes i had to setup a supervisory password. There is no way to enable UEFI without setting up a supervisory password. After enabling UEFI, I couldn't install windows, I got stuck here with this error. [**See this**]("http://i.imgur.com/YCqgHk1.jpg")([More here]("http://ubuntuforums.org/showthread.php?t=2290583&p=13338260#post13338260"))

So i changed back to legacy and installed windows and then installed ubuntu on another drive by fixing HDD partition issue([explained here]("http://ubuntuforums.org/showthread.php?t=2290583&p=13338563#post13338563")).

Now everything is working well, facing only one problem, touchpad is not getting detected. I Will create a new thread for this issue. :)

Thanks a lot for your support.

---

### Post by oldfred on 2015-08-18
Some other possibly related boot parameters are suggested here:
[http://forums.linuxmint.com/viewtopic.php?f=46&t=177619#p937590](http://forums.linuxmint.com/viewtopic.php?f=46&t=177619#p937590)

---

