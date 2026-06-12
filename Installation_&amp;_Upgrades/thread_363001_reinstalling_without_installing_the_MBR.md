---
title: "reinstalling without installing the MBR"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by theophane.weber on 2007-02-16
Hi,

I have Ubuntu installed in parallel with two versions of windows. The MBR boots on Windows vista, which then uses information that I had saved from GRUB (I installed Ubuntu first) to allow to choose which OS to boot from. In a way, I have a GRUB like menu at boot which allows me to choose between Ubuntu and Windows. I'd like to reinstall Ubuntu (in particular i'd like to check if i will have less problems with kubuntu than with ubuntu), but I want to make sure it doesn't overwrite the MBR. Is there a way to tell Ubuntu: don't worry about booting, someone is taking care of it. Now, if I manage to do that, will previous GRUB boot information be still "accurate" to boot on the Ubuntu partition? Is is true if I reinstall the exact same Ubuntu? Kubuntu?

thanks for your help~
-theo

---

### Post by Dr. Nick on 2007-02-16
If you use the alternate install **(not live cd desktop install) **then you can tell it at the end to not set up a boot loader if I recall, If you use the same version or kubuntu as you have ubuntu and install to the same partition then info might be correct. I am not sure how your boot loader works, but grub is picky (rightfully so) about specific kernel versions, if the kernel is the exact same version it may be accurate.

---

### Post by theophane.weber on 2007-02-16
thanks! That's very helpful. So that means that if I update my kernel now, it won't work anymore? Actually, maybe I was a little inaccurate in my description; what I did was the following : I saved some information from Grub (by doing :
    sudo dd if=/dev/hda of=/media/share/ubuntu.bin bs=512 count=1), then installed windows, and gave the grub info to windows (in the form of a .bin). Now if I choose Ubuntu in the vista boot loader, it goes to the ubuntu partition, loads grub (but it goes away fast b/c grub thinks there is only one OS), and goes to ubuntu.
So in a sense, grub is still here, and well alive; what was erased (i am not an expert in "boot theory", so this is a guess) is the information of which parition to boot from at the very beginning: i assume this is what is called the master boot record.

Thanks for your help, really--
-theo

---

### Post by Dr. Nick on 2007-02-16
Ok, that explanation makes it a little easier, i'm not boot theorist either lol, so this is only what i think should happen with no guarantee.

This is one way I understand it, The vista bootloader is only launching grub, and grub inturn launches linux. 

If thats the case and you reformat your current ubutnu partition then grub will disappear and you should be left with the vista loader. but it appears that you could have also used something like this to set it up
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why#Fooling_Windows]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_%28NTLDR%29_and_why#Fooling_Windows")


If that is the case then I think you may be alright as long as the partition numbers stay the same.

With the alternate cd you have the option to install grub to the mbr, install it to the /root partition or not install it at all.

I am not exactly sure how your setup works, but if all the files to boot linux reside on the windows partition I would skip the grub install, if grub is needed  in some way then just install it to the root partition instead of mbr.

---

