---
title: "Where is the boot manager / grub in Windows 8 dual booting with Ubuntu?"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by rehcarlos on 2013-08-22
I have an Asus notebook with Win 8 pre-installed. In the options, Legacy was enabled, and secure boot was disabled. I installed Ubuntu using a flash drive. My problem is that after installing, I can't access Ubuntu. If I use my flash drive again, it says Ubuntu 13.04 is already installed.

Then, I tried boot-repair. It was okay, and gave me this link: [http://paste.ubuntu.com/6013490/](http://paste.ubuntu.com/6013490/)

I still can't seem to boot into Ubuntu.

It always goes straight foward to Windows 8.

Any ideas? I'm really lost.

---

### Post by Cheesemill on 2013-08-22
*Thread moved to **Installation & Upgrades**.*

---

### Post by Yougo on 2013-08-22
Perhaps a silly suggestion, but does holding the left SHIFT button at boot show the GRUB menu?

> 
GRUB_DEFAULT=0
**#GRUB_HIDDEN_TIMEOUT=0**
**GRUB_HIDDEN_TIMEOUT_QUIET=true**
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


[AskUbuntu says:](http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry)
> 
    You can change the default from 0 to any number, corresponding to the entry in the Grub bootup menu (first entry is 0, second is 1, etc.)
    You can change the "hidden timeout" (no menu); and also display the countdown (TIMEOUT_QUIET=false)
    You can force the grub menu to show by commenting out the two GRUB_HIDDEN lines with a # at the beginning of the line

    And set the grub menu timeout (default is 10 seconds)

    Make your changes, press Ctrl-S to save and Ctrl-Q to exit.
    Important: Open a terminal with Ctrl-Alt-T and type sudo update-grub to apply the changes you just made.
    Reboot and you should see your timeout/default entry change.


to comment out both HIDDEN_TIMOUT lines to force grub to show.

the first menuentry is ubuntu and GRUB_DEFAULT=0, so it should go with that by default. don't know why it doesn't. maybe if you can get GRUB menu to show, you could choose ubuntu manually?

---

### Post by QDR06VV9 on 2013-08-22
> **rehcarlos said:**
> I have an Asus notebook with Win 8 pre-installed. In the options, Legacy was enabled, and secure boot was disabled. I installed Ubuntu using a flash drive. My problem is that after installing, I can't access Ubuntu. If I use my flash drive again, it says Ubuntu 13.04 is already installed.

Then, I tried boot-repair. It was okay, and gave me this link: [http://paste.ubuntu.com/6013490/](http://paste.ubuntu.com/6013490/)

I still can't seem to boot into Ubuntu.

It always goes straight foward to Windows 8.

Any ideas? I'm really lost.

Going over your pastebin I had seen this,
```
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
SecureBoot maybe enabled.
```
You may have to enter bios and setup secureboot.
Regards

---

### Post by oldfred on 2013-08-22
If you installed in Legacy/CSM/BIOS mode you have to go back into UEFI and with legacy mode set boot Ubuntu. Windows will not boot from legacy mode.

But it looks like Boot-Repair converted your install to UEFI, by uninstalling grub-pc (BIOS boot) and installing grub-efi(UEFI). But you still have to go into UEFI menu and choose ubuntu as boot option. You will want to set it as default. Do not turn secure boot on as Ubuntu does no have the signed kernel. If you really want secure boot you have to install the secure boot version of grub and kernel.

Also use the new UEFI Windows boot entries from grub not those from os-prober as they do not work.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by rehcarlos on 2013-08-22
> But you still have to go into UEFI menu and choose ubuntu as boot option. You will want to set it as default
Yep it worked!

After installing Ubuntu, I remember trying to change boot order, but Ubuntu wasn't there. I think that it appeared in the boot list, after boot-repair...

Anyway, for future people that access this topic:
I installed Ubuntu in an Asus X401U notebook, that have Windows 8 pre installed, using an flash drive with Ubuntu 13.04 image mounted. After installation, I had to change boot list order (UEFI menu) in order to make grub menu appear when I turn on the notebook.

---

### Post by oldfred on 2013-08-22
Glad you got it working. :)

---

