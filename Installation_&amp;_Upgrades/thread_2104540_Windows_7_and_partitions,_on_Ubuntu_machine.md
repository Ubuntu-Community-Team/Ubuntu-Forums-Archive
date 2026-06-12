---
title: "Windows 7 and partitions, on Ubuntu machine"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by graabein on 2013-01-13
Hi, I've been running Ubuntu 12.04 and I'm looking to install Windows 7 to dual boot. Here's my drive layout:

/dev/sda
* /dev/sda1 (boot) /
* /dev/sda2 extended
** /dev/sda5 swap
** /dev/sda6 home
** /dev/sda7 ext4

/dev/sdb
* /dev/sdb1 ext4
* /dev/sdb2 ntfs <-- install here

sda is a SSD that I initially freed up a logical partition on. Windows 7 didn't like this, so I freed space on the HDD sdb, a primary partition. Still it won't take. I think it needs a //system// partition. 

Is this true? What's the easiest route do you reckon?

---

### Post by grahammechanical on 2013-01-13
Do not take me for a expert on this. I am just passing on some things that I have noticed from other posts on this forum.

It is my understanding that windows likes to be the first and only OS on a hard disk. May I suggest that you remove the SSD and boot the machine from the Windows install disk with only the hard disk in the machine. And install Windows like that.

Then put the SSD back in and boot from it. Load Ubuntu and with both the SSD and the hard disk in the machine run the command.

```
sudo update-grub
```

Others on this forum may give better advice that this. So, wait to see what is suggested.

Regards.

---

### Post by darkod on 2013-01-13
Take the boot flag off sda1 and put a boot flag on sdb2. If you have any other boot flags, turn them off. Try installing again.
Linux doesn't use the boot flag but windows uses it and the flag determines where to put the boot files. If it sees it on sda1 and the partition is linux type, it will probably not like it.

---

### Post by Herman on 2013-01-13
> It is my understanding that windows likes to be the first and only OS on a hard disk.I think that's a myth. A while ago I did a few experiments and I was able to boot Windows in any partition anywhere on any disk, even in a logical partition providing you set the boot flag in the logical partition with GParted. (Grub only sets the boot flag in primary partitions). I think in the case of Windows7 the boot partition should be primary but I'm not sure if that's essential either.

However, that depends on the way the installation media has been programmed. 
Many Windows CDs are 'recovery CDs' (a misnomer) instead of 'installation CDs', and the 'recovery' disks 'return the computer to its factory shipped state', wiping out any other operating systems and all user data and so on. The 'Installation' CDs tend to allow more flexibility and most can choose which partitions to install into but seem to be less commonly available for some strange reason.

---

### Post by graabein on 2013-01-18
Thanks for the input. I'll try setting the boot flag with GParted. Will I be able to boot into Linux without the boot flag on the SSD?

Another thing, do I have to keep the boot flag on the HDD? Because most of the time I'll just go directly to Linux, and I want to boot as fast as possible, naturally. Do you think the start time for getting into grub (wherever its installed) is much slower when it has to check the HDD also?

---

### Post by darkod on 2013-01-18
Yes, linux can boot without the boot flag since it doesn't use it as already mentioned.

And the boot flag doesn't slow down grub2 booting. For linux it's like it doesn't exist.

---

### Post by Mark Phelps on 2013-01-19
> **graabein said:**
> sda is a SSD that I initially freed up a logical partition on. Windows 7 didn't like this, so I freed space on the HDD sdb, a primary partition. Still it won't take. I think it needs a //system// partition. 

Is this true? What's the easiest route do you reckon?

Win7 needs a Primary partition for its boot loader files, but the OS partition can be Logical.

BIG Plus to the advice to remove the other drive to install Win7.  That will prevent Win7 from writing its MBR to the sda -- which it would do by default if both drives were still connected during the install.

I believe that Win7 would automatically set the boot flag to "sdb2" (which will be "sda2" during the install), but I'm not sure about that.

Win7 does not need a separate boot or system partition -- that's just done by default in OEM machines to allow you to encrypt the Win7 OS partition -- as Win7 can't boot if its boot loader files are inside an encrypted partition.

---

### Post by Herman on 2013-01-19
> Win7 needs a Primary partition for its boot loader files
No, like I said, that's a myth. If you don't want to believe me see the following link, I'm not the only person who has done it,[  Booting Windows Vista/7 From a Logical Partition]("http://kemovitra.blogspot.com.au/2009/09/booting-windows-vista7-from-logical.html")

---

### Post by irv on 2013-01-19
Just a side note. Once you have Win7 and Ubuntu installed and have Ubuntu set to boot first in grub, you can set grub to boot without displaying the grub menu. This will speed up your boot time. Then if you want to boot into windows, just press the shift key at boot up to get to the grub menu.

---

### Post by oldfred on 2013-01-19
@Herman
I remember threads by you & .meierfra on booting XP in a logical, but did not know the work arounds could be used for Vista/7. :)
But Windows MBR will not boot to a logical, but lilo will as that was the work around with XP. I assume syslinux will also as that is what Boot-Repair installs.

Will Windows repair the PBR or run other repairs on the logical install? I have seen many users with issues and it seems like it just is easier to install Windows in primary partitions. Then it automatically keeps boot files configured correctly. And with multiple installs of Windows move boot flag before install to keep its boot files separate from first install.

---

### Post by Herman on 2013-01-19
Hello OldFred, yes. I agree it's easier to let Windows do what it likes, but if there's a reason for wanting to make it do what the computer owner wants then it is possible to force Windows to do the owner's bidding.  At least in my computer that is.
I am looking for my notes from my old Windows 7 experiments for the exact details.  I  do remember I really put Windows 7 RC through its paces and subjected it to every kind of cruelty I could think of.  I must admit even if I'm not a Windows fan that the installation disk repair tools did a great job at repairing Windows 7 every time I trashed it. Sometimes I needed to run them a few times though, they would sometimes not always fix everything at once. If I can't easily find those old notes I'll repeat the experiment of making Windows 7 boot and run in a logical partition again myself just for the fun of it and let you know what happens.

---

### Post by graabein on 2013-01-20
Is there somewhere online you could put these notes on Windows 7 (and Linux)? A Ubuntu wiki, AskUbuntu or maybe some Stack Overflow place? Information wants to be free etc.

---

### Post by oldfred on 2013-01-20
Herman has his own site, which is very good if you want to understand how things work. Lots of technical info and he actually tests or experiments with all the info he posts. I refer to his site regularly (and have learned a lot)  but it is more detailed and new users can get overwhelmed.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Herman on 2013-01-20
Well from the series of experiments I have had time for so far it seems I'm wrong and the boot loader files for Windows 7 do need to be in a primary partition.

To try to sum up what I have found out so far without being too wordy, 

[LIST]
[*]The primary partition for Windows 7 boot loader files can be in any partition number between 1 and 4  and the partition can be in any physical location on the hard disk.
[*] The partition that contains the Windows 7 operating system files can be a  logical or a primary partition and it can have any partition number and be in any  physical partition on the hard disk or even in a different hard disk  from the boot loader files.
[*]The Window 7 boot loader files can be cut out of the boot loader partition and pasted into the operating system partition using Ubuntu  and the installation can be easily fixed and made bootable with Windows  7's Startup Repair in the Windows 7 Installation Disk. (But only if the operating system is a primary partition).
[/LIST]
 I spent some time copying and pasting the  operating system partition around with GParted, reinstalling boot loader and also re-installing  the entire operating system and that's how it seems to me so far.

 If an earlier version of Windows exists in the computer, even if it's in a different hard disk, Windows 7 will inject its boot loader files into that. 
I had Windows XP in the first partition in the first hard disk and tried to install Windows 7 in last place in the second hard disk in a logical partition number 7. 
It installed up just fine and I was able to boot either operating system via Windows 7 boot loader files in Windows XP.

I and most other computer users do not like having one operating system dependant on the other. If Windows XP gets a virus or the hard disk fails it will bring down my Windows 7 installation, (if I was a serious Windows user doing real work I would be very concerned about that). After copying the boot loader files out and pasting them into Windows 7   I was not (easily) able to fix Windows 7.

The fact that Windows 7 is tied to the MBRs disk signature added another level of complexity to the task and that was not needed for this experiment. I used a dd command to copy the first 446 bytes of each MBR to a file and then copied the mbr img files to opposite disks to cause the second hdd to have the 1st hdd's disk sig. That task would have been beyond most computer users abilities and dangerous for most users. I do not recommend anyone try that at home. 
Then I unplugged the first hdd containing Windows XP.  This event has disabled the boot of my Windows XP installation but I'll fix that later.

I have not so far managed to get Windows 7 to boot in a logical partition despite trying the commands given in the website I linked to earlier.
Windows 7 's Startup Repair fixed Windows 7 perfectly well as soon as the entire operating system was copied and pasted to a primary partition using GParted.
I intend to try again as I did depart from the instructions in the website by running Startup Repair after the suggested commands and maybe I shouldn't have.

I have spent some time re-installing Windows 7 and copying it and pasting it around with GParted but these experiments are by no means exhaustive. 
I will try a few more experiments but it seems unlikely from now on I will learn anything very surprising.

---

### Post by Herman on 2013-01-20
I'm back and I just did another experiment and I managed to find out something that surprised me.
This experiment is a little 'outside the box' in more ways than one.

I made some room at the back of a USB flash memory stick using GParted and I copied and pasted the 100 MiB Windows 7 boot loader partition to the USB drive. 
Then I deleted the original partition from the (second) hard drive). 
Finally, I ran update-grub and GRUB listed Windows 7 in the USB.

Windows 7 was able to boot up as fresh as a daisy via GRUB to the last partition in the USB and from there to Win7 in the last (logical) partition in my second hard drive. (The bootloader partition in the USB drive is primary).

The significance of this is, if a computer has a shortage of primary partitions they can still install and boot Windows 7. I don't think Windows 7 would be able to do this by itself though, you would need to have a primary partition of at least 100 MiB left vacant for it prior to installing and then re-arrange partitions after the fact.

I am surprised that Windows 7 can boot via a USB drive. I don't think the operating system itself would boot if it was installed in a USB.  I do remember using floppy boot disks for booting Windows 95. (Giving away my age a bit here). 

NOTE: I will not have time to keep on testing this arrangement to see if it's stable and reliable in the long term, it's just an experiment. It may help somebody but no guarantees.

---

### Post by oldfred on 2013-01-20
Good info Herman. I am really surprised that Windows booted from USB. But maybe that is allowed as if boot is damaged so you can get into system?

I once downloaded the Windows repair ISO, but never figured out how to install to a flash drive directly from Ubuntu. I made the CD and used that to install itself to flash drive. But it only used 250 to 300KB so I used the procedure to install grub to the flash drive, made sure there was only one /boot with both grub files & the BCD and it booted Windows. I then created another partition and added several repair ISO to loopmount from grub and had a Windows repair CD plus Linux repair tools.

---

### Post by Herman on 2013-01-21
Hey that's a great idea, OldFred, a Grub over BCD boot disk!

GRUB 2 supports the NT file system, so that would be entirely feasible. I have even installed GRUB inside Windows in the past. There are only two commands needed to turn it into a standalone GRUB/BCD boot disk. A boot disk like that could be made from the Ubuntu LiveCD before a person begins installing Ubuntu. 

Lets see now, in my Ubuntu installation the Windows 7 boot loader partition in the USB  shows up automatically mounted as /media/System Reserved.
This can either be verified by the ls /media command, or by navigating to the /media folder with the file manager and taking a look.

Linux doesn't like white spaces, so I need to use GParted to change the label in that file system and replace the white space with an underscore or a hyphen. (requires nyfsprogs to be installed first).
Now it's showing up as as /media/System_Reserved.

Using the blkid command to check, the partition number is /dev/sdc2, so the MBR to install GRUB to will be /dev/sdc. I can use that in the following command to create GRUB/BCD boot disk, 
```
sudo grub-install --root-directory=/media/System_Reserved /dev/sdc
```NOTE: To anyone wanting to try this, It is very important to check and make sure you will be installing GRUB to the correct MBR,  (shown here as /dev/sdc for me in this computer), this varies between different computers and a mistake here could be disasterous for some people. You need to use the blkid command first to check.

Now all I need to do is copy my current grub.cfg to the new boot disk,
```
sudo cp /boot/grub/grub.cfg /media/System_Reserved/boot/grub/grub.cfg
``` I just tested the new boot disk and it appears to be working on the first test boot-up and has booted Windows 7 okay. I will likely get to test it a few more times as the next items on my agenda are to be risky for Windows 7. In fact I have already trashed the Windows 7 boot,  I deleted my hard disk Windows 7 bootloader partition and 'm going to try that [Booting Windows Vista/7 From a Logical Partition]("http://kemovitra.blogspot.com.au/2009/09/booting-windows-vista7-from-logical.html") tutorial again.

---

### Post by Herman on 2013-01-21
> But maybe that is allowed as if boot is damaged so you can get into system?I don't know but it seems like it could be a handy trick.

Microsoft themselves have a KB article advising people how to copy out their Windows XP ntldr ntdetect.com and create a boot floppy with its own boot.ini files,[ How to create a bootable floppy disk for an NTFS or FAT partition in Windows XP]("http://support.microsoft.com/kb/305595/en-us")

Not so many people use floppy disks these days, a USB is better. I'm not aware of any kb articles about BCD boot disks though. I haven't searched.

---

### Post by oldfred on 2013-01-21
I think it also may make a difference how you format NTFS partition. I once ran chkdsk from the Windows 7 repair flash and it converted  partition boot sector - PBR to Windows 7 from Windows XP. I could see the difference with testdisk dump as backup showed ntldr and PBR showed bootmgr.  Structure is also somewhat different.
I do not know if just installing Windows 7 converts/reformats PBR or not, I guess it must to be able to boot, but with a logical partitions does it?

---

### Post by Herman on 2013-01-21
I agree with you there's something different about the Windows 7 boot sector.
I once installed Ubuntu in a netbook which had Windows XP in it. Windows XP wouldn't boot after Ubuntu was installed. Then I found out there was a peculiarity with that particular make and model of netbook and Windows XP needed a Windows 7 boot sector for some reason. The solution was to run CHKSDK from a Windows 7 DVD.  I probably ran FIXBOOT too and after that I was relieved to be able to give the netbook back to its owner with both operating systems in good working order.  

I wasn't aware the Windows 7 boot sector would be unable to function in a logical partition. 
You were asking me in an earlier post whether or not all the Windows 7 startup repair and the console commands  would work when Windows 7 is in a logical partition. 
The command bootrec /fixboot returns 'element not found'. 
The Startup Repair log ends with: ' Root Cause found: -----------------------  The partiiton does not have a valid System Partition.'

---

### Post by Herman on 2013-01-21
When Windows 7 is installed in a logical partition and the primary partition that normally contains Windows 7's boot loader files is deleted,  'Startup Repair' in the Windows Installation DVD can easily fix it.

It seems to be necessary to run 'Startup Repair' twice in succession to accomplish that.
The first run of 'Startup Repair' takes a long time and creates an new 'System Reserved' partition for the boot loader files if there is free space in the hard disk and a primary partition slot available in the MBR.  
The second run of 'Startup Repair' seems to complete the job, I'm not sure exactly what it does but it seems to be necessary for Windows 7 to boot up.

I'm surprised how hard Windows 7's automated 'Startup Repair' tries to fix Windows 7.

---

### Post by oldfred on 2013-01-22
It is my understanding that beside which boot loader to use ntldr or bootmgr, the PBR also has the start and size of the NTFS partition. That has to match the partition table or its true size or else it will not work. But chkdsk also fixes the size in the PBR if needed. Not sure what else is in PBR.

---

### Post by Herman on 2013-01-23
> It is my understanding that beside which boot loader to use ntldr or  bootmgr, the PBR also has the start and size of the NTFS partition. That  has to match the partition table or its true size or else it will not  work. But chkdsk also fixes the size in the PBR if needed. Not sure what  else is in PBR.     
 Hmmm, I might end up needing to take a closer look into that before I'm through. 

After trying to use bootrec /fixboot to repair the Windows boot sector in a logical partition returns 'Element not found', and it doesn't seem to do any good as far as booting is concerned.

There is another program that can be used instead. That program is called bootsect.exe and here's a web page showing a few different ways to go about it,[How to Rebuild the Boot Sector for Windows Vista and Windows 7.]("http://www.terabyteunlimited.com/kb/article.php?id=556") - Terabyte.

The code for installing a Windowx XP boot sector is  [FONT=Courier New, Courier, monospace][COLOR=#008800]**D:\boot\bootsect /nt52 F: **[/COLOR][/FONT]and the code for installing a Vista or Windows 7 boot sector is [FONT=Courier New, Courier, monospace][COLOR=#008800]**D:\boot\bootsect /nt60 F:**[/COLOR][/FONT] (Where D: is the CDROM drive and F" is the Windows partition).

I tried that and bootsect.exe said it has succeeded.

Unfortunately though, I still only got as far as a black screen with a blinking cursor in the top left-hand corner when I tried to chainload it from GRUB, exactly the same as I was getting before.

---

### Post by Herman on 2013-01-23
As I already mentioned in an earlier post, I was happy and impressed to find out the the Windows Installation Disk's Startup Repair Tool can actually create a new primary partition and install the boot loader files into it when Startup Repair is run twice in succession. (Providing there is a spare primary partition number available and there is enough free space on the hard disk).

I decided to see what happens when all the primary partition numbers in the hard disk are taken up by partitions formatted with Gnu/Linux file systems.
The result was System Repair didn't recognize my Windows 7 installation as a valid Windows operating system and said it couldn't fix the problems.

I tried plugging in the USB with the System Reserved partition (containing Windows 7's boot loader files) and rebooting the Installation Disk's and going to the repair utilities frame but the installation disc didn't accept the USB drive. It could run CHKDSK on it from the command line but it didn't recognise it as part of the Windows installation. I thought about trying to install a USB driver. I don't know whether that may have helped at all but I left that for a future experiment.

But the Startup Repair worked fine when BCD was installed in my other hard disk in Windows XP.
So the next thing I did was plug in my first hard drive again, the one with XP in it.
I created a new partition of 101 MiB, formatted it NTFS and labelled it 'System Reserved'. 
Then I booted the Windows 7 installation disk and my Windows 7 was listed in the Repair Utilities operating system list again, so it was recognised as a valid Windows OS.
I ran Startup Repair twice and it fixed the Windows 7 boot problem. 

Then I booted Ubuntu and took a look around to see what happened. I was hoping it would have used the 'System Reserved' partition I had made for it in my first hard disk. Instead, it installed BCD into my Windows XP again.

So Windows 7 seems to be happy with its boot loader partition in a different internal hard disk than its operating system partition, but not an external USB disk. (Even though it can easily be booted from one).  And it seems to prefer to install its boot loader into another Windows operating system instead of into an available empty partition. 
I wonder how it tells an empty partition from a Windows XP partition and it will create its own boot loader partition in an empty internal hard disk?

---

### Post by oldfred on 2013-01-23
Some of the Windows boot drive issues being discussed in this thread.
[http://ubuntuforums.org/showthread.php?t=2107126](http://ubuntuforums.org/showthread.php?t=2107126)

You can see details of PBR and the backup PBR with testdisk. The dump compares the two and it is about two pages long. Second page shows in text which boot loader it is using.

This is my XP install after using a Windows 7 chkdsk, I did not save the second page, but there seem to be a lot of differences.

Some info on Boot sector.
[http://thestarman.pcministry.com/asm/mbr/NTFSBR.htm](http://thestarman.pcministry.com/asm/mbr/NTFSBR.htm)

---

### Post by graabein on 2013-01-24
Not to interrupt the good talk here, but I managed to achieve what I wanted to do. Here's what I did:
[LIST=1]
[*]Put Windows 7 on a USB stick (NTFS)
[*]Resized a partition on the HDD leaving about 40 GB free
[*]Flagged that partition as boot (both using GParted)
[*]Disconnected the SSD which I used to boot Ubuntu 12.04 from
[*]Booted from the USB stick and put Windows 7 on the free space
[*]Finally I wrestled a bit with Windows and the BIOS before I found the right combination of boot order and boot flags (in GParted)
[*]Celebrated the victory
[/LIST]

---

### Post by graabein on 2013-01-24
and 8. Came here and thanked you guys for all the help ;)

---

### Post by oldfred on 2013-01-24
Glad you got it working. 

Herman & I did get a bit off topic as it should be about your issues. :)

---

