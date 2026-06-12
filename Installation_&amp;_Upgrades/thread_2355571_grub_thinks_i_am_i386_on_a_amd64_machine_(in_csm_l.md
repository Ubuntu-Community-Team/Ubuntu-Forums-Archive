---
title: "grub thinks i am i386 on a amd64 machine (in csm legacy mode)"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by jeff666 on 2017-03-14
i know this because when i look in grub dir i have "/boot/grub/i386" for the modules instead of /boot/grub/amd64 (it also contains a limited amount of modules, not including png or jpeg) So grub wont allow a splash-image and  its resolution looks terrible. When i tried installing with  uefi mode i get /boot/grub/x86_64-efi and grub works/looks fine. Secure-boot makes installing virtualbox, video drivers, etc a painful experience,to bad i can't turn off secure boot and just use uefi mode :mad:. i have actually tried this on multiple computers macbook 13" and asus z170 desktop, both worked the same. any ideas? fixes? a way to install grub amd64 version? thanks a ton.

---

### Post by ajgreeny on 2017-03-14
> **jeff666 said:**
>  Secure-boot makes installing virtualbox, video drivers, etc a painful experience,to bad i can't turn off secure boot and just use uefi mode :mad:.
Is this machine a mac?
Why can you not turn off secure boot? I was under the impression that the UEFI standard made that a required option in the UEFI setup.

Is there some reason that you are not telling us about that makes it is impossible for you?

Tell us more about the hardware specs, make of computer, motherboard, version of Ubuntu, etc, etc, and we may be able to help more.

---

### Post by oldfred on 2017-03-14
My Asus Z97 only installed in UEFI mode with "Other" not "Windows" which was really the UEFI secure boot setting and then with UEFI only on USB boot. Even UEFI & Legacy only booted in CSM/BIOS/Legacy mode.

---

### Post by jeff666 on 2017-03-14
@ajgreeny no its asus z170 pro gaming you deffently right about the uefi standard (i was reading wikileaks the other night and read atlot of the eufi manual linked to it ) but my uefi menu has the option turn secure boot off blocked and im using 16.04 lts (i am using server image becuase i like to choose software i want myself) 

@old fred thanks so much i should have just read my owners manual it says " {windows uefi mode] .... [Other OS] get the optimized function when booting on windows non-uefi mode. Microsft secure boot only supports windows uefi mode." SO i should just select "other os" and turn off csm mode? or wil lthat still give me problems with drivers do i need csm/uefi only on?

---

### Post by oldfred on 2017-03-15
A few systems (Dell?) suggest having CSM on, but boot in UEFI mode. Some found issues with CSM off.
I think my system worked best and most suggest if using UEFI, CSM should be off.
But systems all seem to have different ways to turn on & off the various settings. My other UEFI system can only turn on UEFI, when in the CSM sub-menu??

---

### Post by Dennis N on 2017-03-15
On my Asus H97M Plus system I use the "Other OS" boot mode, and leave the CSM set to "enabled". That has worked fine for me. Selecting "Other OS" will mean no secure boot check is done.

Note: The first UEFI install I did was with the "Windows UEFI Mode" and that did work with Ubuntu on this board. I later changed it to "Other OS" because I wanted to multi-boot other OSes that did not work with secure boot.

---

