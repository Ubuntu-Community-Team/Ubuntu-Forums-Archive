---
title: "Could not find kernel image: Install"
date: 2015-05-17
forum: Installation &amp; Upgrades
---

### Post by kkk3 on 2015-05-17
Dear all,

I am new to linux and i am trying to install ubuntu 14.04.2 x64 on my old AMD Athlon 64 machine using noapic configuration.

When i press Enter on boot: install vga=915 noapic nolapic , I get the massage "Could not find kernel image: Install". I saw most of the other people having similar problem got "Could not find kernel image: Linux"- not Install. 

Can someone help with that? What is the reason for this message?  

I am using Universal-USB_Installer_1.9.6.0. Moreover i made a folder "syslinux"(having syslinux.cfg) identical with "isolinux"(having isolinux.cfg). 
I noticed also that removing the folder isolinux doesn't give any positive result since the start menu doesn't show up=> errors and reboot.

Thank you for the help!

---

### Post by ubfan1 on 2015-05-17
I am not familiar with the Universal-USB_installer, but have used Unetbootin from Windows in the past with success.  When you get the "boot:" prompt, try just typing return, since there is kernel named "install".  Try the kernel named "vmlinuz" if you really neeed the noapic nolapic business.

---

### Post by Bashing-om on 2015-05-17
kkk3; Hello;

My thoughts :
> 
old AMD Athlon 64 machine 

I expect will have Nvidia or ATI for graphics chip set; thus:
> 
vga=915

as an Intel parameter I expect will fail; I can accept that the installer will not find the kernel to support Intel .

Now, my  prior experience with an " old AMD Athlon " machine, ubuntu will not run on it . However (L)ubuntu performed wonderfully (2 Gigs of ram ).

You should not have to fudge with the installer ( folder "syslinux" ) at all . The installer "just works" 

My personal , and it is only personal, preference is to burn that .iso file to a DVD. Then I have a liveDVD on-hand for 'rescue' and my USB thumb drive I can commit to other uses . 

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

