---
title: "Dual-booting Windows 8.1 and Ubuntu 14.04 EasyBCD Issue"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by matthew76 on 2015-03-04
[SIZE=1][FONT=arial]Hello,
I'm new to this forum and I joined because I'm having some issues dual-booting Ubuntu. I've dual-booted before but for some reason this time it will not work.[/FONT]
[FONT=arial]I created a partition for Ubuntu (on my natively installed Windows 8.1) and another for the swap area and created a Live USB with the newest Ubuntu ISO. I then plugged it in and installed it successfully on the partitions. After this, I naturally went back to my Windows 8.1 install to install EasyBCD in order to set up a boot menu. When I added new entry (Entry #9, Name: Ubuntu, Bootloader Path: \NST\AutoNeoGrub1.mbr) saved it, and rebooted, I was presented with both options. However, when I tried to select Ubuntu, it gave the error message that "[/FONT][COLOR=#333333]The application or operating system couldn't be loaded because a required file is missing or contains errors" listing the aforementioned file with the error.

    Scouring the internet, I found a common problem was the UEFI and Legacy settings. One person suggested I run boot-repair within Ubuntu from the USB, but when I do, it says that Legacy must be disabled. When I disable Legacy, I am unable to boot from my USB giving me the error message which basically says that it can't boot (I can provide the exact wording if necessary).

PS: I'm sorry if this question has already been asked or has been asked in the incorrect location but I couldn't find this exact problem.
Thanks for your time.[/COLOR][/SIZE]

---

### Post by oldfred on 2015-03-04
Please use standard fonts.

Post link from Summary report that Boot-Repair gives you.
What brand/model system?
 You may have to also change other UEFI settings to allow UEFI boot of a flash drive. 

I do not recommend EasyBCD with UEFI installs. It uses an old version of grub grub4dos to chain load. But it really just modifies Windows to boot other systems or it is another boot manager.
UEFI is also a boot manager and grub is a boot manager as well as a boot loader. Or you end up with too many boot managers and it is difficult to keep track. 

What brand/model computer?

You do have to have all systems installed in the same boot mode, or all UEFI or all BIOS. If not you can only use the UEFI as the boot manager, as total reboot is required to switch from UEFI to BIOS. And you may have to turn on/off UEFI or CSM/BIOS mode in UEFI to boot system installed in that mode.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by matthew76 on 2015-03-05
Sorry about the fonts, I couldn't change it for some reason.

link: [www.sourceforge.net/boot-repair-cd](www.sourceforge.net/boot-repair-cd)
brand/model: HP Envy h8-1520t CTO Desktop PC running Windows 8.1 64 bit

What do you suggest me to use other than EasyBCD?

Also, I can't access Ubuntu regardless of whether Secure Boot is enabled or not.
The main problem I'm having is I can't use my USB with Legacy enabled (at least I think it is).
How do I change EUFI settings to enable use of a flash drive?
How do I check whether Windows is installed to UEFI or BIOS?

Finally, I can't use boot-repair now because I can't access Ubuntu without the USB.

---

### Post by oldfred on 2015-03-05
HP only boots Windows, we have to copy grub into /EFI/Boot and rename shim to be bootx64.efi which then is the hard drive entry that still works. It will not let you boot an ubuntu entry. Complain to HP as that is not per UEFI standard.

Some other HP threads. some now older, so with newer Ubuntu there are fewer issues.
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

---

### Post by matthew76 on 2015-03-05
Ok well I have verified that Windows 8.1 was installed in BIOS mode (no EFI in Windows 8.1 partition lsiting) and I have uninstalled EasyBCD like you recommended. Now when I reboot I get a different looking boot menu but the same options with the same problem with choosing Ubuntu (missing file /nst/autogrub0.exe) I checked and someone said that EasyBCD doesn't work with UEFI but neither OS was installed in UEFI mode (I installed Ubuntu with Legacy enabled and Secure Boot disabled) so I'm really confused. I'm sorry I'm such a newbie to Linux but I'd really like to get this working.

Thanks

PS: Boot-repair still doesn't work because I can't boot to Ubuntu w/o the flash drive which requires Legacy to be enabled.

---

### Post by oldfred on 2015-03-05
You can run Ubuntu live installer in either BIOS or UEFI mode. And install Boot-Repair either way.

If system was purchased with Windows 8, then it is UEFI. Windows may hide things.

Did you review the threads were others discuss HP issues.

---

