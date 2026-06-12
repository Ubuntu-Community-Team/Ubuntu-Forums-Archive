---
title: "Stuck on &quot;Bad target numbers&quot;"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by AlwaysRemind on 2014-03-03
Hello everyone! I'm trying to install a debian based system (Crunchbang) and I'm thinking about trying Ubuntu but I'm worried I'm going to run into the same issue because of Grub. Here's a quick history on what I had to do:

&#8226; I have Windows 8.1 as my main OS. 
&#8226; I have to switch to Legacy as well as diable Secure Boot + Fast Boot
&#8226; I made a Live bootable thumb drive so I could install it onto another thumb drive
&#8226; I had to install grub to /dev/sdc because it would not work with the MBR

So when I make all of the BIOS changes (Legacy, secure boot off, fast boot off) I select to boot from the thumb drive where it's installed. Grub displays and I select the distro. Then I'm prompted with the following errors (I attached the image). The first image shows the errors I get from booting from the Live USB, and the second image is from the installation (on a thumb drive). Any suggestions?

I was advised to try and disable a memory card reader in my bios, but unfortunately I don't have the option to disable that in my BIOS. My computer uses American Megatrends for bios.

I would greatly appreciate any help. Thank you so much you guys

![ATTACH=CONFIG]250846[/ATTACH][ATTACH=CONFIG]250845[/ATTACH]

---

### Post by oldfred on 2014-03-03
I do not know about Crunchbang, UEFI is still changing a lot and with new computers you need the latest versions. Intel has offered many changes not just to Intel video driver, but kernel & supporting software. And Vendors are also updating UEFI/BIOS as it may need changes also.

Some systems will only install in Legacy/BIOS/CSM mode, but then it is difficult to dual boot. You can only change systems by going into UEFI and choosing which to boot. And some auto switch, others require you to turn on/off legacy or UEFI modes to boot different install.
You then cannot use grub to dual boot as once you start booting in one boot mode you can only boot from grub menu systems in same boot mode.

What system, chip & video chip do you have?

Lots of info (may be too much for new user) in link in my signature. But UEFI is a lot different than BIOS.

---

### Post by AlwaysRemind on 2014-03-03
Thank you so much for responding. Some good news is that I just ditched Crunchbang and went with Ubuntu! I used the Universal USB Installer on one thumb drive, then disabled Secure Boot + Fast Boot, switched to Legacy and was able to get into the Live version of Ubuntu 12.04.4! After that I went ahead and installed the boot and Ubuntu onto the other thumb drive (my 32gig one) and it worked perfectly. 

I'm gonna mark it as solved. Switching to Ubuntu seemed to fix the issue :) Thanks for your fast response!

---

### Post by AlwaysRemind on 2014-03-03
[solved]

---

