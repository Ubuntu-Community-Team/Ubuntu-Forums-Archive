---
title: "Best way to dual boot + GRUB??"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by unglundun on 2011-07-26
I've been planning on setting up my main 64-bit PC with Windows and Ubuntu (possibly Kubuntu) in a dual boot. I've used Windows and Ubuntu in the past, but I'm not familiar with GRUB. Right now my system is set up with Windows Vista on a four 640gb drive software RAID 0+1. Two drives are striped in a RAID 0, and the other two mirror the stripe. This has worked out pretty well for me, however since I'll be reformatting anyway I'm going to switch over to a regular RAID 0 with all four drives for added performance. I have a 2TB network storage drive to back up any data that I need. The risk of losing everything if one of the drives in the RAID 0 goes down isn't significant to me, because I've backed up everything vital to me.

For my reformat, the following are the parts that I want to install:
-Windows 7
-(K?)Ubuntu
-GRUB

In order to set these up in the ideal way, on a new RAID 0 drive, what order should the installs be done in? For GRUB to use the MBR, does it need to be installed first? I'm not sure how GRUB is installed anyway, but if I remember correctly it needs to be attached to a Linux install? The GRUB install is definitely something that I need to read up on more before I try and install it, but I'm just making sure that I do so in the right order with the operating systems.

Thanks for taking the time to read this, it is much appreciated!

---

### Post by YesWeCan on 2011-07-26
I don't have all the answers but I can add some info. that may help you ask the right questions.
You can save a lot of hassle by installing all your linux on a separate disk to your Windows RAID.
Windows RAID is not compatible with linux RAID.
I'm not sure whether Grub can boot a Windows RAID 1+0.
You can make a linux RAID 1+0 easily and Grub will boot it no problem. But Windows will not run on it.

Grub is a bootloader that requires a custome MBR boot code. It is not compatible with the standard MBR boot code that Windows uses. Grub's bootloader program has to be associated with a linux OS installation - it does not (without some crafting) work stand-alone.

---

### Post by unglundun on 2011-07-26
> **YesWeCan said:**
> I don't have all the answers but I can add some info. that may help you ask the right questions.
You can save a lot of hassle by installing all your linux on a separate disk to your Windows RAID.
Windows RAID is not compatible with linux RAID.
I'm not sure whether Grub can boot a Windows RAID 1+0.
You can make a linux RAID 1+0 easily and Grub will boot it no problem. But Windows will not run on it.

Grub is a bootloader that requires a custome MBR boot code. It is not compatible with the standard MBR boot code that Windows uses. Grub's bootloader program has to be associated with a linux OS installation - it does not (without some crafting) work stand-alone.

Thanks for your response! Remember that I'm ditching the RAID 0+1 in favor of a regular, plain old RAID 0. Does that affect any of the compatibilities as opposed to the RAID 0+1? I'm assuming it's no different but I'm still unfamiliar with this area.

In regards to the GRUB compatibility, from what you mentioned it sounds as if I may be able to set up my system as originally intended, but slightly varied. If I did a total format of the drives and set up a RAID 0 from the BIOS, then installed Ubuntu, from which I could install GRUB, would I be able to fit Windows 7 onto this drive at all? Or as a RAID 0 with Linux does that make it impossible for Windows 7 to exist on that drive? I know you said that Windows RAID and Linux RAID are not compatible. Does this also apply to a RAID 0 that is controlled by the motherboard's BIOS? I'm not sure if you meant that a Linux-controlled RAID would be incompatible with Windows, or that ANY RAID with Linux on it would be incompatible with Windows, regardless of how it is set up or controlled.

If it turns out that Windows and Linux RAIDs are completely incompatible, I believe I can still find a way to make this work. With my four 640gb drives, my next option would likely be two RAID 0 drives, striping two drives to make two RAIDs, one for Linux and one for Windows. In this case of two seperate RAIDs, I'm not sure how GRUB would fit into the situation or if it would be possible to control two seperate RAID sets with GRUB. 

Again, I really appreciate your response. Thanks for shedding some light onto the situation for me!

---

### Post by YesWeCan on 2011-07-27
Have a look at this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
It looks like you can install Ubuntu and Grub to your dmraid.

Unlike linux, Windows requires some special hardware on the motherboard to enable it to do software RAID. linux does not. Linux can use the Windows RAID format but Windows cannot use the linux format. So I suppose they are semi-compatible.

As long as Grub can understand the formats it can boot as many OS's on as many RAID arrays as you like.

---

