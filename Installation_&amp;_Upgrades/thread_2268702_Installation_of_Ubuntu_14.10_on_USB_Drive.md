---
title: "Installation of Ubuntu 14.10 on USB Drive"
date: 2015-03-10
forum: Installation &amp; Upgrades
---

### Post by tpelle2 on 2015-03-10
Newbie here, getting cold feet in the middle of an Ubuntu installation to a USB drive.

I am installing a "boot from USB" installation of Ubuntu on a blank 64gb USB drive.  At one point I get to a question where it asks "Install Alongside Windows Boot Manager" or "Erase Disk and Install Ubuntu".  I don't know which way to answer.

Obviously I don't want to blow away Windows 8.1 (yet), as I just want to give Ubuntu a try for a while.

What do I do here?

The computer is a Toshiba Satellite C55 with Windows 8.1.

---

### Post by yancek on 2015-03-10
If you just want to try it you could just test it using the usb.
You would have more control using the "Something Else" option rather than the Install Alongside.  That way you will see the different drives/partitions and can select where to install. 
The link below has a pretty detailed tutorial on installing Ubuntu in dual-boot.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by grahammechanical on 2015-03-10
Do not click Install Ubuntu. Only click Try Ubuntu. Then you will not have this problem until you are ready to actually install. Many have decided to "blow away Windows," as you put it, only to want it back later on. Too late then. As you have Windows 8, you should read this before installing alongside Windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by tpelle2 on 2015-03-10
Thanks for the replies, but can we keep it a little more simple?  What my goal here is to get an installation of Ubuntu that boots from USB, so that, if I want to run Ubuntu I simply insert the USB drive, reboot, and the computer simply boots up in Linux.  To revert to Windows I would simply shut down, remove the USB drive, and start back up.  I thought that this was what the whole "USB bootable" thing was about!

The odd thing is that, even without going all the way through the installation process, the computer actually does boot up in Ubuntu!  While in Ubuntu I poked around and found, in \Dev, a Windows Boot Manager.  I wonder if that's the "Windows Boot Manager" that it wants to install alongside of?

At the same time, while running Ubuntu, I looked around and was unable to see any of the Windows 8 directory structure.  It looks like the only thing it sees is the Ubuntu files on the USB drive - which, as far as that goes, is fine with me!

So another point of confusion is, if it already boots to Ubuntu, what the heck does the rest of the installation process do?

---

### Post by Mark Phelps on 2015-03-11
The safest way to do this is to have the hard drives DISCONNECTED while doing the install.  This way, there is no risk of accidentally overwriting the hard drives.

When you later reboot, when you have the USB stick inserted, it should boot automatically from it -- if you have that first in your boot order.

---

### Post by C.S.Cameron on 2015-03-11
I agree, It is safest and easiest to first disable your internal HDD, boot your Live DVD or USB, insert your target drive and install to it.
I usually make the first partition on the drive FAT32 or NTFS so that the drive can communicate with a Windows PC.
For this use the "Something Else" option.

---

### Post by sudodus on 2015-03-11
+1 I agree too, It is safest and easiest to first disable your internal HDD, boot your  Live DVD or USB, insert your target drive and install to it.

In order to see different ways to install Ubuntu into a USB drive (or any drive), have a look at the following link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it
[/URL]

---

### Post by tpelle2 on 2015-03-14
Update:

Well, I got it working!  I used a bootable installation CD-ROM to boot from, then inserted the USB stick and did the install on to the USB stick.  (The hard drive with Windows 8.1 was removed from the PC to prevent any terminal OOPSIES from happening.)

I confess that it did take me two tries, because on the first try I neglected to allow the installer to re-format the target drive during the install, so the installer crashed.  Second try worked great.

So far it's working pretty good.  I have a few issues to work out (The sound card is putting out very low volume.  I have to get our network printers set up.  And I really don't like the Unity GUI - "What?  No Command Line?), but I'll start tackling that stuff today.

It seems to be running pretty fast, as the USB port and memory stick are both USB 3.0, which I think has a faster data transfer rate than my Windows hard drive.

So now the fun begins!

---

### Post by sudodus on 2015-03-14
Congratulations :KS

When you feel that the problem in the first post of this thread is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

It is usually better to start a new thread with a good descriptive title, when you need help with some other problem.

-o-

You can to try other flavours / desktop environments than Unity (but after a few days you might find Unity really nice). [Try live (without installing)]("http://ubuntuforums.org/showthread.php?t=2230389").

Take your time and tweak the audio settings with ***pavucontrol*** to increase the sound volume.

Ubuntu is linux ,so of course there are command line options :-) The standard one is to start a terminal window (in Unity) with the hotkey combination

[I][B]ctrl + alt + t
[/B][/I]
and if you want crude text screens, use the hotkey combination

[I][B][I][B]ctrl + alt + F1
[I][B]ctrl + alt + F2
...
[I][B]ctrl + alt + F6
[/B][/I][/B][/I][/B][/I][/B][/I]**[B][B]**[/B][/B]
and return to the graphical desktop environment with**[B][B]**[/B][/B][I][B][I][B][I][B][I][B]

***ctrl + alt + F7***
[/B][/I][/B][/I][/B][/I]
[/B][/I]

---

### Post by tpelle2 on 2015-03-19
Well, the rumor of my success has been greatly exaggerated!

Here's a summary so far and a status Update:


After a long time away from it I am fooling around with Linux again.  I'm trying to get the operating system on a bootable USB stick to run on a machine, a Toshiba Satellite C55, with Windows 8.  I have always disliked Windows 8, but this experience has converted my mild dislike to active hatred!


Here is where I am with this effort:


I have downloaded an iso of xUbuntu, and installed it on a 65GB USB stick.  No problems at all so far.  I've gone into the BIOS of the C55 and set the boot order to go USB, DVR, HDD.


If I remove the Windows HDD from the machine, insert the USB stick, and power up, it will boot to Linux just fine.


If I power down, reinstall the Windows 8 HDD, then power up with the Linux USB stick removed, it boots Windows 8 just fine.


If I then power down, and with the Windows HDD installed, insert the Linux USB stick, it goes to Windows 8 first (even though USB is first in the boot order) and searches out and destroys the Linux USB stick!


I have gone into the BIOS and disabled 'Secure Boot', thinking that would solve the problem of Windows 8 killing my Linux USB stick.  No dice.  I have read that I can go to the BIOS and switch from UEFI to CSM (legacy BIOS boot method) and it will work for Linux, but I will have to switch back to UEFI before I try to boot Windows 8 again.  At this point my USB stick is dead, and I will have to do a reinstall (again).  I know that, if I want to get into the BIOS, it has to be from a "cold boot" to do so with the ALT-F2, otherwise I will have to use the Windows-W key combination to get to a Settings screen.  I want to make sure I can get to the BIOS during the Linux boot if I have set the BIOS to CSM.


Does anyone have any further suggestions regarding what to do (or more importantly, what NOT to do)?

---

### Post by ubfan1 on 2015-03-19
I'd suggest not going to CSM.  Check the grub.cfg files for disk numbers -- they may have gotten mixed up with all the disk switching.  My USB3 boot device has a EFI partition containing the /EFI/ubuntu/grub.cfg (and grubx64.efi and shimx64.efi), AND the default bootloader for the USB in /EFI/Boot/bootx64.efi (which is a renamed copy of shimx64.efi) and also a copy of grubx64.efi.  The /EFI/ubuntu/grub.cfg files is a short stub, copying in the maintained grub.cfg from /boot/grub/grub.cfg, and uses the UUID, (mine also has a (hd0,gpt8) reference, which is wrong (probably having been created when on another machine).  The rest of the grub.cfg file uses hd1 for all Ubuntu references, and hd0 for the Windows boot, which is consistent with the sdb for the USB and sda for the hard disk (which does not have Ubuntu on it).

---

