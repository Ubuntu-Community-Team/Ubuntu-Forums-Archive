---
title: "Problems when installing Ubuntu 13.10"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by Colin_Garcia on 2014-01-28
I have downloaded the ubuntu-13.10-desktop-amd64.iso on my Asus Essentio CM6730 desktop for dual booting Ubuntu 13.10 and Windows 8. Unfortunately, I am having some problems. When I boot into the motherboard BIOS to boot through my DVD that I burned the Ubuntu 13.10 ISO to, I select the DVD, and then I get this:

```

Could not open "\EFI\BOOT\fallback.efi": 14
error: variable 'root' isn't set.

```

It then proceeds to the GNU GRUB. I get the options to "Try Ubuntu without installing", "Install Ubuntu", "OEM install (for manufacturers)", and "Check disc for defects". No matter which one I choose, it ends up with a black screen. Sometimes, in the top left corner there is a flashing white hyphen. It stays like that for minutes and minutes. After waiting 20 minutes, I gave up and decided to post this issue in the forums. Does anyone know how to fix this? If it's relevant, here are my CPU specs:

Intel Core i5-3550P
6GB 1600MHz DDR3 RAM
1TB HDD


Thanks!

---

### Post by ajdlc47 on 2014-01-28
Hello Collin_Garcia, I am not as skilled as many others but I do have a few suggestions, first acess your BIOS and make sure that you have UEFI mode enabled. Try that and see if that works. You can try turning off SecureBoot as well, that may help with it too but I am not too sure. If it doesn't make sure that your DVD isn't damaged, also make sure your ISO image is complete and not damaged as well. If everything looks good what you can do is download the Boot-Repair Disc and burn that to either a disc or flash drive and run the BootInfo Summary and paste the link here. I have seemed to notice that that summary helps many of the experts on here to determine what is going on with your hardware. 

Here is the to the Boot-Repair Rescue disc: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hope it helps!

---

### Post by Colin_Garcia on 2014-01-28
> **ajdlc47 said:**
> Hello Collin_Garcia, I am not as skilled as many  others but I do have a few suggestions, first acess your BIOS and make  sure that you have UEFI mode enabled. Try that and see if that works.  You can try turning off SecureBoot as well, that may help with it too  but I am not too sure. If it doesn't make sure that your DVD isn't  damaged, also make sure your ISO image is complete and not damaged as  well. If everything looks good what you can do is download the  Boot-Repair Disc and burn that to either a disc or flash drive and run  the BootInfo Summary and paste the link here. I have seemed to notice  that that summary helps many of the experts on here to determine what is  going on with your hardware. 

Here is the to the Boot-Repair Rescue disc: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hope it helps!

Thanks for replying, ajdlc47! How do I enable UEFI mode and SecureBoot in the BIOS? Or better question, where is it located in an Asus BIOS? I don't think the DVD is damaged because it works on my other Mac laptop. Also, I tried it from a USB and it had the same problem on that as well.

---

### Post by ajdlc47 on 2014-01-28
For Secureboot I am not too sure. You may want to refer to your motherboard's documentation for that. I have an Asus laptop myself so I am hoping our BIOS menus are similar. For the UEFI mode, go to BOOT in BIOS and under that screen one of the first options should say UEFI Boot and that should be enabled. So if you are getting with a USB drive then I want to say it's something on your system then. I would say download the Boot-Repair Rescue disc and burn it on a DVD or put it on a flash drive with the instructions on the webpage and boot to it. Once it's loaded up run the "Recommended" option and then let it do it's thing. At the end, it will give you a Bootinfo Summary link as well, please post that too for the experts to read. The Boot-Repair Rescue disc is kind of my go-to tool when I get errors so you may want to try that if the UEFI mode is already enabled. So hopefully it should fix that issue you are having.

---

### Post by Colin_Garcia on 2014-01-29
> **ajdlc47 said:**
> For Secureboot I am not too sure. You may want to refer to your motherboard's documentation for that. I have an Asus laptop myself so I am hoping our BIOS menus are similar. For the UEFI mode, go to BOOT in BIOS and under that screen one of the first options should say UEFI Boot and that should be enabled. So if you are getting with a USB drive then I want to say it's something on your system then. I would say download the Boot-Repair Rescue disc and burn it on a DVD or put it on a flash drive with the instructions on the webpage and boot to it. Once it's loaded up run the "Recommended" option and then let it do it's thing. At the end, it will give you a Bootinfo Summary link as well, please post that too for the experts to read. The Boot-Repair Rescue disc is kind of my go-to tool when I get errors so you may want to try that if the UEFI mode is already enabled. So hopefully it should fix that issue you are having.

Can you link me to the Boot-Repair rescue disc download? Sorry, I don't know exactly what to look for. All the help you can give is very much appreciated :)

---

### Post by ajdlc47 on 2014-01-29
Your welcome, I am glad that I can help. I know Ubuntu can be a little intmidating at times so I definitely understand how you feel. Here is the link: [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by fantab on 2014-01-29
You probably don't need Boot-Repair at this stage.
Read this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
and follow instructions. If you get stuck anywhere we'll be glad to help.

---

