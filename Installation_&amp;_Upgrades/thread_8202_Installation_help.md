---
title: "Installation help"
date: 2004-12-15
forum: Installation &amp; Upgrades
---

### Post by firstbishop on 2004-12-15
I'm reasonably new to Linux, but have had a little experience with Mandrake 9.1. I've spent the last day or so trying to install Ubuntu from the CD's that were posted to me.

The PC I am using is brand new and has no pre-installed operating system on it. The chip is a P4 2.8GHz, the hard drive an 80M Maxtor. 256MB RAM

The entire Ubuntu install process seems to have run fine,  but when I remove the CD and reboot, the computer searches the hard drive, eventually gives up and looks to the CD drive. At this point a message appears to the effect that a system disk needs to be inserted.

I've tried some of the various install parameters, but my machine doesn't seem to fall into any of the special categories mentioned. I've looked around the BIOS settings, but can't spot any obvious problems.

I'd be very grateful for any pointers. 

Thanks

Mike

---

### Post by Original Brownster on 2004-12-15
Hi,
Can you remember at the disk partitioning stage what you did?
If you accepted the default or did you do your own partitioning?  
Just wondering if you marked a partition as bootable?

At the stage where the boot loader Grub is being installed, what option did you choose?

---

### Post by firstbishop on 2004-12-16
Thanks for your reply.

The first time I ran the installation, I interfered as little as possible and just accepted any defaults that were offered - partitions included. On one of my subsequent attempts, I remember specifically setting the root partition to be bootable, but the system still wouldn't boot.

After all the different things I'd tried, I eventually took the PC back to the guy who sold it to me and asked him to have a look at the hard drive. He then deleted all the partitions and attempted an XP installation. He found that although he could run through the whole installation, he couldn't boot from the hard drive at the end of it. 

His theory is that the Ubuntu installation may have affected the boot sector in some way - but he really wasn't sure what the problem was...  In any event, they're going to replace the drive - which is pretty decent of them if it was the Ubuntu installation (or the ignorant user!) at fault.

Is this something to do with the hard disk? BIOS settings? Or was there something I missed during the Ubuntu installation?

Your second question about the grub bootloader - the installer correctly identified that there was no existing operating system installed and it suggested that GRUB  could be installed in the boot sector (or MBR - I can't reremember the exact term). I chose to follow that option.

---

### Post by gheorghe_pop on 2004-12-16
:)
I don't tink it's neider Ubuntu or The user.It's a hardware problem(bad hdd or the master jumper isn't set).

---

### Post by firstbishop on 2004-12-17
Thanks, I'll have another look at it today when the new HDD comes back.

---

### Post by Original Brownster on 2004-12-17
Hi,
Yes it sounds like a faulty disk.  If the boot sector is damaged that would be the cause. As far as I know it would be impossible to physically damage a sector purely by installing an operating system!  Unless of course Ubuntu has used some 'demonic power' to crash the heads into the sector !  :lol:

---

### Post by Hellsteeth on 2004-12-17
I hope the absolute obvious was checked in the BIOS that the boot order was set appropriately? My pc has many boot order options one of which is CD only!

---

### Post by firstbishop on 2004-12-20
Thanks, but the boot sequence was right I think.

This weekend I started again with a brand new HDD. First I set up an NTFS and a FAT partition for XP (Home),  then ran the XP installation. Everything went fine and I was able to boot up the Windows system from the hard drive.

I then attempted another Ubuntu installation. Using expert mode, I allowed the installer to create two partitions (root ext3 and swap partition). Towards the end of the installation, the installer told me that it had detected XP on another partition but that it would be safe to install the grub bootloader in the MBR. I chose that option and when the system rebooted I couldn't start up Ubuntu (or Windows!).

I read somewhere in this forum that you can fix a Windows installation using the recovery console, so I tried that and ran the fixmbr command - no success. I then tried the fixboot command and although Windows kept giving me encouraging messages, the system still won't boot.

I have tried deleting all the partitions, reformatting them, reinstalling Windows, but although the first stage of the install always seems to work, the system will never perform once it is asked to boot from the hard drive.

This time around the problem is clearly not with the HDD. Can it be that the Ubuntu installer is able to play havoc with the boot sequence of my hard disk, to such an extent that I now can't even install another operating system?

I'd be hugely grateful for any help!

---

### Post by Rhodan on 2004-12-20
[QUOTE=firstbishop]Thanks, but the boot sequence was right I think.

This weekend I started again with a brand new HDD. First I set up an NTFS and a FAT partition for XP (Home),  then ran the XP installation. Everything went fine and I was able to boot up the Windows system from the hard drive.

I then attempted another Ubuntu installation. Using expert mode, I allowed the installer to create two partitions (root ext3 and swap partition). Towards the end of the installation, the installer told me that it had detected XP on another partition but that it would be safe to install the grub bootloader in the MBR. I chose that option and when the system rebooted I couldn't start up Ubuntu (or Windows!).

I read somewhere in this forum that you can fix a Windows installation using the recovery console, so I tried that and ran the fixmbr command - no success. I then tried the fixboot command and although Windows kept giving me encouraging messages, the system still won't boot.

I have tried deleting all the partitions, reformatting them, reinstalling Windows, but although the first stage of the install always seems to work, the system will never perform once it is asked to boot from the hard drive.

This time around the problem is clearly not with the HDD. Can it be that the Ubuntu installer is able to play havoc with the boot sequence of my hard disk, to such an extent that I now can't even install another operating system?

I'd be hugely grateful for any help![/QUOTE]
 Howzit firstbishop, I see you from South Africa as well !

If you run the XP installation process again, and continue to the point where it says press "enter" to install a new OS or press "R" to do a repair, press "R" and that should fix the XP install for you. Basically Linux has taken over the boot record of the drive. If you have a dos boot disk, you could always boot off that and run "fdisk /mbr" and that should fix it as well.

Ubuntu should be installing grub to the boot record so it can find it when it boots up. You can download a dos disk from [www.bootdisk.com](www.bootdisk.com) .

---

### Post by firstbishop on 2004-12-20
That's why I couldn't resist Ubuntu :) 

I have tried the repair option using the Windows installation CD - neither fixmbr or fixboot worked for me. If you think the dos boot disk will help, I'll try the fdisk option too.

---

### Post by OLE on 2004-12-20
[QUOTE=firstbishop]That's why I couldn't resist Ubuntu :) 

I have tried the repair option using the Windows installation CD - neither fixmbr or fixboot worked for me. If you think the dos boot disk will help, I'll try the fdisk option too.[/QUOTE]

Had a similar problem. Try explicitly set the HDD Mode from "Auto" to "LBA" or "Large". Worked for me -- my problem had exactly the same symptom as yours.

---

### Post by Rhodan on 2004-12-20
[QUOTE=firstbishop]If you think the dos boot disk will help, I'll try the fdisk option too.[/QUOTE]

I'm talking not talking about the recovery console, the step I'm talking about should be further on, where you press F8 for the license agreement. Try it again and let us know. 

Also try setting the hard drive mode to LBA or Large as suggested above.

Whats the specs of your pc ?

---

### Post by firstbishop on 2004-12-20
I vaguely remember trying the Large / LBA option without any luck, but I'll have another look at that - the symptoms do look similar to the other case discussed in this forum.

And I must have been half asleep when wading through the installation screens - I didn't see any additional repair options at all. Thanks - I'll try that too.

Off the top of my head, the PC specs are:

Pentium 4 chip - 2.8GHz. (Couldn't tell you anything about the motherboard offhand)
80G Maxtor HDD
256M RAM 
15 IQ user...

We'll see how this all goes this evening, when I return to the field of battle.

Thanks for your input

---

### Post by Rhodan on 2004-12-20
[QUOTE=firstbishop]I vaguely remember trying the Large / LBA option without any luck, but I'll have another look at that - the symptoms do look similar to the other case discussed in this forum.

And I must have been half asleep when wading through the installation screens - I didn't see any additional repair options at all. Thanks - I'll try that too.

Off the top of my head, the PC specs are:

Pentium 4 chip - 2.8GHz. (Couldn't tell you anything about the motherboard offhand)
80G Maxtor HDD
256M RAM 
15 IQ user...

We'll see how this all goes this evening, when I return to the field of battle.

Thanks for your input[/QUOTE]
 Well at least you getting it installed, I can't even get past the initial installation stage ! 

I downloaded the latest "hoary" release, will try that tonight, if you still having problems maybe try that as well if you can get hold of it ?

Let us know how you get on with your install.

---

### Post by firstbishop on 2004-12-21
Still no success. I tried setting the HDD to LBA or Large and both settings return a Disk Read Error (and invite me to press Ctrl-Alt-Del to continue...)

As for the repair options under XP (Home, not Professional), the only options I see are when I can choose to Install, Repair or Exit. Choosing repair takes me to the Recovery Console (and Fixmbr and Fixboot don't seem to fix anything). If I continue with the installation, I am asked to press F8 to agree to the generous MS licensing terms and then taken to the screen which invites me to reformat my drive (which I have attempted, but without being able to reboot once the setup files are copied to the drive).

I don't know where to go from here. FYI, here are some of the other bits and pieces that may be helpful:

The motherboard is a MS-6540G (v2.X) Micro ATX Mainboard (661FM series) - based on the SiS 661FX and SiS 963/963L chipsets.

At some stage last night, having failed with the XP installation, I attempted another Ubuntu installation. The install seemed to start fine, but then returned a CRC error, with the message "System halted". Trying again after rebooting, the message persisted, but then on a subsequent attempt disappeared and the install appeared to run normally. I tried using other install CD's from the pack I was posted and the same behaviour continued.

One time, the machine froze at this point:

"Ramdisk Compressed image found at block 0
crc error
VFS: Mounted root (ext2 filesystem)
mounted devfs on /dev
Freeing unused kernel memory 204 k freed"

When I have managed to complete the entire installation (whether choosing grub or lilo as bootloader), I see the message "Rebooting into your new Ubuntu system". Once the computer has rebooted, it searches the hard drive and eventually stops at "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

Any ideas?

---

### Post by firstbishop on 2004-12-21
Still no success. I tried setting the HDD to LBA or Large and both settings return a Disk Read Error (and invite me to press Ctrl-Alt-Del to continue...)

As for the repair options under XP, the only options I see are when I can choose to Install, Repair or Exit. Choosing repair takes me to the Recovery Console (and Fixmbr and Fixboot don't seem to fix anything). If I continue with the installation, I am asked to press F8 to agree to the generous MS licensing terms and then taken to the screen which invites me to reformat my drive (which I have attempted, but without being able to reboot once the setup files are copied to the drive).

I don't know where to go from here. FYI, here are some of the other bits and pieces that may be helpful:

The motherboard is a MS-6540G (v2.X) Micro ATX Mainboard (661FM series) - based on the SiS 661FX and SiS 963/963L chipsets.

At some stage last night, having failed with the XP installation, I attempted another Ubuntu installation. The install seemed to start fine, but then returned a CRC error, with the message "System halted". Trying again after rebooting, the message persisted, but then on a subsequent attempt disappeared and the install appeared to run normally. I tried using other install CD's from the pack I was posted and the same behaviour continued.

One time, the machine froze at this point:

"Ramdisk Compressed image found at block 0
crc error
VFS: Mounted root (ext2 filesystem)
mounted devfs on /dev
Freeing unused kernel memory 204 k freed"

When I have managed to complete the entire installation (whether choosing grub or lilo as bootloader), I see the message "Rebooting into your new Ubuntu system". Once the computer has rebooted, it searches the hard drive and eventually stops at "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

Any ideas?

---

### Post by KiwiNZ on 2004-12-21
I would suggest returning your PC to a known state . That is delete all partitions and reset your Bios setting to factory set .
 Then  install Windows , (leaving sufficient unpartitioned space to install Ubuntu).
 Ensure Windows is working without any errors .
 Then install ubuntu using allthe suggested defaults and following all on screen instructions.

---

### Post by Rhodan on 2004-12-21
[QUOTE=firstbishop]Still no success. I tried setting the HDD to LBA or Large and both settings return a Disk Read Error (and invite me to press Ctrl-Alt-Del to continue...)

As for the repair options under XP (Home, not Professional), the only options I see are when I can choose to Install, Repair or Exit. Choosing repair takes me to the Recovery Console (and Fixmbr and Fixboot don't seem to fix anything). If I continue with the installation, I am asked to press F8 to agree to the generous MS licensing terms and then taken to the screen which invites me to reformat my drive (which I have attempted, but without being able to reboot once the setup files are copied to the drive).

I don't know where to go from here. FYI, here are some of the other bits and pieces that may be helpful:

The motherboard is a MS-6540G (v2.X) Micro ATX Mainboard (661FM series) - based on the SiS 661FX and SiS 963/963L chipsets.

At some stage last night, having failed with the XP installation, I attempted another Ubuntu installation. The install seemed to start fine, but then returned a CRC error, with the message "System halted". Trying again after rebooting, the message persisted, but then on a subsequent attempt disappeared and the install appeared to run normally. I tried using other install CD's from the pack I was posted and the same behaviour continued.

One time, the machine froze at this point:

"Ramdisk Compressed image found at block 0
crc error
VFS: Mounted root (ext2 filesystem)
mounted devfs on /dev
Freeing unused kernel memory 204 k freed"

When I have managed to complete the entire installation (whether choosing grub or lilo as bootloader), I see the message "Rebooting into your new Ubuntu system". Once the computer has rebooted, it searches the hard drive and eventually stops at "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

Any ideas?[/QUOTE]
 Try deleting all the partitions on the drive, and then try installing Ubuntu using the expert mode, it asks you a few more questions but they are straight forward. I did this last night and managed to get my Ubuntu install to work without a problem, so I'm now typing this from Ubuntu !

If you want to try recover your XP installation first, boot off the Ubuntu cd, get to the partitioning step and set your XP partition as bootable, delete the other linux partiitions and then write the changes to disk and reboot, your XP installation should boot fine then.

Cheers

---

### Post by firstbishop on 2004-12-21
I've brought my box to work today, and have tried your suggestions:

I reset the BIOS settings to their optimized defaults, deleted all the partitions and created a 20G NTFS partition, ran the Windows installation, which as previously seemed to go without incident until the system attempted to reboot.

I then tried Rhodan's suggestion and booted from the Ubuntu install disk (eventually after having to reboot three or four times due to crc errors). When I reached the partition stage, I chose the option to manually edit the Windows NTFS partition. It was already set as bootable. I unset it and reset it, saved changes, exited from the installation and still the system would not boot from the hard disk.

I would think that this was a hard disk problem were it not for the fact that Windows installed fine before I attempted to install Ubuntu.

---

### Post by Rhodan on 2004-12-21
Hmmm, sounds like the ubuntu disc isn't happy, can you burn another copy or not ?

Are you able to go to [www.bootdisk.com](www.bootdisk.com) and download a dos 6.22 disk and create a bootable disk. Boot off the disk and run fdisk and delete everything, then reboot and boot off the disk again and run fdisk /mbr. Now try install XP again.

My msn address is [email]rhodan@ananzi.co.za[/email], I'm online now if you want to chat.

---

### Post by firstbishop on 2004-12-21
I was sent 10 Ubuntu disks and have tried several of them along the way.

I downloaded the DOS 6.22 disk and booted with it. It spent some time looking for the hard drive and then finally brought me to the A: prompt. I couldn't access the C: drive and fdisk gave me an error (something like error reading / locating fixed disk).

Also tried downloading a utility called MBRTool mentioned elsewhere in this forum. It also couldn't read the C: drive, although it worked fine on another PC.

 :confused:

---

### Post by Rhodan on 2004-12-21
Did fdisk start up and show you the partitions, it would not be able to read them, but as long as you can delete them ?

Did you try typing "fdisk /mbr" ?

---

### Post by firstbishop on 2004-12-21
Should have read your last post more carefully. Rhodan you're a star! I've been banging my head against thing all day and suddenly XP is back in the land of the living!

Thanks very much for your help.

Now to attempt to get XP to share its home with Ubuntu ...

---

### Post by Rhodan on 2004-12-21
Great ! Let us know how you get on with it will you  :-D

---

### Post by firstbishop on 2004-12-22
Right! Now we're getting close.

Last night, once I had XP up and running again, I tried installing Ubuntu again. More crc errors, but eventually was able to run the installer in expert mode. I made a point of not installing Grub to the MBR. Result? XP wouldn't boot again

So, I went back into the XP set up and deleted the Ubuntu partitions, booted with the DOS disk and ran fdisk /mbr again. This time fdisk let me see the partition info on the C drive and I was able to set the NTFS partition to active. 

On a reboot, the hard drive returned a disk read error (like the one I'd had previously when changing the drive to LBA or large). So, I tried changing to LBA and this time it worked! XP then started up fine. Tried installing Ubuntu again and this time allowed the installer to put Grub in the MBR. And grub now works and I can boot either system.

One last problem relates to screen resolution (I don't know if this needs to be taken to some other forum). Previously when I ran the Live CD (and now when I boot into Ubuntu from the HDD), the screen is virtually impossible to decipher. Under the Live CD, it created a whole lot of multi-coloured lines, but under the installed version it is slightly clearer (not much though) - the monitor looks as if it has been divided into four columns of similar blurry, content. 

I tried to reproduce this on XP and when I pushed the resolution really high I got a similar result. My monitor is old and I don't have any documentation for it. Is there a way I can reduce the resolution from a command prompt - I can't get to any of the GUI config options?

---

### Post by firstbishop on 2004-12-24
And now all sorted out. The resolution issue eventually came right with a whole lot of fiddling with XFS86Config-4.

Thanks to all for your help

---

