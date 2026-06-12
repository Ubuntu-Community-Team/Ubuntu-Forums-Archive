---
title: "dual boot with win 8.1"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by mmcl26554 on 2014-05-21
I have followed the directions for doing the dual boot installation with win 8.1, as stated in everyday linux.   The installation is successful except the grub menu doesn't come up and the computer only boots to win 8.1.   I did run boot repair which should have fixed it but at the end it told me there were errors and suggested a boot partition.   It doesn't see difficult to setup a boot partition but how will this effect the dual boot with win 8.1.   If I do this will I then get the grub menu and be able to boot to ether win 8.1 or Ubuntu 14.04?   The boot repair log can be found at paste.ubuntu.com/7499133
Michael

---

### Post by ubfan1 on 2014-05-21
Try running chkdsk from Windows, and make sure the power option for fast bootup is turned off.  Can you get to the efi menu (to select devices or OSes to boot) with a function key, and what happens if you select ubuntu?  Hold off a bit on the new boot partition, usually not such a problem on the new machines.

---

### Post by oldfred on 2014-05-21
Almost sure you do not need boot partition.
Boot-Repair flags boot files beyond 100GB on drive. That was a problem years ago with BIOS and we saw some newer BIOS systems with same issue, most were USB hard drives. Have not seen a UEFI system where a /boot helped or was an issue.

> The NTFS partition is in an unsafe state. Please resume and shutdown

You have to turn off fast boot.
And often better with secure boot off.

What model HP. Most HP's have a buggy UEFI or HP only allows Windows to boot.

This says you have ubuntu as a boot choice.
> 
BootOrder: 0000,0001,3001,2001,2002,2003
Boot0001* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot0000* [COLOR=#ff0000]ubuntu.[/COLOR]

Can you in UEFI choose ubuntu entry? Or from a one time boot key choose ubuntu entry?

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

These are various alternatives as work arounds for those systems that only boot Windows. You can use the rename that Boot-Repair offers, but undo that if you update Windows as it will overwrite the renamed file. Often better to manually rename so you know what you changed. And backup efi partition.

 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

If Description has to be Windows then change description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by mmcl26554 on 2014-05-22
Fred (good to hear from you again!)
I can boot into Ubuntu by pressing the F9 key and selecting Ubuntu from the devices, then the Grub menu comes up and I can select Ubuntu (default) or Win 8.1.  That works fine and only an extra key 2-3 strokes so it's not bad.   But I would like to have work as it should.   However, I did discover the touch pad on my Envy (bad name for it) in Ubuntu 14.04 doesn't work well at all (cursor will jump all over the place) and the Synaptics driver program for it doesn't work with 14.04.   So I gave up on Ubuntu 14.04 in this computer and reloaded the backup.   I'm thinking about trying 12.04 which will work with the Synaptics program for Ubuntu and maybe it will install and work correctly with grub.   But I won't hold my breath.   Any suggestions would be appreciated.
Michael

---

### Post by oldfred on 2014-05-22
Do not know specifics of HPs.

I am surprised of a regressing on the Synaptics driver. Is there a way to install the old one in the new system? Or what is real difference.

---

### Post by mmcl26554 on 2014-05-22
Based on what I read of others experiences, the program is no longer supported and doesn't work on 14.04 conflicts with something else (I don't remember what).  But mu touch pad makes the cursor sometimes quite wild and it will jump from corner to corner and top to bottom.  The synaptics program may not even allow settings to control this behavior, but the only settings for touch pad in 14.04 is to turn off tap to click and 2 finger scrolling.  No setting for sensitivity.   So the only option is a mouse, which is ok but not as convenient a as the touch pad.    I did read an article I found using your previous suggestions, where a fellow was able to make rEFInd to work on an HP laptop (like what I have) but he didn't give enough specifics on just how to do it.   So I am not knowledgeable enough to make that work.   The thing that is funny is I had another laptop that HP sent me which was very much identical to the one I have now and I was able to install 13.10 on it and it worked fine.  I had to send that one back to them because the sound output was mono not stereo and they couldn't figure it out.  The sent me this Envy to replace it and what do you think it also didn't have stereo sound.   I did some research on the web and found a forum entry (Hp's forum) where a fellow figured out there was an error in a registry key.  All you had to do was change a 0 to a 1 and then you had stereo.   I actually got a call from an HP chat supervisor because they couldn't find the problem when I chatted with them.   I shared the fix with him and he got rather excited about it.   I wonder if they are going to fix it.

---

### Post by oldfred on 2014-05-22
I do not have UEFI. I started helping those with boot issues and hoped a couple of years ago to build a new system and realized it would be UEFI, so I started following those issues and not many were helping early on, so I helped a few. Still expect to build a new system with UEFI "Real Soon Now".  Old Jerry Pournelle quote.

Some links on rEFInd.

 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
More info on secure boot - Ubuntu's shim may need changing to work with Refind
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by mmcl26554 on 2014-05-23
I installed 13.10 and the grub menu showed up and I can boot just fine.  Isn't that strange?
Michael

---

### Post by oldfred on 2014-05-23
Whatever works is always a good choice.

Supposedly updates fix things, but there are regressions as they just are not able to test all alternatives that exist.

I also saw where with new systems and with 14.04, some have had to use the ppa to add the just released new kernel that may be in 14.10 and the extra support software and video drivers to get some systems to work.

---

