---
title: "Dual Booting in HP Laptop &quot;Selected boot device failed to boot&quot; Error"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by apu1995 on 2014-12-09
[COLOR=#000000][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I am planning on dual booting Ubuntu14.04 along side Windows 8.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I have created a Bootable USB , disabled secure boot and fast boot. But when I go to Advanced startup and select Load a USB device it shows the above error.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I tried using another USB but in vain.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I never got that error before as I had booted my Laptop dually before.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Please help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I used Universal USB installer.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]and my laptop is HP 14-b157tu.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks in Advance.

The problem with me was that the Ubuntu iso file was not bootable checked by md5sums [/FONT][/COLOR][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)[COLOR=#000000][FONT=Verdana]

And the boot repair problem: [/FONT][/COLOR][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) this link was helpful.
After running boot repair. I was not still able to bring the boot menu. So I ran cmd as administrator and typed in the following command : bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

This was for Ubuntu 14.04 64bit version.

---

### Post by oldfred on 2014-12-09
The flash drive has to be a bootable device. 
Did you confirm download is correct?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some versions of USB installer have issues:

 Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

If Windows 8 is pre-installed be sure to boot flash drive in UEFI mode.
      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Use Windows to shrink the NTFS partition and immediately reboot so it can run chkdsk and make  repairs for its new size. Make sure fast boot is still off as Windows likes to reset to its own defaults, particularly after any maintenance or updates.

While not same model, HP issues are pretty common across models.

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by apu1995 on 2014-12-09
Hi , 
Thank you so much for the reply.
I compared my iso file with md5sum calculator and the hashes turned out to be different.
I dont know why but i have used the same files to dual boot before. is there a possible reason for this ?

---

### Post by bfmetcalf on 2014-12-09
oops, wrong thread...

---

### Post by apu1995 on 2014-12-10
Hi thanks for the links. the iso file had a problem. I have succesfully installed Ubuntu alongside windows and it was not difficult as windows 8 was recognised. But I have another problem. I dont get a menu showing which OS i want to log into even after disbling the secure boot. And i tried using boot repair, its not nstalling after the commands. Its showing an error "run su from the terminal". I installed Ubuntu 14.10.

thanks in Advance. :D

---

### Post by oldfred on 2014-12-10
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Post the command & error that you get when you do the install & run the program as shown in link above.

---

