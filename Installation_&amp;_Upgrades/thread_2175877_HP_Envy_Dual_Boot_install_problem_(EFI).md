---
title: "HP Envy Dual Boot install problem (EFI)"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by mpirringer on 2013-09-21
Hi,

I Got a new hp labtop Intel I7 4200 processor 16 gb of ram and 2 1TB hd. The first 1 TB hd has win8 on it the 2nd HD has no partition atm.

I had previously installed ubuntu on various machines - no problem. Even got a UBUNTU install on a 320GB USB drive (I am a consultant and it comes in handy when one of my customers ex employees changed the PW before leaving etc) 

Here are my issues.

1) The system does not recognize the USB as a bootable device because it is not EFI - So worst case how do I make it EFI

2.) Tried to install from a 13.04 Desktop dvd. Also tried a Fedora, Kubuntu and even a backtrack DVD. same result on all

The DVD is not recognized as a bootable device (Boots fine on many other computers) I can make it recognize and boot it by turning on "legacy boot". Then I get to the menu but as soon as I make any selecting (Install ubuntu, try ubuntu etc) the Screen goes black (turns off) and absolutely nothing happens

Help would be apprechiated. 

Martin

---

### Post by oldfred on 2013-09-21
A few computers need to have Ubuntu installed in legacy mode and then converted to UEFI. But you need to install with gpt partitioning on the second drive. Most now use USB flash drives and the 64bit version will offer to boot in UEFI mode, UEFI mode with secure boot on (if it is on) or in legacy/BIOS/CSM mode.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some other HP

 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Some other dual drive:
      
 Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

---

### Post by Jonathan Precise on 2013-09-21
Looks like a bad download. Have you tried re-downloading, or is it the same disk you used to install on other computers?

Also, make sure it is the 64-bit version of ubuntu. If your computer is only 32-bit, please mark yourself as affected in [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1025555") and [this other bug]("https://bugs.launchpad.net/boot-repair/+bug/1228717").

---

### Post by mpirringer on 2013-09-22
Thanks - using the 64 bit helped some - now at least it boots from the DVD by itself w/o problems Setting it to legacy mode also allowed it to recognice my ubuntu on a USB drive that I have been using for a year (currently upgraded to v 13)

HOWEVER

All 64 bit installs and my USB drive have the following problems. After either selecting "install ubuntu" or "try ubuntu" or anything ubuntu the screen goes black the DVD/USB churns away for a while and then everything stays black. Maybe something to do with an incompatablility of the intel HD 4600 graphics card? that the laptop is using?

Need to see what is on the screen to type something in or click someting

TIA

Martin

---

### Post by oldfred on 2013-09-22
Most times with black screen we suggest nomodeset. 
If BIOS boot with purple screen you hit the infamous 'any key' and then f6, and choose nomodeset. 
If UEFI boot or first boot after install you have grub menu, use e to edit, scroll to Linux line and replace quiet splash with nomodeset.

 Shows both f6 & grub edit screens.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Some newer Intel systems need this instead of nomodeset.
       i915.i915_enable_rc6=1
    
And some others need this:
       acpi_osi=Linux  acpi_backlight=vendor
     Or this:
 Force Intel Video mode as boot parameter in grub menu - change to your screen size not 1280x1024.
video=1280x1024-24@60

---

### Post by mpirringer on 2013-09-22
Thanks all - got it going so here are the install instructions for a HP Envy with an I7-4600 processor. 

I got 2 HD (1TB each) and used the first for Win8 and the 2nd for Ubunto 13.04 After going through my notes I can summize the following

1.) when starting the computer hit <ESC> then <F10> to get into the bios - go to advanced - then boot - Enable Legacy support (Even though you will install EFI nothing will work without legacy boot enabled). If you also want to boot from older USB 2.0 devices alse set USB 3.0 from <enabled> to <auto> restart the computer

2.) Insert the 64 bit version DVD of 13.04 when starting hit <ESC> then <F9> to get into the boot screen 

3.) as soon as the grub menu appears select "install ubuntu" and then  hit "e" and add "nomodeset" to the linux line after the word "quiet" (do not use the quotes)

4.) Now hit F10 to start the installation

5.) When prompted select the "Otherwise" option on the bottom of the list

6.) In the partition menu select the 2nd HD (in my case sdb) and create a new partition table

7.) Create an EFI partition of about 100 MB as the first partition

8.) Create your Linux partitions with whatever mount points you want - don't forget the swap partition if you are using one

9.) install linux

10.) From now on when you want to boot into Linux you will have to hit <ESC> and <F9> during startup to get to the boot selector and you can now select your Ubuntu disk (the one you installed Ubuntu on). IMPORTANT! You will need to leave your bios in "legacy boot" mode or your system will always boot the WIN8 selection even if you select your ubuntu HD (beats me why but I can live with that as I got many other "old" boot sticks I need to work on)

11.) When you get into linux the first time after the install you will have to add the "nomodeset" to the Linux line in the grub edit. To make it permanent go in the terminal and tyep
sudo gedit /etc/default/grub

then add nomodeset after quiet in the grub file then in the terminal type

sudo update-grub


NOTE: Win8 Will assign a drive letter to your Linux partition(s). Should you click that drive letter or access it somehow it will tell you that you need to format that partition - DO NOT FORMAT THE LINUX PARTITION(s) from windows as you will wipe out your linux install

HTH

---

