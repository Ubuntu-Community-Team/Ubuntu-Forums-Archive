---
title: "Reboot and Select proper Boot device"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by jim-anderson on 2015-07-16
I have an Asus X551M laptop. I had Lubuntu, Windows Vista and Crunchbang Linux installed on it. The laptop crashed and the boot records must have gotten messed up because I was no longer able to boot. When I try to boot, I get the following error message:

>>> Reboot and Select proper Boot device
>>> or Insert Boot Media in selected Boot device and press a key

In the UEFI menus, I have set the options to enable CSM and disable secure boot, which is what I have done in the past to get the Linux O/S to run on the laptop. I have tried running the Lubuntu install disk and it seems to work, but when it completes the installation and I try to boot from disk, the above error message comes up.

I tried running boot-repair, but that did not help.

Can anyone help me to get Lubuntu (or Kubuntu) installed so that can be booted?

Jim A

---

### Post by yancek on 2015-07-16
If you have run boot repair, it has an option to Create BootInfo Summary.  Select that and then post the output here and someone should be able to help.

---

### Post by jim-anderson on 2015-07-16
I have worked on the system and tried 'Boot Repair' and a supergrub2 CDROM, but I was not able to make progress. I then tried systemrescueCD and I was at least able to boot into an old version of lubuntu (version 13.x.x) that was on the hard disk. I'm not sure why, but there are many things that don't work on this version. For example, I cannot bring up the  Synaptic Package Manager.

If nothing else, systemresuceCD indicates to me that Linux can still be booted on this laptop.

Yesterday, I tried running the Lubtuntu 14.04.01 installation CDROM. It ran completely through, but I cannot find what partition is was installed in. Also, when it finished grub does not get setup properly and I cannot boot into it, but I don't see any obvious error messages.

---

### Post by jim-anderson on 2015-07-16
@yancek

I just saw your message. Unfortunately, I have family commitments today, tomorrow and Saturday and then my wife and I will be on vacation. I will do my best to get a look at this late tonight or early tomorrow morning. Otherwise, I will be silent for over a week. But I will try running boot repair with the option you suggested as soon as I can.

Jim A.

---

### Post by jim-anderson on 2015-07-16
Well, I made the time to get the Bootinfo Summary. The generated file was too large to attach, so I split the file into 4 pieces, bootInfoA.txt, bootInfoB.txt, bootInfoC.txt and bootInfoD.txt. If you read them in that order you will have the full report.

I will try to find the time to get online over the next week or so, I just don't know when.

Jim A.

---

### Post by grahammechanical on 2015-07-16
If I remember correctly, 12.04 was the last version to have Synaptic Package Manager installed by default.

Also, the two versions from 2013 reached end of life sometime last year. So, their repositories are now closed and it is not possible to install anything or update them.

When we run Boot Repair its report is stored on the internet at pastebin and we are provided with a URL. Publishing the URL is enough for us to access the report.

A lot depends on what you were doing when the laptop crashed and what OS was being used at the time. It could mean that you need to re-install the Linux boot loader. It could mean something more serious.

If you can load into that 2013 version of Lubuntu and if you only have one hard disk, you could try opening a terminal and running:

```
sudo grub-install /dev/sda
sudo update-grub
```

Watch the printout on screen. Does the update to grub detect all the OS? If you are then able to get into the Lubuntu that you really want to use (the Lubuntu that is still being supported) then do so and run those two commands again. They will then put the supported Lubuntu in charge of the boot loader.

Regards.

---

### Post by oldfred on 2015-07-16
This shows the pastebin link and suggestion to just copy link to forum. Lot easier for those who want to help you to help you.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I just looked at first text file. You have grub installed everywhere which can lead to issues. Once you decide to use UEFI, everything should be based on UEFI boot. 
But you have grub installed to the MBR for BIOS boot and you even installed grub to the efi partition boot sector which was from a BIOS install but specifying the efi partition for grub. You should always specify the drive like sda for install of grub. 

Are you booting in UEFI mode or BIOS mode?

---

### Post by jim-anderson on 2015-07-18
@grahammechanical

This is to acknowledge that I read your message. I will do as you say and reply to you over, hopefully over the next few days. Before I do that, I am going to respond to '
		oldfred' because he seems to have spotted an error in the BootInfo Summary.

My apologies to both you and oldfred, and others for not posting the URL. I did not realize the report was stored with a URL. I will have to go back and read about the procedure and make sure I understand where and when the URL gets set up. I will take a look at the URL provided by oldfred.

Jim A.

---

### Post by jim-anderson on 2015-07-18
@oldfred

I am booting in BIOS mode.

Just a little history here. I originally set up this laptop a year or 2 ago and it was the first PC that I encountered that supported UEFI. It was a struggle to get anything working. The laptop  came with Windows loaded and I did not want to destroy Windows, so I started installing Crunchbang Linux (Waldorf), which was my preferred Linux distribution at the time (not anymore since Crunchbang is sort of in maintenance mode). If I remember correctly, the Crunchbang installation went ok, but not perfect. After the installation, Crunchbang worked, but the internal wireless adapter (Wifi interface) did not work. As part of the installation, Crunchbang install finished by writing grub to disk. Because I wanted to have Wifi support when I was on the road, I also installed Lubuntu, I think version 13.x.x, which was current at that time. This worked and I was able to use the Wifi adapter when Lubuntu was booted. I believe the Lubuntu install also installed grub. For both the Crunchband and Lubuntu install, there was no choice regarding installation of grub.

Since installing Linux, my laptop has been VERY stable and I rarely had to boot, especially since I picked up another laptop from ebay and when I was on the road, I used that laptop, not the one currently being worked on. When I did need to reboot, the laptop reboot ok initially, but I did eventually have some troubles with the booting process, until just recently, the laptop could not be booted at all, except that I found recently that I can still boot Lubuntu when I used the systemRescueCD.

Ok enough background. Now to answer you question, I boot in BIOS mode, meaning that I have CSM mode enabled and the Secure Boot Mode disabled.

---

### Post by jim-anderson on 2015-07-18
@grahammechanical

I booted lubutu and got the following:

[FONT=arial black]furillo: sudo grub-install /dev/sda
Installing for i386-pc platform
Installation finished. No error reported.[/FONT]

Then I ran:

[FONT=arial black]furillo: sudo update-grub
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows 8 (loader) on /dev/sda4
Found Debian GNU/Linux (7.0) on /dev/sda7
done[/FONT]

Note: I would normally box the information as 'code' but my browser does not show this option, so I cannot select it.

---

### Post by oldfred on 2015-07-18
Code is the # icon in the advanced editor.

UEFI & CSM/BIOS are not compatible.
Or even if BIOS grub shows Windows in menu, if Windows is UEFI it will not boot it. But you can change from CSM to UEFI in UEFI boot menu or one time boot key. Then you start system in correct mode to boot.

---

