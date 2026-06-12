---
title: "GRUB Help!"
date: 2004-12-02
forum: Installation &amp; Upgrades
---

### Post by madept on 2004-12-02
I have just installed Ubuntu, and didn't know about the GRUB problems.
Now I get the error 17 and cannot boot Windows or Linux.
I have an XP reinstall disk, but no recovery disk, so I can't do fixmbr/fixboot.
I tried some of the suggestions I found here but can't get anything to work.
I have a Knoppix cd I can boot if that helps any.

Please help me to get Windows booting again, then I'll worry about getting Ubuntu working.

Thanks!

---

### Post by madept on 2004-12-03
I've been trying some other suggestions out.

The installer's Lilo option isn't working.  At first, I keep getting framebuffer problems.
When I disable framebuffering, I get a segmentation fault once the Lilo progress is 100%.

I have looked for other suggestions, but they all require you to mount the hard drive.
The Ubuntu installer will not mount the drive because it is not in /etc/fstab.  I can't put it in /etc/fstab though, because I'm not really sure what options I need to use.

I've tried mounting the hard drive in Knoppix, but that also fails.
Qtparted can see the drive, but gives and error and exits when I select it.
I'm trying to use the Wiki's install from knoppix howto right now.  I'm hoping that if I can get to installing the bootloader, I can just replace GRUB with Lilo.
But I can't partition the disk with qtparted, so I can't get very far with that.  Currently the only working partitioning tool is the Ubuntu installer, but immediately after partitioning, Ubuntu is installed.

I will keep messing around with Knoppix and the installer and try to get Grub configured or LILO installed over Grub, and post an update on what I figure out.
I'm also thinking using a Gentoo install cd might help - it has a lot of tools, and with emerge you can add pretty much anything.
I'm hoping while I'm doing that someone will see this information and suggest something that might work.

---

### Post by wallijonn on 2004-12-03
did you go into the BIOS and change the disk tpe from Auto to Large or LBA?

---

### Post by madept on 2004-12-03
[QUOTE=wallijonn]did you go into the BIOS and change the disk tpe from Auto to Large or LBA?[/QUOTE]
No, I couldn't find that option in the Dell BIOS or the Promise options, but I didn't spend too long looking around the Promise options.  Am I not looking in the right place?

---

### Post by wallijonn on 2004-12-03
Exactly which Dell do you have? I believe f1 or f2 will get you into the Dell BIOS. There should be a submenu to set the disk geometry.

---

### Post by adbak on 2004-12-03
I have a Dell Dimension 4800.

Yes, F2 will take you to the BIOS set-up, and F12 will take you to a screen that I mentioned above.

---

### Post by madept on 2004-12-03
[QUOTE=adbak]I have a Dell Dimension 4800.

Yes, F2 will take you to the BIOS set-up, and F12 will take you to a screen that I mentioned above.[/QUOTE]
 I have a Dimension 8300.

I press F2 and get the BIOS.
From there, my options are:
> Drive Configuration
Hard-Disk Drive Sequence
Boot Sequence

Memory Information
CPU Information

Integrated Devices (LegacySelect Options)
Power Management
System Security

Keyboard NumLock
Report Keyboard Errors

Auto Power On
Fast Boot
OS Install Mode
IDE Hard Drive Acoustics Mode

System Event Log

Asset Tag

I can quote the information on any of those categories if you need it.  I just can't find anything about disk geometry.

---

### Post by adbak on 2004-12-03
From Boot Sequence, hit enter, I believe, highlight your CDROM entry, and repeatedly hit the plus sign on your numpad until it becomes the top one.  After that, pop the CD in, save your settings, and it should load up.

---

### Post by madept on 2004-12-03
[QUOTE=adbak]From Boot Sequence, hit enter, I believe, highlight your CDROM entry, and repeatedly hit the plus sign on your numpad until it becomes the top one.  After that, pop the CD in, save your settings, and it should load up.[/QUOTE]
I'm kind of confused about this, because I can get a CD to boot fine by pressing F12 when the BIOS comes up - that displays the boot menu.
And what CD are you talking about?

---

### Post by froogle on 2004-12-04
Your windows installation CD is actually a recovery one as well. I can't remember the option off the top of my head but you will find that if you boot of it that it will give you a couple of options including one to repair/recover and existing WIndows installation. Selecting that should drop you into a dos like command prompt where you can do a fixmbr and get WIndows back that way.

---

### Post by usasma on 2004-12-04
I've found, in my case at least, that Grub will assign the wrong hard drive (at least on my system) for the kernel.

What I did was I found an article about Grub that had me download a boot image for a floppy (grub.img) and a program to write it to floppy (rawrite.exe).  Once I booted from the floppy I was able to edit the first line of the entry for booting Ubuntu.  I changed the  (hd1,1) to (hd0,1) and Ubuntu boots sortof normally (I say sort of because I've had to boot through the editor as I can't figger out how to save the changes to menu.lst  ](*,)

---

### Post by madept on 2004-12-04
[QUOTE=froogle]Your windows installation CD is actually a recovery one as well. I can't remember the option off the top of my head but you will find that if you boot of it that it will give you a couple of options including one to repair/recover and existing WIndows installation. Selecting that should drop you into a dos like command prompt where you can do a fixmbr and get WIndows back that way.[/QUOTE]
This is very close to a solution I think, but there's still a problem (this time it's Microsoft's fault though).
When I boot the XP reinstallation cd, it loads a menu that tells me I can press enter to install XP, press R to get the recovery console, or press F3 to exit setup.
But when I try to select my choice, it doesn't do anything.  I can't get past that screen if I press enter, r, or F3.  I searched the Knowledge Base and found nothing that helps.  Any suggestions?

[QUOTE=usasma]I've found, in my case at least, that Grub will assign the wrong hard drive (at least on my system) for the kernel.

What I did was I found an article about Grub that had me download a boot image for a floppy (grub.img) and a program to write it to floppy (rawrite.exe).  Once I booted from the floppy I was able to edit the first line of the entry for booting Ubuntu.  I changed the  (hd1,1) to (hd0,1) and Ubuntu boots sortof normally (I say sort of because I've had to boot through the editor as I can't figger out how to save the changes to menu.lst  ](*,)[/QUOTE]
That may be my problem.  I have Grub on a floppy, but I can't get it to find the copy of Grub that Ubuntu installed.

---

### Post by usasma on 2004-12-04
I'm presuming that you get the Error 17 after you execute the grub menu.  If that's so, then just press "e" instead of "Enter".  It'll let you edit the offending line.  Then press "b" to boot the correction (I still can't figger out how to get it to save!)

Once you've booted into Ubuntu you can open the menu.lst file by hitting Alt and F2 together, then typing in "gksudo gedit /boot/grub/menu.lst"  It'll ask you for a password and then should open.

Since it's marked read only, I didn't mess with it - rather I copied it to a new file, edited my corrections in, and then saved it over the original menu.lst.  FWIW - It took 2 boots for it to work correctly for me.

---

### Post by madept on 2004-12-04
[QUOTE=usasma]I'm presuming that you get the Error 17 after you execute the grub menu.  If that's so, then just press "e" instead of "Enter".  It'll let you edit the offending line.  Then press "b" to boot the correction (I still can't figger out how to get it to save!)

Once you've booted into Ubuntu you can open the menu.lst file by hitting Alt and F2 together, then typing in "gksudo gedit /boot/grub/menu.lst"  It'll ask you for a password and then should open.

Since it's marked read only, I didn't mess with it - rather I copied it to a new file, edited my corrections in, and then saved it over the original menu.lst.  FWIW - It took 2 boots for it to work correctly for me.[/QUOTE]
 I get the Error 17 before I even see a grub menu.
Right after I see the BIOS and Promise BIOS, I see a Grub stage 1.5 message, then error 17.

---

### Post by madept on 2004-12-05
Okay...I got the XP install cd to boot and I've tried:
map - doesn't list a hard drive
fixmbr - does nothing
fixmbr \Device\HardDisk0 - gives error
fixboot - gives error
bootcfg /scan - finds no XP installs
chkdsk - finds "unrecoverable" error.
So I don't really think that will help much.

The Gentoo 2004.3 installation livecd boots and can mount /dev/sda3 (the Ubuntu partition).
I can access /boot/grub/menu.lst now, but I'm not sure what's going wrong that's causing the error.

Here's the result of 'fdisk', then 'p':
> Disk /dev/sda: 120.0 GB, (some long number) bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280

Device		Boot	Start	End	Blocks		Id	System
/dev/sda1		1	5	40131		de	Dell Utility
/dev/sda2		6	12626	101378182+	7	HPFS/NTFS
/dev/sda3	*	12627	14531	15301912+	83	Linux
/dev/sda4		14532	14593	498015		f	W95 Ext'd (LBA)
/dev/sda5		14532	14593	497983+		82	Linux swap


And this is my menu.lst:
> title        Ubuntu, kernel 2.6.8.1-3-386
root         (hd0,2)
kernel       /boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda3 ro quiet splash
initrd       /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title        Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root         (hd0,2)
kernel       /boot/vmlinuz-2.6.8.1-3-386 root/dev/sda3 ro single
initrd       /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title        Memory test
root         (hd0,2)
kernel       /boot/memtest86+.bin

title         Windows NT/2000/XP
root	      (hd0,1)
savedefault
makeactive
chainloader +1

title         Windows NT/2000/XP
root	      (hd1,1)
savedefault
makeactive
chainloader +1

Any ideas on what that menu.lst file needs to contain, or any other way to fix my problem?

If this doesn't work, I'm going to attempt to mount /dev/sda3, chroot into it, and use apt-get to install Lilo.

---

### Post by madept on 2004-12-05
One more note on this:  Could a part of the problem be that Ubuntu is only being installed to sda.
I have a Promise SATA controller, and in the Ubuntu installer, I see that the Dell utility and Windows partitions appear on both sda and sdb.
But Ubuntu is only being installed to sda...

---

### Post by madept on 2004-12-06
Okay, I've fixed the problem.
For anyone else with the same problem:

I booted the Ubuntu installer and deleted my Ubuntu partitions.
Then I put mbrtool ([http://www.diydatarecovery.nl/](http://www.diydatarecovery.nl/)) on a floppy and booted it.
I used mbrtool to set my XP partition to active and overwrite Grub.
I no longer have Ubuntu, but it was a new install - the important thing to me is that Windows boots fine and no data was lost my Windows partition.

---

### Post by ante0 on 2005-03-02
Acually, there is a option in the Ubuntu install to install Grub or Lilo to a harddrive. Just press "Go Back" button. That will take you to the main menu of Ubuntu installer where you can choose to install a bootloader. It needs to load the "detecting hardware" steps first though. And one more thing, would'nt "fdisk /mbr" erase the information in the Masterbootrecord and make the Windows partion bootble?

//ante

---

### Post by madept on 2005-03-02
[QUOTE=ante0]Acually, there is a option in the Ubuntu install to install Grub or Lilo to a harddrive. Just press "Go Back" button. That will take you to the main menu of Ubuntu installer where you can choose to install a bootloader. It needs to load the "detecting hardware" steps first though. And one more thing, would'nt "fdisk /mbr" erase the information in the Masterbootrecord and make the Windows partion bootble?

//ante[/QUOTE]
The Ubuntu installer was no help at all.  It wouldn't install Grub to a floppy or Lilo because of bugs.
The Windows XP install cd's recovery console was also no help.  It kept telling me I had a corrupt partition and it couldn't do anything.
mbrtool is the only thing that actually did anything useful.

---

### Post by ante0 on 2005-05-17
oh yeah, i found out about the installing GRUB in the ubuntu cd now... its just a step it does, but is installed after the files from the cd is copied.
oh well, hope you found out some other way =)

---

