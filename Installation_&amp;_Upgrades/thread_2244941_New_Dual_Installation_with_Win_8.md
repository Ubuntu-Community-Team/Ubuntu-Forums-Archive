---
title: "New Dual Installation with Win 8"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by cressrt2 on 2014-09-19
I am trying to install 14.04 as a dual boot on a new HP PC with Win 8 preinstalled, but the USB installation does not detect the other OS, I have disabled Fast start but cannot see any other reason or what else to do. I have searched the Forum but did not find anything, any ideas?

---

### Post by oldfred on 2014-09-19
Just about everyone has that issue. And HPs have a few more issues but many have installed.

What model HP computer?

Use Windows to shrink the NTFS partition to make room for Ubuntu. Reboot immediately so it can run chkdsk and make repairs for its new size.
Make full backups of Windows & the efi partition. Some force install or now just a reinstall will overwrite Windows.
Currently you have to use something else or manual install. 

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

See also below in my signature for many more links and info.

---

### Post by cressrt2 on 2014-09-20
Thnaks for the links I will start looking through these now.
The model details are  HP 15-D006SS/15/1/-32.

---

### Post by oldfred on 2014-09-20
Have not seen that specific model.

But some other HP that may be similar and the issues they had:
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

      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by cressrt2 on 2014-09-22
Have not yet installed, if I cannot manage will probably just wipe Win8 and stay with Ubuntu.
Another related question is this only a problem with HP PC's or is it the same for all with Win 8 preinstalled. and/or what make would you recommend to use as dual boot?

---

### Post by fantab on 2014-09-22
> **cressrt2 said:**
> Have not yet installed, if I cannot manage will probably just wipe Win8 and stay with Ubuntu.
Another related question is this only a problem with HP PC's or is it the same for all with Win 8 preinstalled. and/or what make would you recommend to use as dual boot?

So far on these forums, it is only with certain HP machines.
There are workarounds as oldfred pointed out, Wiping Win8 may not help IMO because its not the OS but the firmware that prevents 'other' os from booting.

---

### Post by oldfred on 2014-09-22
I think HP sells a few systems with Ubuntu pre-installed, so it must know what it has done in hard coding UEFI to only boot Windows.

Sony and a few others also have the same issue of hard coded UEFI which then leads me to believe it is from Microsoft. They may give a extra discount if you only boot Windows. 

I think so far Dells have worked, but when it was being sold I saw that Microsoft was going to own 10%. Since they went thru a few changes on the deal, I never did see final results. 

A few of the Windows only systems with only Ubuntu, we have had to create a new /Windows/Boot/bootmfgw.efi file that really is grub.  UEFI thinks it boots Windows but just boots grub. A bit more maintenance as if grub updates you have to manually copy to the "Windows" file.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by cressrt2 on 2014-09-23
OK I have installed OK and run the Boot Repair but this did not work,  got the message http://paste.ubuntu.com/7584715/". Is there another link to suggest how to fix the Grub or any other suggestions.
Many thanks so far!

Sorry wrong link should be [http://paste.ubuntu.com/841252](http://paste.ubuntu.com/841252)

---

### Post by oldfred on 2014-09-23
That link does not work. Missing digit? Most are now 7 chars.

---

### Post by cressrt2 on 2014-09-23
I must have copied wrong, I am will re-run and post the correct link, thanks.

Try this:
An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/8413112/](http://paste.ubuntu.com/8413112/)

---

### Post by oldfred on 2014-09-23
Install looks normal. Boot-Repair picks up the slightest error and reports that.
Your grub says it installed correctly as error code 0 is no error.

 Reinstall the GRUB of sda5 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

But HP's only boot Windows. See post #4 on what others with HP had that worked.

Most seem to find this works. You may still have to use the one time boot key.


 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

---

### Post by cressrt2 on 2014-09-24
I tried a couple of suggestions last night but none seemed to work, however I switched on this morning and I was presented with a "normal" grub screen so something did worl.
Many thanks for all help.

---

