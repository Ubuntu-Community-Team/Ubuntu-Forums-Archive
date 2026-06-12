---
title: "Boot problem"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by krishnan t s on 2013-11-13
I had my laptop motherboard replaced today(Lenovo G505S) and booted it. It went straight to Free DOS command prompt. I figured the mbr had been overwitten. So i popped in the live cd and faced the following issues:

1. Ubuntu 13.10 amd64 bit would not boot into the desktop after clicking try ubuntu. It showed low graphics card prompt.
2. Only ubuntu 13.04 boots into the live session(try ubuntu)
3. Boot repair works. But at the end of the repair process, it shows the following: [COLOR=#000000]Please [/COLOR][COLOR=#AA22FF]**do **[/COLOR][COLOR=#000000]not forget to make your BIOS boot on                                   sda1/EFI/ubuntu/grubx64.efi file!
4. To do the same, i went into bios and happily set the efi mode as default. i rebooted the computer and there was no grub!!
5. Slightly panicking now, i set the boot priority back to legacy and tried again. Still no grub!!

To sum it up, i have the following questions:

1. Why did my 13.04 live usb work but 13.10 did not??
2. How to i restore grub and access ubuntu again??

Here is the boot info summary after boot repair: [/COLOR][http://paste.ubuntu.com/6410067/](http://paste.ubuntu.com/6410067/)
[COLOR=#000000]
Please help me soon. Thanks and have a nice day :)

[/COLOR]

---

### Post by fantab on 2013-11-13
After a major hardware upgrade like replaced Mobo, its always a great idea to re-install OS. Ubuntu is quite capable of surviving Hardware upgrades, but not always. 
Did the Graphics change with new mobo?

To answer you questions, I have no idea why 13.04 worked and 13.10 didn't.
2. Grub and OS install to HDD and not on Mobo. You didn't change your HDD, right? So its not a Grub issue. When an OS installs it installs configuring itself according to the Hardware. When there is a major hardware change the old hardware configurations don't work.

Your best bet is to RE-Install Ubuntu.
If you have DATA to be backed up then use 13.04 Ubuntu DVD/USB and BACK UP ALL YOUR IMPORTANT DATA, preferably to an External Device.

---

### Post by krishnan t s on 2013-11-13
I did backup my data(luckily :D :D ) before changing my motherboard. I guess a clean install would be cool. But if its a clean install, i would want to install 13.10. Could it be that 13.10 does not recognise my AMD Sunpro graphics card(which was not changed btw)? That dosent seem right. I'll see if i can directly install ubuntu by erasing the existing partition. I dont want to touch DOS which came preinstalled with the laptop as the thing is still under warranty.
Also, sort of off topic. The laptop heats A LOT(probable cause of mobo failure? I'm bad with hardware..). I would like to go for a cooling pad. Are there any good ones around?
Thanks for replying so quickly. Have a nice day :)

---

### Post by Bucky Ball on 2013-11-13
Boot from the 13.10 liveCD, when you get to the options screen that says 'Try Ubuntu', hit f6 key. From the options that pop up choose 'nomodset'. Proceed as normal.

Any luck?

---

### Post by krishnan t s on 2013-11-13
I erased ubuntu and reinstalled it successfully using the install ubuntu option.Try ubuntu still does not work. My flashdrive is recognised as both an EFI drive and a normal pendrive. Tried nomodeset in both. It dosent work. Is there any way i can install grub to the hdd? The hdd shows as a legacy drive but according to the boot summary info, i'm supposed to set the boot at [COLOR=#000000]sda1/EFI/ubuntu/grubx64.efi file!. Also, boot in BIOS does not show any EFI drives. Only legacy drives are shown namely, USB Drive, Hard Disk and DVD/CD Drive.
How do i do that?[/COLOR]

---

### Post by fantab on 2013-11-13
Did you disable UEFI in BIOS and set it to Legacy/CSM? How did you run your Ubuntu Pendrive, in EFI or PMAP?

> Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
[COLOR=#b22222]**Partition Table: msdos**[/COLOR]

Windows will NOT boot with UEFI from 'msdos' partition table. It needs GUID Partition Table [GPT]. And vice versa, it cannot boot in 'Legacy mode' from GPT Disk. Ubuntu/Linux can boot from GPT in 'Legacy mode' but it needs a separate 5MB Unformatted partition with 'bios-grub' flag.

As you can see you have 'msdos' partition table. So with that in place you cannot boot in EFI mode. To boot in EFI mode you need GPT. 

What can you do?
You can either disable 'UEFI/EFI' booting in BIOS and change to 'Legacy/CSM', OR use GUID Partition Table on your Disk. Either ways you may have to re-install both OS.
Changing Partition table will result in complete data loss.

---

### Post by krishnan t s on 2013-11-13
First and foremost, i do NOT have windows. I have free DOS which came preinstalled on the laptop. I installed ubuntu 13.04 initially alongside DOS a few months back. From the live cd, i installed grub to the mbr with boot-repair(recommended repair). Now after replacing my motherboard, i reinstalled ubuntu. I did not run my pendrive in EFI to install ubuntu. I wanted to replace the existing bootloader with grub to access ubuntu. In order to do that, i had to use boot repair again. But now its not going into the live session because of the low graphics problem. 
I have already changed my BIOS settings to boot from legacy i.e. where the hard drive is present. There is no entry in EFI so it dosent make any sense to boot from EFI in the first place. I just need to restore my grub. But i cant figure out how.:confused:

---

### Post by fantab on 2013-11-13
Can you post the latest BootInfo-Summary from Boot-repair. The one you posted in your first post is what I have been refering to. And it shows an EFI Parittion with:
```

Boot files: /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi /KERNEL.SYS 
                       /COMMAND.COM
```

For low-graphics use [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132") option. Have you tried it?

---

### Post by krishnan t s on 2013-11-13
I tried boot repair with the 13.04 iso again. I guess grub is installed. But all i'm able to see is a purple screen. Nothing else works.
The new boot summary info:[http://paste.ubuntu.com/6411620/](http://paste.ubuntu.com/6411620/)
Should i change the boot flag in gparted or something? it dosent seem to recognise ubuntu anymore.

---

### Post by ubfan1 on 2013-11-13
Did your replacement motherboard come with the same (or higher) firmware revision?  Sometimes you have to bring them up to date yourself.
The boot flag on the extended partition cannot be right.  I'd think it belongs on the DOS partition (DOS may need it there), or maybe the EFI partition (but since you're not booting EFI maybe not), or even the Linux ext4 partition (but Linux really does not care).  Really, with the same disk, video, ...
everything should still work.

---

### Post by krishnan t s on 2013-11-13
Mixed success. Managed to restore grub but now ubuntu will not boot!!
Advanced options also dont work. I managed to restore grub by following the instructions in [http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found)
I'm able to boot into both DOS and windows recovery. But not into ubuntu. Strange..

---

### Post by krishnan t s on 2013-11-13
Also, how do i check the motherboards firmware? and update the same?

---

### Post by oldfred on 2013-11-14
You would have to look in the UEFI/BIOS for the version number. Some systems will have it flash by just as you start to boot. Then go to vendor's site to see if they have a newer verison.

I think there is still is confusion between UEFI and BIOS boot and particularly your FAT32 partition.
In BIOS old BIOS system used a FAT partition with command.com and kernel.sys to boot. Your FAT32 partition shows those files. 
But the new UEFI uses a FAT32 partition with the boot flag to be the efi boot partition or ESP. You are showing both a ubuntu folder and a Microsoft folder with efi files. From a UEFI menu those would be bootable in UEFI mode.
Or you have both a very old (your DOS) boot and a very new boot (UEFI) in your sda1 FAT32 partition. Boot flag should be on that partition.

If you are able to boot to DOS that would be a BIOS boot and it looks like Windows recovery is a UEFI boot.

Some BIOS based installs do have issues with very large root partitions. Just because we now can create 1TB partitions does not mean we should use them for system partitions with boot files. If install is on one very large partition system may have to jump all over drive to boot. Slightly better to have a 25GB / (root) partition and use rest of drive for data or /home.

From line 387 of pastebin.
>   306.197750092 = 328.777330688  boot/grub/i386-pc/core.img                     1
   2.706390381 = 2.905964544    boot/vmlinuz-3.11.0-12-generic                 1


One file is at beginning of drive and one 1/3 of the way into drive, but still 300GB apart.

---

### Post by krishnan t s on 2013-11-15
Apologies for replying so late. I had my exam today :grin:
I have been a big idiot really. I tried something different and it worked! I wiped my flash drive clean, used unetbootin from ubuntu and flashed 13.10 again.
I tried nomodeset now and the live usb freakin works!! I thought of starting fresh.. so i wiped the ubuntu partition(only sda6) and nothing else. Now i'm very new to this area. Can someone guide me in creating a root partiton and a home partition seperately as was suggested above? how do i resize sda6? And.. how do i overwrite my mbr to boot into grub? will it be automatically done? Also, once i seperate my / and /home, how do i automatically mount my /home. Its night here.. It would be awesome if it gets solved by noon tomorrow :D

Have a nice day :)

---

### Post by oldfred on 2013-11-15
You currently have MBR(msdos) partitioning. With MBR you can only install Ubuntu or Windows so you boot with BIOS.
Ubuntu will boot from gpt partitioning with BIOS or UEFI.
Windows will only boot from UEFI with gpt partitioning.
Will you ever install Windows? Do you want to boot with BIOS or UEFI.
If you want UEFI you will have to either totally reformat or try the convertion tools that are available.
       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

            Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

    
If you know about partitions and can use gparted I prefer to create partitions in advance, but you can create as part of install. Either way if you want more than the default of / (root) and swap you have to use Something Else or manual install to choose size, mount and format of each partition. If you mount your /home during install it will automatically be part of your install in fstab. If an exisiting /home you DO NOT check format but specify mounting of it on a reinstall.

Partitioning is very personal as it depends on what you may want to use system for. 
My suggestion as a starting point. Others may have different suggestions that are just as valid.
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by krishnan t s on 2013-11-16
After careful consideration, i've come to the following conclusions:
1. I couldnt care less about DOS or windows so i dont want both of them. I want to purge them off my system completely
2. The windows recovery is useless to me as i'm never going to install or use windows on this laptop
3. I got back grub but its going into kernel panic and x server is not starting when there is no panic.

With that in mind, i want to do the following. However, i'm bad with command line( Avoid it most of the time)
1. Completely wipe all partitions(including windows recovery)
2. Convert the fresh disk from mbr(msdos) to GPT if doing so will allow me to install more than one linux distribution(the link above just went over my head)
3. Restore grub to boot ubuntu and other linux distros i want to install in legacy mode.

Please provide me with guidance on doing the same. In case there are terminal commands to be executed, please provide the same. I'll probably be doing this either tomorrow morning or only after a week or so as i'm very busy with exams and other personal stuff going on.
Thanks for everything so far and have a nice day :)

---

### Post by oldfred on 2013-11-16
I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

But you can install mulitple systems with either MBR or gpt partitioning. I have used both. It just is that with MBR you have to put most of the partitions in the extended partition as logicals.

We see many users like you who say they do not want Windows. But then come back later and want to know how to reinstall it as the have one game, application, or class that requires them to use Windows.
Best to make an image backup of your Windows so you could reinstall if necessary.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by krishnan t s on 2013-11-16
I'm most definitely not going to install or run windows on this laptop. I can assure you that. I already have a desktop and 3 fairly new laptops dual booting windows and other linux distros(mint, elementary etc etc). So if there is that one application i need that can run only in windows i'll do it with either of the 3 systems i have :)
This is the only system in my family( both close and extended) which is uefi enabled. It ran ubuntu 13.04 pretty well but a bad mobo ruined it. If it wasnt for uefi, i'd be facing lesser issues than i normally would :)
I'll see what i can do in a week or so. Have a great weekend. Cheers! :)

---

### Post by krishnan t s on 2013-11-17
I cant believe it!! Problem almost solved. I changed the boot order to boot from legacy but to boot uefi first and voila! ubuntu boots into its beautiful desktop :D :D
But i've run into another big problem. The /home partition of close to 900 GB i created during install is not getting recognised. What do i do now?

---

### Post by krishnan t s on 2013-11-17
I'm an even bigger idiot than i thought i was actually. I thought /home would be mounted as a separate partition like my ntfs drives in my other systems. I discovered just now that its mounted by default. Thanks a lot guys for all the suggestions you gave me the last few days. I'll see all links in detail once i finish my exams.
Have a great weekend. This thread is officially solved
Ciao

---

