---
title: "file error on win 8.1"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by revolutionkiteman on 2016-03-25
hi huys,
hope you can help here, not sure what im doing wrong, i have checked a few guides and im pretty sure i have done everything(not enough obviously)
i have a laptop with pre installed win 8.1, i want to dual boot at first, then very likely just get rid of windows.
i downloaded wily, then burt image to disc, i have tried switching on/off secureboot with same results, i have swithed fast boot off.
the problem is, the laptop wil give me the blue screen asking what do i want to run, i click ubuntu, and i get the file ubuntu\winboot\wubidlr.mbr problem.
checked control panel\remove programs, ubuntu\wubi not listed.
i hate windows even more now lol.
allthough i love my mac, im not familliar with linux, windows that much so be gentle :)
thanks for any help,
p.s i have allready shrunk the windows volume so after testing in i hope a live dvd i can install next to the win partition

---

### Post by Bucky Ball on 2016-03-25
Welcome. Wubi is obsolete, no longer supported and is not a dual-boot. It is Ubuntu inside Windows. 

A dual-boot is Win on one partition, Ubuntu on another. One of the main reasons Wubi is no longer supported is that it doesn't work with UEFI installs and sounds like you might have one. 

My advice: boot into Windows, uninstall your Wubi install, then we can help you with a dual-boot.

---

### Post by revolutionkiteman on 2016-03-25
as i said, checked the uninstall menu and no wubi to be found? is there a way to do a deeper search?

---

### Post by Bucky Ball on 2016-03-25
*Thread moved to **Apple Hardware Users**.*

Probably better here. There is a slightly different black art involved with installing on a Mac. 

It looks like the wubidlr may be part of the bootloader? I know nothing of Wubi and very little of how the Win bootloader works nowadays so not clear on what is going on exactly. Hopefully someone can leap in who is.

---

### Post by revolutionkiteman on 2016-03-25
hehe, sorry mate, maybe misunderstood, i love my mac, but i am a bit useless on linux\ windows....on my laptop where im installing the live dvd :)

its not a mac problem

---

### Post by oldfred on 2016-03-25
Use Windows to shrink the Windows NTFS partition and reboot immediately to let it run chkdsk and update to its new size.
Make sure fast start up in Windows is off.
Usually best to have Secure boot off, but UEFI on and CSM/BIOS off. But some require CSM on even if booting in UEFI mode.
Also if UEFI has fast boot best to turn it off, at least while configuring. It can make it difficult to get back into UEFI to change settings.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by revolutionkiteman on 2016-03-25
with a real lot of messing about with re starts and bios changing i can get the kubuntu live dvd to run, after what seems like ages i get a screen with a box on saying the installer has CRASHED?
click ok and in the end i get a plasma login screen, with live user and in need of a password, tried all the kunbuntu/blank, CTRL ALT F1 no luck at all, in the end it reverts to a black screen, reloads the login screen and is in a loop, black screen login etc etc

done that oldfred in the start, arghhh windows!

could do with this put back in support as its not apple related :)

---

### Post by oldfred on 2016-03-25
Since Mac was off topic, side issue moved back to Installs.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by revolutionkiteman on 2016-03-25
ok, a breakthrough lol, it will now boot to the live cd
1. fast boot in power options to off
2. secure boot on in bios
3. enable legacy mode in bios
now, as said before, i shrunk my original volume to have space for this and asigned it a letter, but im unsure how to proceed?
when i boot up kubuntu, and click on the install icon on desktop, i dont understand where it wants to be installed, as there are none of my original drive letters, this would seem the easiest option if it had it.
am i better to delete\unshrink the origanal partition and let it do it itself, or what do letters it use mean, something like sda1,2,3,4, etc?
i never get the option that would reassure me to install next to original os

---

### Post by oldfred on 2016-03-25
If Windows is UEFI, you really want Ubuntu to be UEFI also.
And how you boot install media is then how it installs, or you need to boot installer in UEFI boot mode.

You may be able to install in BIOS mode, and then convert to UEFI with Boot-Repair. It uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI).

But you need to see partitions, or else it may totally erase Windows and restore partitions, so you need separate backups.

Do you have good backup of Windows?
With my one Windows system, I did Dell backup, Windows backup and full backup with Macrium. Multiple flash drives & DVDS required.

---

