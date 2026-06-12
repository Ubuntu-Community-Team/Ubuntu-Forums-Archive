---
title: "Accidentally deleted Windows 8 and Ubuntu wouldn't install"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by Hadi_ on 2014-12-13
Don't laugh at me >.< But here's the story. I know I shouldn't have messed with things I have no knowledge of...silly, stupid me u.u 

So, before I get into the details, I'll say something that I **will **allow you to laugh at me for: Lazy, ignorant me did not back up Windows 8 before this whole thing. I don't know why, but I thought I wouldn't need to. And I was too lazy. Bleh, stupid me, right?

Anyway, so I'd been hearing about this cool "Linux" thing and decided to try it. After some research, I found that Ubuntu is generally known as the best if not one of the best distros for beginners. So I decided to try it. Watched a tutorial, then started the process of installing Ubuntu.

So, I used a program to create a Live USB for installation. Made the USB, then went to Disk Manager to do partitioning so I could install Linux. I'm not sure what the hell I did with partitions, but I think I messed some up. I had no idea what I was dealing with, and up until then, didn't know a thing about the existence of hard drive partitions. I might've found some weird, and being very curious (and foolish), I might've messed around with them a bit too much. Anyway, in the end, I had a decent amount of free space to install Ubuntu in. 

So I turned off fast boot and secure boot, as all the tutorials told me to do, and booted the Live USB. Used the "Try Out" option to try the OS out before installing, and I liked it. So I went to install. I noticed that unlike the tutorial I watched, I didn't have the "Install alongside Windows 8" option. So I checked out a few more tutorials to find a solution. I found one, and it required me to choose the "Something else" option and do stuff with partitions. Here is where I had to mess around with partitions. I don't really remember, it might've been in the partition table on the installer or it might've been in he Windows Disk Manager. In any case, you should get the point by now: [I]I might've messed with stuff in ways I should'nt have.  
[/I]
I thought everything was going the way it was supposed to and installed Ubuntu. Took out the Live USB and rebooted, but it just booted into Windows. I inserted the USB again and rebooted again, and it just took me to the menu you see at first, that has the options to either try or install Ubuntu. Point is, Ubuntu either didn't really install or wasn't being booted into. Tried to fix stuff by following tutorials more closely and installed Ubuntu multiple more times, but nothing was working. 

About the 4th time around, careless me accidentally clicked the "Wipe the hard drive and install Ubuntu" option on the installer....and, when Ubuntu won't actually boot, that's a huge problem. Rebooted my computer, and it had nothing to boot into. I pretty much had a computer with no OS. I then installed Windows 8 using a new installation disk (**if only I had freaking backed up Windows 8 before this whole mess**) and decided not to mess with linux until I knew what the hell I was dealing with. Well, here I am, with no more knowledge than I had before. And wanting to mess with linux again.

Recently, I partitioned my hard drive to make free space again and booted Ubuntu from the Live USB. Went to the installation, only this time, on the partitions table I see after clicking the "Something Else" option, I don't see my actual partitions. All my disk space is just one "partition", labeled "free space". I'm not sure what's not letting the installer recognize my Windows OS or my disk partitions. But I think it has something to do with the fact that my partitions don't look the same as they did before the whole mess. Here's a screenshot:
[IMG]http://i.gyazo.com/00da8532d65b0a7ba6460018dbb6f72f.png[/IMG]

Did a bit of research today and found that I seemed to be missing the EFI partition, which is very necessary for not only Ubuntu installation but my system, too, I guess. How do I make an EFI partition?
Also, how come my whole hard disk is shown as free space? How can I fix this? How can I...well, fix the issues my system has and install Ubuntu? It's clear to me that my computer isn't the same as before. I want to fix that so I can start fresh with dual-booting linux.

As you can see, I have little to no knowledge of what goes on in my computer and generally what I'm dealing with. I'm looking to change that , though...someday. Also, I know I deserve criticism for my carelessness, but try not to make it too harsh, please.

---

### Post by agillator on 2014-12-14
Don't feel bad. There are two kinds of people: those who will, and those who have. You have moved from the first to the second category. Congratulations. You probably won't make those mistakes again.

Are you working with a desktop or a laptop? From what you showed from Disk Management I would assume a desktop. Laptops can be a real pain. 

Someone else will have to help you with the EFI business, I have thankfully not had to deal with that yet. However, from what you have posted your entire hard disk is not free space. You have a Windows partition that appears to be about half the disk. Of that partition, only thirty something gigs is filled at the moment, which would be about right for a recent installation. The rest of THAT partition is empty, waiting to be filled. The other half of the drive is unallocated, i.e. it has not been partitioned and is not available for use yet. You could have done this when you manually repartitioned. It could also happen if, after you reinstalled Windows, you attempted to install Linux. Generally Windows, the stupid, greedy s.o.b., will use the entire hard disk which is why you load it first on a dual boot system. Then if you tell the Linux installer to install 'beside' Windows it will try to use up to half the hard disk, shrinking Windows and using some of the unused space. It looks as if that is what happened but then Linux could not or did not install for one of many possible reasons. During an installation, if you use the 'other partition' method just tell the installer to use the unallocated space by creating a partition (ext4, probably) there. Don't forget to also create a 'swap' partition, normally twice the size of your memory, there, too. After installation, the Linux installer will install a boot loader, GRUB, at least in pre-EFI days. This is what gives you the choice of which system to boot. 

That is how the installation went prior to EFI. I have described it in hopes that it will make some sense to you so you can understand what is going on. From here someone will have to explain the EFI parts to you, but hopefully I have given you a decent foundation for them to build upon.

Finally, when working with computers remember a couple of things. First, Murphy is alive, well and active. Second, computers are NOT inanimate objects. They have evil souls and are out to take over the world (and doing a fine job of it, I might add). One must always keep one's computer afraid of one by reminding it that YOU know where the power cord is and how to unplug it and/or to remove the battery. Sometimes judicious application of the "If at first you don''t succeed, get a bigger hammer" rule is also appropriate.

---

### Post by coldraven on 2014-12-14
If it's a desktop then maybe the easiest option would be to install a second hard drive and put Ubuntu on it. Sorry but I don't use Windows so I cannot help you there.
Congratulations for keeping your sense of humour after your boo-boo :)

---

### Post by Gordonbp531 on 2014-12-14
OK. Do a Reset of your computer to factory specs. (See your User Manual or the Manufacturer's website on how to do this). That will restore all the disk partitions to their correct format.

then:
1. Boot into Windows and create the free space on the HDD using Disk Manager. Do  NOT use GParted to do this as there have been incidences of this borking the Windows install.
2. Shut down the computer. Do not bother to turn off UEFI.
3. Boot from the live USB.
4. Click on the "Install Now" icon.
5. Select the "Something Else" option.
6. Create 3 new partitions in the unallocated space - 30GB for the OS, mounted at /, a partition for data, mounted at /Home and a Swap partition, usually 1.5 or 2x your amount of RAM
7. Install GRUB on the EFI partition.

HTH

---

### Post by oldfred on 2014-12-14
If you only have the 100MB boot partition and the main C: "drive" of Windows you have converted your system from UEFI to BIOS. 
Windows only boots in UEFI mode on gpt partitioned drives.
Both Ubuntu and Windows only boot from MBR(msdos) drives with BIOS.

But when you install Windows in BIOS mode over a gpt or UEFI system, it does not correctly convert drive from gpt to MBR. It leaves the backup gpt partition table. Then Linux tools see both MBR and gpt and assume you can only erase drive and select one or the other. You need to use fixparts to remove backup gpt partition table or reinstall Windows in UEFI mode.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Your hardware is UEFI and BIOS or UEFI has CSM.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

The two boot modes are not compatible so once you start booting in one mode you cannot switch. So how you boot install media for both Windows or Ubuntu is how it will install. You can install Ubuntu in BIOS mode on a Windows UEFI boot system, but then grub will not be able to boot Windows from its menu as is is not in same boot mode. So you want all systems installed in the same boot mode.

Your UEFI boot menu should have two boot options for installer. One usually is clearly UEFI and name/label of flash drive and the other is just the label of flash drive which then is the BIOS boot.

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Hadi_ on 2014-12-19
> **agillator said:**
> Don't feel bad. There are two kinds of people: those who will, and those who have. You have moved from the first to the second category. Congratulations. You probably won't make those mistakes again.

Are you working with a desktop or a laptop? From what you showed from Disk Management I would assume a desktop. Laptops can be a real pain. 

Someone else will have to help you with the EFI business, I have thankfully not had to deal with that yet. However, from what you have posted your entire hard disk is not free space. You have a Windows partition that appears to be about half the disk. Of that partition, only thirty something gigs is filled at the moment, which would be about right for a recent installation. The rest of THAT partition is empty, waiting to be filled. The other half of the drive is unallocated, i.e. it has not been partitioned and is not available for use yet. You could have done this when you manually repartitioned. It could also happen if, after you reinstalled Windows, you attempted to install Linux. Generally Windows, the stupid, greedy s.o.b., will use the entire hard disk which is why you load it first on a dual boot system. Then if you tell the Linux installer to install 'beside' Windows it will try to use up to half the hard disk, shrinking Windows and using some of the unused space. It looks as if that is what happened but then Linux could not or did not install for one of many possible reasons. During an installation, if you use the 'other partition' method just tell the installer to use the unallocated space by creating a partition (ext4, probably) there. Don't forget to also create a 'swap' partition, normally twice the size of your memory, there, too. After installation, the Linux installer will install a boot loader, GRUB, at least in pre-EFI days. This is what gives you the choice of which system to boot. 

That is how the installation went prior to EFI. I have described it in hopes that it will make some sense to you so you can understand what is going on. From here someone will have to explain the EFI parts to you, but hopefully I have given you a decent foundation for them to build upon.

Finally, when working with computers remember a couple of things. First, Murphy is alive, well and active. Second, computers are NOT inanimate objects. They have evil souls and are out to take over the world (and doing a fine job of it, I might add). One must always keep one's computer afraid of one by reminding it that YOU know where the power cord is and how to unplug it and/or to remove the battery. Sometimes judicious application of the "If at first you don''t succeed, get a bigger hammer" rule is also appropriate.

Thanks for the explanation. Now I can make sense of all the UEFI/BIOS and boot manager nonsense I read so much about but just confused myself with. To answer your questions, it's a desktop, and I had made the unallocated space myself before taking the screenshot.

And lmao @the last part.

> **Gordonbp531 said:**
> OK. Do a Reset of your computer to factory specs. (See your User Manual or the Manufacturer's website on how to do this). That will restore all the disk partitions to their correct format.

then:
1. Boot into Windows and create the free space on the HDD using Disk Manager. Do  NOT use GParted to do this as there have been incidences of this borking the Windows install.
2. Shut down the computer. Do not bother to turn off UEFI.
3. Boot from the live USB.
4. Click on the "Install Now" icon.
5. Select the "Something Else" option.
6. Create 3 new partitions in the unallocated space - 30GB for the OS, mounted at /, a partition for data, mounted at /Home and a Swap partition, usually 1.5 or 2x your amount of RAM
7. Install GRUB on the EFI partition.

HTH

Did this and successfully installed Ubuntu. Thanks!! Unofortunately, I couldn't boot back into Windows and never saw the GRUB menu. But I fixed the problem with boot-repair and can FINALLY boot into the OS of my choosing with the GRUB menu I'm finally seeing. 

Thanks for the help guys! Really appreciate it. Now everything is, for once, the way it should be.

---

