---
title: "I'm having problems installing ubuntu on my medion device"
date: 2019-11-20
forum: Installation &amp; Upgrades
---

### Post by jorgeba01 on 2019-11-20
Hi, I would like to get some help. The fact is that in recent days I have been trying to install ubuntu. I have tried to install versions like 19.10 or 18.04 and in no case was it possible to install it. I've tried other distributions like pop_os and it doesn't work for me either.
At first I thought it could be my USB memory, but when trying with others I could not do anything, and I tried to flash the memory with several programs such as rufus, edge, or yumi. In all cases I get a black screen for a few seconds and then a message which I do not understand.
I hope you can help me since I am very lacking this operating system for my studies and it is not enough with virtual machine for it. Thank you very much.  
My laptop is a Medion P6685.

Here I leave some images about the text and my rufus configuration: [https://mega.nz/#F!rHQHjAhC!c8ogiz_WT-82BXFrheqrcg](https://mega.nz/#F!rHQHjAhC!c8ogiz_WT-82BXFrheqrcg)

---

### Post by oldfred on 2019-11-20
Is this 32 bit UEFI or 64 bit UEFI. Generally only some small/tablet type systems were 32 bit UEFI.
You typically want to boot new systems in UEFI boot mode.

What video card/chip?
Black screen typically means you need nomodeset and/or other boot parameters.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Another Medion:
[https://ubuntuforums.org/showthread.php?t=2387481](https://ubuntuforums.org/showthread.php?t=2387481)

---

### Post by jorgeba01 on 2019-11-20
Hi, oldfred and thanks for answering so fast. I tried to use the nomodeset, I forgot to say. 
My video card is a mx150 an i have a 64 bit BIOS UEFI

---

### Post by oldfred on 2019-11-20
At very least you need nomodeset to boot live installer. You may still need other boot parameters.

You need to have UEFI settings changed. But not familiar with your system.
Often best to have UEFI secure boot off (my motherboard calls it "Windows" or "Other" but fine print say use "Other" for Windows 7 as it does not support Secure Boot. Also turn off fast boot in UEFI and fast start up in Windows.

You also need nomodeset on first boot once installed or until you install proprietary nVidia driver.
Very newest Ubuntu now offers to install nVidia driver.

Lots of details in link in my signature below (maybe too much). But at least review install steps.

---

### Post by jorgeba01 on 2019-11-22
I have tried writing nouveau.modeset=0 in the boot menu option but it didn't work

---

