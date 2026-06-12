---
title: "Disk with Ubuntu not booting in other PC"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by Joel_Oliveira on 2015-03-26
[FONT=Helvetica Neue]I have installed Ubuntu Server 14.04.1 (Lubuntu Minimal Installation) on a SSD disk through a USB pen. Everything whent fine.[/FONT]
[FONT=Helvetica Neue]After that, I need do duplicate the hard drive to use the same installation on another computers.[/FONT]
[FONT=Helvetica Neue]When I connect the the disk to other computers I can't boot from disk. It says "Error: No boot disk has been detected or the disk has failed"[/FONT]
[FONT=Helvetica Neue]If I plug the disk to the computer I installed the system it works fine. The computers are the same model HP Compaq Pro 4300.[/FONT]

---

### Post by Joel_Oliveira on 2015-03-26
[FONT=Helvetica Neue]I'm thinking if it could by beacause the usb pen was botted in UEFI mode. And may have some protection when using in another system. Any way to disable this protection? Or I have to install the system again in legacy?[/FONT]

---

### Post by grahammechanical on 2015-03-26
@Joel_Oliveira

If you installed Lubuntu on an SSD in a machine with EFI mode activated, then the second machine must also have EFI mode activated for the OS to load. Both machines must be set to have the same boot system EFI or legacy if we are going to switch drives like this. 

I may be mistaken. Is it the SSD that you are swapping out or the USB pen that you are trying to use in the second machine?

Regards.

---

### Post by Joel_Oliveira on 2015-03-26
@grahammechanical They have both EFI mode activated. The USB Pen was only  to install the OS. It's the SSD I'm swapping between machines

---

### Post by Joel_Oliveira on 2015-03-26
I need to hand to the client the disk ready in a couple of ours and still no luck...
I did the most simple experiment. Two machines side-by-side, exact same model. I load the BIOS/UEFI defaults, install a ubuntu server with default options on the SSD. Then use the same SSD on the other machine, power up, load BIOS/UEFI defaults and I can't boot the Ubuntu Server OS. 

If I change back to the machine I installed the system it woks fine...

---

### Post by JohnnyComeL8ly on 2015-03-26
Do you have the same UEFI in both MBs?  I'm thinking that maybe the defaults might vary in different versions.

---

### Post by Joel_Oliveira on 2015-03-26
It's the same computer model, so I guess the UEFI version is the same. I plugged a HD with windows from another computer and it works fine. At this point I just think I'm doing something stupid, cause none of this makes sense.

---

### Post by yancek on 2015-03-26
Asking the obvious, did you put the EFI partition on the SSD when you installed the server to the first machine?

---

### Post by oldfred on 2015-03-26
Even with efi partition on external drive, you probably do not get the /EFI/ubuntu folder on the external drive. And if an external drive, you have to boot from /EFI/Boot, by copying grubx64.efi into that folder and renaming it to bootx64.efi.

I just installed another copy on my sdb drive and definitely told it to install to sdb, but it put the new install's efi folder in sda and overwrote that ubuntu folder.

Server does not have live mode, but you should have one just for repairs anyway. Download desktop version and add Boot-Repair. Post link to summary report so we can see what is where.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

