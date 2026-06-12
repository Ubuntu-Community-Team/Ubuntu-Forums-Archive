---
title: "Installed Ubuntu, can't boot into it."
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by Baldip on 2013-08-25
Just managed to install ubuntu but I ran into another problem. It won't  let me boot into it. Grub doesn't show up, I have tried boot-repair which doesn't fix anything. 

here is my ubuntu pastebin from boot-repair 
[http://paste.ubuntu.com/6026577/](http://paste.ubuntu.com/6026577/)

---

### Post by Boab1993 on 2013-08-25
Hey baldip, 

This is a very common problem at the moment, it is because you had windows 8.

Have a look here : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Sadly after you make the changes to accompany for UEFI you will need to re-install.

---

### Post by oldfred on 2013-08-25
Actually Boot-Repair can convert a BIOS install to UEFI. But you have to boot Boot-Repair in UEFI mode or in UEFI with secure boot on mode.
Does you system boot Windows with secure boot off. If so I would suggest leaving secure boot off. But to dual boot you need both Windows & Ubuntu in UEFI mode.

 [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

---

### Post by Boab1993 on 2013-08-25
> **oldfred said:**
> Actually Boot-Repair can convert a BIOS install to UEFI. But you have to boot Boot-Repair in UEFI mode or in UEFI with secure boot on mode.

Always good to know these things, thank you for the insight.

---

### Post by Baldip on 2013-08-25
Thing is. When I try to install ubuntu in UEFI mode I end up in the grub menu and if I click install ubuntu or try ubuntu without installing it leave me with a black screen. : /

---

### Post by oldfred on 2013-08-25
That is almost always a video issue, and you need to add nomodeset to linux line. Use e on grub menu, scroll to linux line, replace splash quiet with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Baldip on 2013-08-25
I've already tried that tons of times. I've had no luck.

---

### Post by Baldip on 2013-08-25
I tried it again. I replaced [COLOR=#000000] splash quiet with nomodeset and pressed f10 and I still got the black screen. [/COLOR]

---

### Post by Baldip on 2013-08-25
Can anyone help me please?

---

### Post by oldfred on 2013-08-25
What model HP?

---

