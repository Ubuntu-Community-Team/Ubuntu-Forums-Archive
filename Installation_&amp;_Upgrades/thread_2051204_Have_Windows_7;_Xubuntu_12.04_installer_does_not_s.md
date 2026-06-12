---
title: "Have Windows 7; Xubuntu 12.04 installer does not see it though."
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by Jpendragon on 2012-09-01
Sooooo, basically the last four days straight I have devoted (and a couple of my friends have devoted) almost all my time to this problem. I may be a little wordy, but I'm trying to be as specific about my problem as I can. Also, I'm relatively new to Linux and may need instructions on the specific side, rather than vague.

I bought a new computer recently, an HP p7-1234 computer. And I wanted to split the harddrive roughly in half: half for Windows 7 (for Netflix, and any gaming I care to do), and half for Xubuntu (for school, web-browsing, torrents, and for communicating with my school's Macs).

My friend and I try to install xubuntu, but it didn't work. Please don't ask exactly why or how, I don't remember which problem it was at this point. You must understand, I spent the next several days going back and forth, doing one thing to fix a previous problem, that would create 8-9 other problems, and I probably went through about 8 total OS installation sequences in the last three days.

Everything was wiped last night though and then we reinstalled Windows 7. It is finally working. And it is only on a partition that takes up half the drive.

Specifics:
System Reserved -- 100 MB
C: -- 465.66 GB
Unallocated -- 465.76

I want to use the Unallocated space to install grub, xubuntu, and the swap space. But when I run the live USB version of Xubuntu, the installer gets to the step where you select how you want it to be partitioned, and it doesn't have an option for "Install Xubuntu alongside Windows 7." It just has "wipe drive and install Xubuntu" and "something else."
I click something else and it says That my whole drive, all 1000 GB, is free space. Which I know it is not because I am using the windows partition to post this.

On the trial xubuntu 12.04 desktop, it even shows two unmounted drives, one of 500 GB, and another that says it is "unallocated" (or something like that). I tried to mount one and nothing happened.

Neither of my friends has heard of this kind of problem before, both have installed xubuntu alongside windows before (one of them has done it many times). I am afraid to do much because I was in the same situation a day and a half ago and trying to fix the partitions ended up messing up my Windows Installation. (Resulting in the second half of that 4 days worth of struggle). That's why I decided to post here and ask if anyone knows what I am supposed to do.


Anyway, if anyone knows how to install xubuntu alongside Windows 7 when Xubuntu doesn't know the Windows exists, that would be awesome.

---

### Post by Merrattic on 2012-09-01
1. You can't mount unallocated space ;)

You may only want to create a reasonably small partition for your Xubuntu install, say 20-40gb, and create a data partition using ntfs (this will mean both Windows and Xubuntu can read the data) 

2. Choose something else (this will offer you manual partitioning and setup
2.1. Create a primary ext4 partition in the unallocated space, giving it the mount point "/"
2.2 Confirm all this the installer should offer you to create swap space do so.
2.3 Install Xubuntu

Note: there may be more steps, look at the psychocats tutorials for more help

---

### Post by ajgreeny on 2012-09-01
Can you boot again to the live Xubuntu system, then open a terminal and post the output from the command ```
sudo fdisk -lu
```
It would also be useful to see a screenshot of a gparted window;  I am pretty sure gparted is available on the live Xubuntu system without you needing to install anything to it, so just use the print screen key, save the image then attach it back here by using the paperclip icon in the toolbar, and navigating to the image you saved.

---

### Post by darkod on 2012-09-01
I would say don't try to install until you figure out why it doesn't see your win7. It's pointless to install since without seeing win7 is there it will not create a dual boot.

Boot into live mode with the cd, open terminal and post the output of:
```
sudo fdisk -l
sudo parted -l
```

The disk can show as unallocated if there is some error in the partition table. Windows often ignores some errors but linux doesn't.

Another thing, is the disk in windows Basic or Dynamic? Check in windows Disk Management for this. If it's Dynamic, don't even try to install since that is MS format and linux doesn't understand it correctly.

Also, are you using UEFI bios/boot or the older standard BIOS boot?

---

### Post by Jpendragon on 2012-09-01
> **Merrattic said:**
> 1. You can't mount unallocated space ;)

You may only want to create a reasonably small partition for your Xubuntu install, say 20-40gb, and create a data partition using ntfs (this will mean both Windows and Xubuntu can read the data) 

2. Choose something else (this will offer you manual partitioning and setup
2.1. Create a primary ext4 partition in the unallocated space, giving it the mount point "/"



1: Wasn't sure about that, but I tried mounting the 500 drive as well, and it didn't work.

1.5?: Thanks, I will look into that.

2. I would, except that the installer thinks that the whole drive is unallocated space.

---

### Post by Jpendragon on 2012-09-01
> **ajgreeny said:**
> Can you boot again to the live Xubuntu system, then open a terminal and post the output from the command ```
sudo fdisk -lu
```It would also be useful to see a screenshot of a gparted window;  I am pretty sure gparted is available on the live Xubuntu system without you needing to install anything to it, so just use the print screen key, save the image then attach it back here by using the paperclip icon in the toolbar, and navigating to the image you saved.

Here is the result of the command you said to input:
[http://imgur.com/KMVIN](http://imgur.com/KMVIN)


I took two screenshots, one of how Windows views the partitioning, and one on gparted respectively:
[http://imgur.com/zADLt](http://imgur.com/zADLt)

[http://imgur.com/qlMvu](http://imgur.com/qlMvu)


Hope this is what you meant!

EDIT: totally thought html format would work... sorry >.>

---

### Post by Jpendragon on 2012-09-01
> **darkod said:**
> I would say don't try to install until you figure out why it doesn't see your win7. It's pointless to install since without seeing win7 is there it will not create a dual boot.

Boot into live mode with the cd, open terminal and post the output of:
```
sudo fdisk -l
sudo parted -l
```The disk can show as unallocated if there is some error in the partition table. Windows often ignores some errors but linux doesn't.

Another thing, is the disk in windows Basic or Dynamic? Check in windows Disk Management for this. If it's Dynamic, don't even try to install since that is MS format and linux doesn't understand it correctly.

Also, are you using UEFI bios/boot or the older standard BIOS boot?


[http://imgur.com/ew5N6](http://imgur.com/ew5N6)

[http://imgur.com/1SwWN](http://imgur.com/1SwWN)

There are the results of the two commands you had me input. :)

It says Basic btw.

I don't know what the last part means, I'm very sorry. Ummm.... Although the word BIOS is familiar. I did enter the live usb by using the boot menu.

---

### Post by Jpendragon on 2012-09-01
Some screenshots of the Xubuntu install window.

[http://imgur.com/vdoEX](http://imgur.com/vdoEX)

Here you can see there is no option for installing alongside.
You can also see the two halves of the HDD as unmounted drives on the left on the desktop.

[http://imgur.com/UIWDu](http://imgur.com/UIWDu)
Here you can see what I get when I select the "something else" button on the last screen.
There is an obvious difference between what is in the window and what is in the desktop.

EDIT: side note: I will be leaving for work in an hour or so. I'll be able to check this page, but I will be away from the desktop that I'm writing about and will not be able to try your suggestions until 7pm central.
I will stay in contact if I can though.

---

### Post by darkod on 2012-09-01
OK, we got it. The results of fdisk -lu helped. By the way, the parameter of the commands I asked you to run -l was small L, not the number 1. That's why I posted them as code, so you can see it's curved, the L. That's why it said parameter not recognized, because you tried -1.

Anyway, you have a left over gpt backup table. It seems this disk was used with gpt partition table and then you converted it to msdos with windows. But windows doesn't delete the backup gpt table which linux can detect and it gets confused whether the disk is msdos or gpt. Use fixparts to remove the backup gpt table and you're OK.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Jpendragon on 2012-09-01
> **darkod said:**
> OK, we got it. The results of fdisk -lu helped. By the way, the parameter of the commands I asked you to run -l was small L, not the number 1. That's why I posted them as code, so you can see it's curved, the L. That's why it said parameter not recognized, because you tried -1.

Anyway, you have a left over gpt backup table. It seems this disk was used with gpt partition table and then you converted it to msdos with windows. But windows doesn't delete the backup gpt table which linux can detect and it gets confused whether the disk is msdos or gpt. Use fixparts to remove the backup gpt table and you're OK.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


Okay, I will try that tonight when I get back home. Thank you so much. :)

---

### Post by oldfred on 2012-09-01
fyi,

You can attach screen shots to your message with the little paperclip icon in the edit panel above your message.

And if results from terminal you should just copy & paste to message, but if long highlight again like copying and click on the # or code  tags to preserve formatting and make it easier to review.

Some other codes that you can use, but the most useful are already icons in edit panel:
BB Code List 
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by Jpendragon on 2012-09-01
> **oldfred said:**
> fyi,

You can attach screen shots to your message with the little paperclip icon in the edit panel above your message.

And if results from terminal you should just copy & paste to message, but if long highlight again like copying and click on the # or code  tags to preserve formatting and make it easier to review.

Some other codes that you can use, but the most useful are already icons in edit panel:
BB Code List 
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)


I'll keep the paperclip thing in mind, but I actually tried to copy and paste, but all it did was enter into the command line ^*C or something like that.

---

### Post by JKyleOKC on 2012-09-01
It's possible that your machine is set up to boot through UEFI rather than the conventional MBR approach; I bought an HP machine this past month that had that situation, and spent a frantic four days trying to get a dual-boot setup to work. OldFred finally walked me through the recovery and it's now working properly, but I never had to re-install Win7 along the way.

Can you bring up the HP Tools menu by hitting ESC on the very first screen at boot time? If so, and if you have nothing on the machine you want to retain, you might try recovering the box to factory condition via the HP Recovery entry on that menu, and starting over. I had no problem doing my initial installation of Xubuntu 12.04.1 -- the "Something else" option was there, I used it after shrinking the "OS" partition as much as possible via Win7's Disk Manager, and it showed me 228 GB of available space into which I installed Xubuntu.

UEFI seems to be the wave of the future, and it's not at all (or at least not very) compatible with all the procedures we're used to and which are coded into most installation routines...

---

### Post by Jpendragon on 2012-09-03
> **JKyleOKC said:**
> It's possible that your machine is set up to boot through UEFI rather than the conventional MBR approach; I bought an HP machine this past month that had that situation, and spent a frantic four days trying to get a dual-boot setup to work. OldFred finally walked me through the recovery and it's now working properly, but I never had to re-install Win7 along the way.

Can you bring up the HP Tools menu by hitting ESC on the very first screen at boot time? If so, and if you have nothing on the machine you want to retain, you might try recovering the box to factory condition via the HP Recovery entry on that menu, and starting over. I had no problem doing my initial installation of Xubuntu 12.04.1 -- the "Something else" option was there, I used it after shrinking the "OS" partition as much as possible via Win7's Disk Manager, and it showed me 228 GB of available space into which I installed Xubuntu.

UEFI seems to be the wave of the future, and it's not at all (or at least not very) compatible with all the procedures we're used to and which are coded into most installation routines...


I would try that, but the thing is, a friend of mine has already reinstalled and fixed up Windows the way he thinks is best twice.. I really don't want to delete that (intentionally or not) a third time. So I'm gonna give this fixedparts thing a shot before I do something that drastic. Thanks though, I will keep that in mind as a backup.

---

### Post by Jpendragon on 2012-09-03
> **darkod said:**
> OK, we got it. The results of fdisk -lu helped. By the way, the parameter of the commands I asked you to run -l was small L, not the number 1. That's why I posted them as code, so you can see it's curved, the L. That's why it said parameter not recognized, because you tried -1.

Anyway, you have a left over gpt backup table. It seems this disk was used with gpt partition table and then you converted it to msdos with windows. But windows doesn't delete the backup gpt table which linux can detect and it gets confused whether the disk is msdos or gpt. Use fixparts to remove the backup gpt table and you're OK.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


Okay, so for the last day or so I've been reading up on this fixparts thing you sent me, looking through the tutorial and whatnot. I decided to give a shot to the first thing it tells me to do, which is to backup my partition table by typing "sfdisk -d dev/sda > part.txt" or something like that. And it gives me this error. "sfdisk: cannot open /dev/sda for reading"

What perhaps did I do wrong? (Yes, I already checked, and sda is the device that I'm wanting to backup. ) I am however running the trial version of xubuntu to do this because the whole process seemed like it was going to be easier, as well as the fact that much of the software involved was already installed.

---

### Post by darkod on 2012-09-03
> **Jpendragon said:**
> Okay, so for the last day or so I've been reading up on this fixparts thing you sent me, looking through the tutorial and whatnot. I decided to give a shot to the first thing it tells me to do, which is to backup my partition table by typing "sfdisk -d dev/sda > part.txt" or something like that. And it gives me this error. "sfdisk: cannot open /dev/sda for reading"

What perhaps did I do wrong? (Yes, I already checked, and sda is the device that I'm wanting to backup. ) I am however running the trial version of xubuntu to do this because the whole process seemed like it was going to be easier, as well as the fact that much of the software involved was already installed.

Not sure about that message. Personally I have never needed to do this since I never was in a situation with gpt leftover backup table.

I know from this forum and people who had this issue that the fixparts helps. All of them reported success. You can try it without doing the backup table first, it's not a huge risk in my opinion. But the choice is yours.

Maybe oldfred will know more about this error if he pops in.

---

### Post by Jpendragon on 2012-09-03
> **darkod said:**
> Not sure about that message. Personally I have never needed to do this since I never was in a situation with gpt leftover backup table.

I know from this forum and people who had this issue that the fixparts helps. All of them reported success. You can try it without doing the backup table first, it's not a huge risk in my opinion. But the choice is yours.

Maybe oldfred will know more about this error if he pops in.

Okay, well thank you so much still for all your help. You are awesome and you get 42 internets from me. :D

---

### Post by haresear on 2012-09-03
> **Jpendragon said:**
> Okay, so for the last day or so I've been reading up on this fixparts thing you sent me, looking through the tutorial and whatnot. I decided to give a shot to the first thing it tells me to do, which is to backup my partition table by typing "sfdisk -d dev/sda > part.txt" or something like that. And it gives me this error. "sfdisk: cannot open /dev/sda for reading"

What perhaps did I do wrong? (Yes, I already checked, and sda is the device that I'm wanting to backup. ) I am however running the trial version of xubuntu to do this because the whole process seemed like it was going to be easier, as well as the fact that much of the software involved was already installed.

This is a long shot, but I notice that your first quoted command string ("sfdisk -d dev/sda > part.txt") is missing the first forward slash before "dev" (i.e. it should be "sfdisk -d /dev/sda > part.txt" -- unless you issued the command from the root directory). If that was just a typing error, and you actually issued the correct command, just ignore my comment.

---

### Post by Jpendragon on 2012-09-03
> **haresear said:**
> This is a long shot, but I notice that your first quoted command string ("sfdisk -d dev/sda > part.txt") is missing the first forward slash before "dev" (i.e. it should be "sfdisk -d /dev/sda > part.txt" -- unless you issued the command from the root directory). If that was just a typing error, and you actually issued the correct command, just ignore my comment.

Yeah it was just a typo.

---

### Post by haresear on 2012-09-03
I'm not familiar with fixparts nor gpt structure, but if you now have a standard old style MBR and partition table, you could back that up with the 'dd' command, e.g.
```
dd if=/dev/sda of=part.txt bs=512 count=1
```

You might need sudo in front if permission is denied.

If you google "dd if=/dev/sda" you'll get more info on partition table backup and restore.

---

### Post by Jpendragon on 2012-09-03
Fixparts got rid of the old GUID data, but unfortunately I can't get grub to load. It will put linux next to my Windows partition, it sees the partitions just fine. But when I turn it on I get this message:

"Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel CorporationF: Exiting PXE ROM.

ERROR: No boot disk has been detected or the disk has failed."

I removed the partitions with linux and the swap space and it is still giving me this message.

---

### Post by darkod on 2012-09-03
Don't remove partitions before trying to fix the problem, it will rarely do any good.
Since you have removed the partitions, do another install now. If it still does the same, boot into live mode and post here, we will try to sort it out.

---

### Post by Jpendragon on 2012-09-03
> **darkod said:**
> Don't remove partitions before trying to fix the problem, it will rarely do any good.
Since you have removed the partitions, do another install now. If it still does the same, boot into live mode and post here, we will try to sort it out.

I thought since it worked without those partitions, that they must be the problem. Error in judgement I know.

I did reload it, and then I ran something called a "boot repair" it fixed grub. Grub and Xubuntu now work, but Windows somewhere down the line got pissy with me.

"Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or your computer manufacturer for assistance.

Status 0xc000000e

Info: The boot selection failed because a required device is inaccessible."

A friend of mine has a Windows 7 disc (my comp didn't come with one). Should I run the "repair your computer" command, or will this undo everything linux related?

Linux can actually see all my Windows files in it's file manager if that helps. So I know the information is still there.

---

### Post by oldfred on 2012-09-03
You can make a repairCD or USB as long as both are 32 bit or both are 64 bit.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You often have to run the auto repairs 3 times and one of those will reinstall the Windows boot loader to the MBR. You then can test that Windows boots directly, Then reinstall grub2's boot loader and run sudo update-grub once in Ubuntu.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Or just use Boot-Repair. Will not fix the Windows issues but will reinstall grub2's boot loader and make other fixes if required.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Jpendragon on 2012-09-03
> **oldfred said:**
> 
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
.

So..... I followed these instructions, and restarted my computer, and suddenly Windows worked.... I have no f***ing clue what happened (pardon my french...). I'm going to reboot about five times now to make sure this is true...

---

### Post by oldfred on 2012-09-03
That should have just created a repairUSB to boot not by itself fix it?? From that repairUSB then you should be able to fix it.

---

### Post by Jpendragon on 2012-09-03
> **oldfred said:**
> That should have just created a repairUSB to boot not by itself fix it?? From that repairUSB then you should be able to fix it.


I know, that's why I'm so confused. But I'm reluctant to do anything now that everything is relatively close to how I wanted it.

Okay, actually I was a little inaccurate in the the moment I wrote that. I tried to do that, but instead just burned it to a CD. I turn it on and was going to try to load the CD, but suddenly Windows says ~~"Windows didn't shut down properly. Do you want us to start normally or look into it?" I start normally and it works.

Now here is the really confusing bit. I turn it on and Grub loads up. It gives me four options.

xubuntu
xubuntu (recovery mode I think)
Windows Boot Loader sda1
Windows Boot Loader sda2

sda2 still gives me that error message, but sda1 loads Windows 7 perfectly and that it has 500 Gb. But when I turn on xubuntu, it claims that sda1 is the windows system recovery partition (the 100 Mb thing), and that sda2 is my 500 Gb windows drive.

[http://i3.kym-cdn.com/entries/icons/original/000/004/592/my-brain-is-full-of-****.jpg](http://i3.kym-cdn.com/entries/icons/original/000/004/592/my-brain-is-full-of-****.jpg)

---

### Post by JKyleOKC on 2012-09-03
The partition numbers are assigned in the sequence that the partitions respond during the boot sequence, and it's not uncommon for them to vary from one boot to the next -- especially if any hardware is added or removed. That's why the various flavors of Ubuntu use UUIDs for the device names (by default) rather than using the partition numbers.

Thunar (the Xubuntu file manager) should show you both Windows partitions, probably labeled according to their sizes, in the sidebar. Can you verify that they are both accessible from there? If so, it's probably all good and does not need additional fixing...

---

### Post by oldfred on 2012-09-03
Windows normally has a hidden 100MB boot/repair partition that Windows calls the recovery partition. It is not the vendor recovery partition which is usually 10 to 20GB to hold an image of the hard drive as purchased. Often the vendor recovery is seen by grub as a bootable partition.

If you repair the main Windows or c: drive that may add all the boot files back into that partition. Windows will work from that also if correctly configured. You may be able to run repairs on that and then either will boot without issue.

Many users just hide recovery boots to not see them. You can use grub customizer to hide or adjust grub entries.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

