---
title: "Other ways of entering recovery mode?(without Shift holding and esc toggle)"
date: 2024-05-15
forum: Installation &amp; Upgrades
---

### Post by mikelemon1 on 2024-05-15
Using ubuntu 22.04 with HP-Z1-G8-Tower-Desktop-PC

I've played a little with building softwares from source and maybe because of messing with the apt packages or the upgrade from 3 days ago might have bugged my ubuntu
and rebooting after building (freecad and wXWidgets) the keyboard and mouse are unresponsive.
Now I've heards somewhere you can enter from the grub menu the recovery mode and from the bash terminal there input some commands to fix the apt no keyboard and mouse detection error
but all I'm able to access beyond the ubuntu is the HP Bios "Start up" Menu by pressing esc repeatedly and in the boot menu choose the "UEFI-ubuntu" options which just boots to the same stuck logins screen 
(Holding shift after the bios intro don't pop the grub menu) 

What are other methods to access that mono color screen of how'd access the system bash externally if for example I want to use and external nvme reader to fix it?

---

### Post by oldfred on 2024-05-15
Grub uses the same driver as UEFI/BIOS since system is not yet mounted.
Often issue then is a setting in UEFI/BIOS for USB support or keyboard/mouse settings.

HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings
But in UEFI mode Ubuntu uses escape key to get to grub menu. Just after UEFI/BIOS screen, but before grub menu would normally appear.
You then have to try several times and/or spam the escape key to find correct timing.
Shift was only used with BIOS installs.

Can you boot live installer? 
Boot-Repair primarily updates or re-installs grub as fix, but report can show other configuration issues.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mikelemon1 on 2024-05-16
Yes but what incase the ubuntu bios with esc doesn't work? 
Is there a way to reach the bash terminal of the broken ubuntu with another ubuntu machine (with the broken ubuntu mounted on external usb nvme reader to it)?

---

### Post by oldfred on 2024-05-16
Post link to summary report, so we can see issue. 

You can chroot into your system. And reinstall grub or make other repairs.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

---

### Post by Impavidus on 2024-05-17
The easy way to get to recovery mode is to show the grub menu automatically on every boot – even if just for 2 seconds. But of course, that has to be configured before your system breaks.

I think boot repair can actually do that: unhide the grub menu. But I never tested it on recent versions of Ubuntu.

---

### Post by MAFoElffen on 2024-05-18
The answer to your first (main) question, is that if, at the Grub2 Boot menu, you either use a Recovery Mode Boot option, or enter 'nomodeset recovery" as kernel boot parameters... But to do either of those, you need to be able to get to the Grub2 Boot menu. 

You still need to run, the 'boot-info' info script of boot-repiar, so that people have the details to help you.

What some have suggested... Editing the Grub2 menu to show at least 2 seconds, gives me a chance to use the Grub2 menu, in case something happens. A useful safeguard for the just-in-cases... Something I do for all my machines, and most of my customer's.

Example, in your case: Let's say you wanted to chroot into your installed Linux OS, to edit your Grub2 defaults, so that the Grub2 Menu shows, each time you boot, so you don't have to use a hot-key to get around it being hidden... I say chroot, because that is what it would need to pick up and apply the changes on a machine that will not boot... 

"chrooting into an installed system to repair it and make change to repair it..." That is what the Ama-Gi Project LiveCD was based on to repiar Linux Systems. That is how Boot-Repair makes repairs. 

Reading all your posts... you want to do something that could be done in a chroot to repair your system. You do not provide the details to tell you how to do that. We would have to know those details of your system. We are not clairvoyant. We cannot read minds. 

I don't understand your resistance in doing that. That is shooting yourself in the foot. Without that, each additional question you ask, you will only get a generalized answer back... But not a tailored solution.

Please run the report and post the URL to where it gets uploaded to a pastebin. Help others to be able to help you. Please be part of your own solution.

---

