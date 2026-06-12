---
title: "HP Elitebook 8570w"
date: 2018-11-20
forum: Installation &amp; Upgrades
---

### Post by gehringj on 2018-11-20
Hello,

PLEASE HELP.

I recently purchased the above named computer and my task is simple: boot from a live usb that I am aware is bootable on other machines. I have tried so many combinations of different BIOS settings that I am losing track. I have tried turning on legacy mode, etc. as well as the other standard procedures but ultimately I can never get it to boot into the live environment. I am using a BIOS version 68IAV Ver. F.70 and I will paste a couple photos showing my BIOS screen. I have literally tried everything. The boot failure pictures are displayed with Legacy mode on! The pictures taken are followed by a blank screen until one decides to retry the process again in an attempt to change some settings and hopefully boot on the next try.

I have restored the BIOS now to its default settings and I will be standing by for instructions. I really need to be able to boot linux on this thing tonight! I have no other machine to complete my work on. 

PLEASE PLEASE HELP

I will post the pictures soon after they are uploaded into my system.

---

### Post by gehringj on 2018-11-21
[ATTACH=CONFIG]281726[/ATTACH]

Here is a picture taken right before it hangs on a black screen before booting.

---

### Post by ubfan1 on 2018-11-21
Looks like you have Nvidia hardware, so did you try adding the word "nomodeset" to the grub boot line starting with "linux" at the "quiet splash" words?
There are other HP problems, such as only booting "windows Boot Manager" named bootloaders, so check this site and askubuntu for other suggestions.

---

### Post by gehringj on 2018-11-21
Is the grub boot line accessible through the bios? I do not have to be booted into the live environment do I? I really appreciate your help throughout this process!!!

Joey

---

### Post by ubfan1 on 2018-11-21
Assuming Windows on your new PC is in UEFI mode, it won't be seen by grub booting in legacy mode.  Find the BIOS/UEFI setting option to boot UEFI USB, not legacy USB.   Grub should show up , but if it sees only one (or none?) operating systems, it immediately boots the default kernel (which is what you posted I think).  In U"EFI mode, it should display the grub menu, type any key to avoid a timeout boot to the default, and then type "e" to edit the grub default, adding the nomodeset.

---

