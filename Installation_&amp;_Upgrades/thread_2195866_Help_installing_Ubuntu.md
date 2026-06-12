---
title: "Help installing Ubuntu"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by miguel.renaud on 2013-12-26
Okay I'll start from the beginning. 

I burned Ubuntu 13.10 to a DVD. I turned on my computer and went in to my bios. I diden't let me boot from the DVD so I googled it and turned off Safe Boot and Turned on Legacy Sources. After that I booted on to the CD. And it diden't allow me to boot along side Windows 8. So I created a partition and installed it on that blah blah blah.. Anyways, I get on to Ubuntu after the installation is complete. I install Skype, tell my friends I have it. Then to see if I can boot back to Windows 8 I reboot my computer.
I get the ubuntu boot manager screen that gives me a few options something like:
-Ubuntu
-Windows Boot Manager
I select Windows Boot Manager. So it boots to windows 8. I was a little bit mad that I diden't get the Windows 8 boot manager but what ever. Then I get in to Windows 8, restart my computer and it boots straight to Windows 8. I restart my computer like 4 more times. Same thing. So I did a lil research. Torrented this: EasyBCD 2.2.
I ran it created, a new boot thing and then I restart my computer. I get the Windows 8 boot manager. Then when I select Ubuntu I get some sort of error from boot manager I wrote some of it down but my computer reset. I got something like can't find  /NST/AutoNeoGrub0.mbr

Any suggestions? I don't mind reinstalling Ubuntu. Especially if I can make the Boot Alongside Windows 8 option appear.

---

### Post by westie457 on 2013-12-26
Welcome to UF.

A couple of questions first. Did you burn the 32bit or 64bit version of Ubuntu to dvd?

In your research did you find any information about disabling Windows 'Fastboot'?

The reason it did not allow you to install along side Windows is the Windows partitions are still mounted because of the way Windows goes into 'hybrid-sleep'

the answers you give to the questions will partly decide if re-installing is necessary.

---

### Post by miguel.renaud on 2013-12-26
I burned the 64-bit version of Ubuntu 13.10 to my DVD. And I did not see anything about fast boot nor have I disabled it and I believe seeing that it was enabled in my BIOS.

Is there a solution to this problem?-"[COLOR=#000000]The reason it did not allow you to install along side Windows is the Windows partitions are still mounted because of the way Windows goes into 'hybrid-sleep'"[/COLOR]

---

### Post by oldfred on 2013-12-26
You need to turn fast boot off. And best to install Ubuntu in UEFI mode not CSM/BIOS/Legacy. You cannot easily dual boot if one system is UEFI and the other is BIOS based boot. They are not compatible so once you start booting in one mode from UEFI menu you cannot switch with grub menu. 

 Backup efi partition and Windows partition before Install of Ubuntu. How you boot installer is how it installs.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by miguel.renaud on 2013-12-27
> **oldfred said:**
> You need to turn fast boot off. And best to install Ubuntu in UEFI mode not CSM/BIOS/Legacy. You cannot easily dual boot if one system is UEFI and the other is BIOS based boot. They are not compatible so once you start booting in one mode from UEFI menu you cannot switch with grub menu. 

 Backup efi partition and Windows partition before Install of Ubuntu. How you boot installer is how it installs.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks! That seemed to be the answer. I just turned off fast boot and installed ubuntu 12.04 alongside Windows 8. Even though I'm still using the Ubuntu boot manager, atleast it works.

---

### Post by miguel.renaud on 2013-12-28
> **miguel.renaud said:**
> Thanks! That seemed to be the answer. I just turned off fast boot and installed ubuntu 12.04 alongside Windows 8. Even though I'm still using the Ubuntu boot manager, atleast it works.

Okay, nevermind, i got it working but it seems Windows 8 has taken over again. I really need to grab some files from my ubuntu side. I don't want to reinstall Ubuntu just yet. I'm really nervous as I have coded an application for work. All I need is a ew folders off of it or to get on the ubuntu side quickly D; 

Any suggesitons..

---

### Post by oldfred on 2013-12-28
Some find Windows keeps resetting itself to be first in UEFI menu. Can you go into UEFI menu and boot Ubuntu entry? Or one time boot key?

Also if reinstalling be very careful. Some are finding that Windows may have turned on hibernation or other issue so installer does not see it. But it may offer to over instal Ubuntu. But since it does not see Windows it just uses entire drive and erases Windows. Only use Something or manual install if reinstalling so you know you are installing to the same / (root) partition.

       NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

      
 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

