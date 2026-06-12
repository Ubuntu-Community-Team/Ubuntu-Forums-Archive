---
title: "How do I make Ubuntu installer boot in uefi?"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by 0310aditya on 2014-08-29
Hi all,

Recently I made a USB bootable disk with Ubuntu 14.04.1 64 bit on it. I booted into the USB and for a while all I so was a black screen until finally the Ubuntu screen came up and booted into the live USB. But I know for a fact it didn't boot in uefi mode because it didn't have the grub menu at all. When I clicked install Ubuntu it wouldn't detect my windows 7 installation. I assume its because it isn't in uefi mode. Keep in mind that USB Legacy is turned on in my BIOS (It doesn't recognize the USB if its off). Do I need to make a separate efi partition?? How do I get ubuntu to install in uefi mode? BTW my computer IS  efi because the disk is GPT and boot-repair says "efi detected". PLEASE HELP!!

---

### Post by uRock on 2014-08-29
Hello, 

While you wait for someone who can help you through it, you may want to check this out [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Cheers & Beers,
uRock

---

### Post by 0310aditya on 2014-08-30
> **uRock said:**
> Hello, 

While you wait for someone who can help you through it, you may want to check this out [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Cheers & Beers,
uRock

Hey thank you for your reply! Another problem is that there is no option in my bios for me to turn uefi on or off. The only option is turning USB legacy on or off. I'm using phoenix securecore tiano setup.

---

### Post by priyesh2 on 2014-08-30
I think your PC has default Legacy mode on..

To turn  ON UEFI mode, Just **disable Legacy Option** in Bios>>System Configuration>> Boot Option.


Also i have same problem, Ubuntu installer is not detecting my Windows 8 (in legacy mode), well i will try it in UEFI mode

---

### Post by 0310aditya on 2014-08-30
> **priyesh2 said:**
> I think your PC has default Legacy mode on..

To turn  ON UEFI mode, Just **disable Legacy Option** in Bios>>System Configuration>> Boot Option.


Also i have same problem, Ubuntu installer is not detecting my Windows 8 (in legacy mode), well i will try it in UEFI mode

Thanks for your reply. As metioned in the earlier post i made, my bios (phoenix securecore tiano setup) has no option to turn uefi booting on or off or turn legacy on or off. The only option is to turn "usb legacy" on or off but if i turn USB legacy off it doesn't recognize my USB! The options in my BIOS are quite limited the only things i can do is change date, time, Usb le gacy, boot order, intel virtual technology and AHCI or compatible. The funny thing is that i Used to have a ubuntu 12.10 installation running alongside windows 7 perfectly fine! But one day i was stupid and deleted everything and upgraded to windows 8 but that didnt work out so i erased everything and installed windows 7. Now i want ubuntu back again alongside windows but it doesnt detect my operationg system. Every time i boot my usb it just shows a black screen for a while and eventually the ubuntu logo will pop up and it will boot into the installer. What do i do??

---

### Post by LostFarmer on 2014-08-30
How did you make the usb stick ?

---

### Post by grahammechanical on 2014-08-30
First of all, the Ubuntu live session does not use Grub. So, do not expect a boot menu when you run the live session.

 Secondly if the BIOS/UEFI is set to load in legacy mode then the live session will also run in legacy mode and Ubuntu will be installed in legacy mode.

Thirdly, the question to ask, is why does the installer not detect the Windows partitions? Please use a Windows utility to examine the hard disk and partition structure, Then take a screenshot and post the image here.

Another thing you can do to run the live session and open the Disks utility. Does that recognise the Windows partitions.

Oh, one more thing. where is the link to the Boot Repair report? It would be useful to see what Boot Repair says and what it offered to do to repair things.

Regards.

---

### Post by 0310aditya on 2014-08-31
Hi guys,

Thanks for your help. I ended up accidentally zapping my gpt data  structures from the terminal (some guy online to me to do it) so then (obviously) windows would not boot anymore. Then all of a sudden (after windows would not boot) the ubuntu install usb booted into grub 2 and gave me a choice of installing ubuntu, trying ubuntu without installing, and OEM install. So then i was eventually to lazy to re-install windows so i backed up my data using the ubuntu live usb and i erased my disk and installed ubuntu in uefi mode. My question is why wouldn't ubuntu recognize my existing windows partition (before the data structers were destroyed) AND the efi boot system? And like i said before my laptop DOES NOT recognize the usb disk unless it is set in 'USB legacy" mode. I'm currently typing this from my ubuntu 14.04.1 installation.

Edit: In reply to grammechanical when i had windows it was a basic gpt disk. I had a 200 mb efi partition. and a 2nd 80GB NTFS partition. My bios options are rather limited so like i said i can't turn legacy on or off or uefi on or off.

---

### Post by ubfan1 on 2014-08-31
@grahmmechanical -- In a UEFI boot, the live media actually does use grub (well shim first), just not started in the legacy way from the MBR.  All the UEFI criteria are met -- FAT filesystem, Boot flag, and for removable media (CD/USB) the boot loader in /EFI/BOOT/BOOTX64.EFI (that's shim), with grubx64.efi in the same directory.  So for a UEFI boot, grub should show up offering the try, install, etc. choices.  For legacy boots, the MBR is used for starting syslinux.  So the boot should be an easy way to tell what mode the machine is in.

---

