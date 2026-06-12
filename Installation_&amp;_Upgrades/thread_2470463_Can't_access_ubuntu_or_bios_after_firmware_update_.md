---
title: "Can't access ubuntu or bios after firmware update (F12 Z390 AORUS PRO WIFI)"
date: 2021-12-30
forum: Installation &amp; Upgrades
---

### Post by bingodingo on 2021-12-30
Updated to bios version F12 (Z390 AORUS PRO WIFI (rev. 1.0)) and now I can't access either the bios or my Ubuntu (20.04, installed on separate hdd to windows 10; previously, accessed Ubuntu by changing boot priority in bios).
I don't want to clear the CMOS - I still currently have the xmp correctly set on my RAM, I'll loose it if I reset and can't get back in. (I seem to have lost my resizable bar setting and don't think I'll be able to get it back until I can get into bios again).
Looking at the efi partitions, I see what I assume to be the old partition on the linux disk and a separate partition on the windows disk. (I'm wondering if the new bios bootloader got clobbered in the update and the old one is being blocked by the TPM - can't boot at all when I disconnect the windows drive and try to boot of the Ubuntu drive).
I think the firmware TPM on the motherboard is now set to on. (I think I had turned that off in the bios, but Windows update now says 'Great news—your PC meets the minimum system requirements for Windows 11'.)
I could try disconnecting the Windows drive and doing a fresh installation of Ubuntu on the other drive (existing installation is backed up). If that worked then perhaps grub might give me access to the bios.
Thoughts?

---

### Post by Frogs Hair on 2021-12-30
> (I seem to have lost my resizable bar setting and don't think I'll be able to get it back until I can get into bios again). Can you elaborate on this ? Were you using efi or legacy mode for the dual boot ? If you are currently in windows on that system you can check your TPM status . Open the run dialog with   Windows+R and type tpm.msc  .

To check out efi or legacy related info type msinfo into windows search.

---

### Post by bingodingo on 2021-12-30
Thanks Frogs Hair.
I was in EFI mode  for the dual(ssd/hdd) boot.
Currently: Bios mode UEFI
TPM Management ...Status: The TPM is ready for use. Available options: You may clear the TPM to remove ownership and reset the TPM to factory defaults.
Resizable bar: can't find a web-link just now to say precisely what I should see in Device Manager for my GPU but I'm pretty sure what I'm seeing now isn't it, was getting this previously. :(
Little bit worried that if something happens I'll end up with a bricked motherboard (e.g. Windows decides, without asking me, that it's time for Windows 11, and something goes wrong).

---

### Post by bingodingo on 2021-12-30
Some additional background:
First boot after the bios update was wierd. Multiple restarts. (I was wary about removing the USB with the bios in, not sure if that is relevant.)
At some point I entered the bios. 
Then I booted in my Ubuntu installation. 
I had updated the firmware bios with both drives connected (possible not the best idea).
After booting into Ubuntu, and removing the usb, I shut down and disconnected the Ubuntu drive.
Since then, after restarting, I'm only able to boot into windows (I can see the Ubuntu drive from within windows). :(

---

### Post by Frogs Hair on 2021-12-30
If you can boot from the Ubuntu USB , run boot repair and upload to pastebin if possible and link it here. I have Win 11 ssd/hdd 20.04 dual boot, but can't answer why the bios is off limits. If it were just a windows boot-loader or grub overwrite you would still be able to enter the bios. I wouldn't worry about a brick as long as you have a working operating system. Double check the sata cable too if you removed it.

---

### Post by bingodingo on 2021-12-30
Disconnected the windows drive, on rebooting presented with the GRUB menu, chose the existing Ubuntu installation.
Now I can get into Ubunut :), but after update / reboot, no longer presented with the GRUB menu and thus still can't access the bios.
Error message on booting below.
Can I run boot repair from within the existing Ubuntu installation, or do I need to boot into 'Ubuntu live' to run boot repair?
Error message on booting:
Coud not create MokListRT: Invalid Parameter
Coud not create MokListXRT: Invalid Parameter
Importing MOK states has failed: import_mok_state() failed: Invalid Parameter
Continuing boot since secure mode is disablederror: no suitable video mode found.
error: can't find command 'hwmatch'.

---

### Post by tea for one on 2021-12-31
> **bingodingo said:**
> Disconnected the windows drive, on rebooting presented with the GRUB menu, chose the existing Ubuntu installation.
Now I can get into Ubunut :), but after update / reboot, no longer presented with the GRUB menu and thus still can't access the bios.

As you can boot into a UEFI installation of Ubuntu,  you can try to reach the UEFI set up via a terminal command:-
```
sudo systemctl reboot --firmware-setup
```

---

### Post by oldfred on 2021-12-31
My older systems reset defaults in UEFI after an UEFI update.
I have multiple settings that I have to redo. I have to keep a list for my Asus system. My newer Gigabyte only has a couple of settings.

Did your update turn UEFI Secure boot on and you had it off?

Also review UEFI fast boot (different than Windows fast start up). Fast boot does speed booting, but then you may not have time to press any key to get into UEFI to make changes. It assumes no system changes, does not then scan system & write hardware configuration onto drive for operating system to use. Often a full cold boot or power down & drain all power will force a full normal boot.

Many also have USB full support or USB allow boot settings.

---

### Post by bingodingo on 2022-01-01
Thanks Tea, I'll give that a try.

---

### Post by bingodingo on 2022-01-01
Hi oldfred,
I can't remember what setting I had for secure boot - I vaguely remember turning it off so I could boot into Ubuntu, I'm not sure though. 
Looking at the error message, I wonder if the firmware update did turn it on ('Continuing boot since secure mode is disablederror: no suitable video mode found').
I may have to ultimately try resetting CMOS but I'd like to look at other options first - if I'm not able to get back into the bios after resetting CMOS I will loose the XMP memory settings which seem to have survived.
The update introduced something called 'capsule BIOS support', not sure if that is playing a role in any of this. I suspect that the bootloader? for accessing the bios setting screen has been clobered. (On start up on windows, I get a prompt to hit 'del', but when I hit that it looks like the system attempts to load a program and then falls through to a windows bootloader. Grub is similar - I can access this if I disconnect everything else but a live usb - when I chose edit uefi firmware it fails, goes back to the grub screen).
Thanks

---

### Post by oldfred on 2022-01-01
My older z97 UEFI screens shots, Asus still uses similar screens for UEFI, just updates for newer features.
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

You should always be able to get into UEFI after a full cold boot, total shutdown & drain power by unplugging & holding power switch & then f2 on boot. And then turn off fast startup for as long as making any changes.

---

### Post by bingodingo on 2022-01-01
Quick update: unable to reach the UEFI set up via a terminal command - goes to a black screen with a flashing cursor top left, then the error message reported above (Coud not create MokListRT: Invalid Parameter ... error: can't find command 'hwmatch'.)

---

### Post by oldfred on 2022-01-01
Anything related to moklist is then UEFI Secure Boot.
You need a full cold boot and go into UEFI & turn off UEFI Secure Boot.

---

### Post by bingodingo on 2022-01-01
Hi oldfred,
thanks. I'm a little worried that a full cold boot won't allow me to access the uefi setup. 
following an old hint in relation to this problem I got an abreviated error message that made no mention of moklist:
Continuing boot since secure mode is disablederror: no suitable video mode found.
error: can't find command 'hwmatch'.

---

### Post by oldfred on 2022-01-01
You do have live installer flash drive, so you can make repairs.

Normally Secure boot works, but if you have to install proprietary drivers like nVidia and some WiFi drivers then with Secure Boot you have to sign them yourself.
It seems like you need nVidia driver to make it work but you have secure boot on and have not then allowed the nVidia driver to be installed.

[URL="https://wiki.ubuntu.com/UEFI/SecureBoot"]https://wiki.ubuntu.com/UEFI/SecureBoot

[/URL]sudo update-secureboot-policy --enroll-key[URL="https://wiki.ubuntu.com/UEFI/SecureBoot"]
[/URL]

---

### Post by bingodingo on 2022-01-01
Thanks oldfred,
when I try this command I get:
No MOK found.

Any advice?

---

### Post by oldfred on 2022-01-01
I really do not know details on UEFI secure boot with proprietary drivers.
I always turn Secure Boot off.

There have been a few other posts where users did use Secure boot, but I have not saved any links.

---

### Post by bingodingo on 2022-01-01
Is it even possible to turn off secure boot with capsule BIOS?
I don't recall turning secure boot on (very much doubt that I would have), likewise I don't believe I turned Firmware TPM on.
I have a suspicion that the new bios forces the state on these parameters whatever the user selects in settings.

---

### Post by bingodingo on 2022-01-01
Removed the power supply from the graphics card, connected monitor to the MB HDMI output (cpu has an internal GPU, might be causing the problem), changed monitor input and was then able to boot into the bios / UEFI settings.
Secure boot was disabled, CSM was enabled (I set to disable), Trusted computing / Intel Platform Trust Technology both enabled (left as is) - I believe that these settings were chosen as defaults after the upgrade, they are not settings I recall choosing.
Above 4G decoding etc seem to be correctly set - but internal graphics is set to auto. A little dilemma here - I think I have to leave it as auto to get access to the bios (as the nvidia drivers are unsigned), but I seem to recall that it should be set to 'disabled' to gain the resizable bar.

---

### Post by bingodingo on 2022-01-02
Thanks very much for the help Frog, Tea and Fred - very happy to have my computer working again :P

---

