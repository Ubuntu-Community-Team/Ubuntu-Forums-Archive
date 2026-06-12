---
title: "I want to install ubuntu-xenial on Acer Aspire with Win10 and secureboot"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by ventrical on 2016-09-19
Hi All,

  I have yet another potential ubuntu convert but the client wants to have dual boot.  Client wants ubuntu installed alongside an already existing Windows 10 upgrade from Windows 7 that has secureboot (standard) set in BIOS.  I had read that Ubuntu will not successfully installl on a  PC (Acer Aspire E1-572P-6616). That has secureboot  on in the BIOS. Is this correct? If not is there any few step solution to try and install a successful side by side install on this PC/

Thanks

---

### Post by oldfred on 2016-09-19
Windows 7 will not work with Secure boot on.
You can install Windows 7 in UEFI mode, but only from a modified flash drive that moves the .efi files to correct location for UEFI boot of installer.

BIOS is not Secure Boot, only UEFI. If upgrade from standard Windows 7, it almost always will be BIOS with MBR partitioning. Windows only boots with UEFI from gpt partitioned drives.

Acer needs trust settings:
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

Some older threads mention that UEFI must be downgrades, but newer threads says newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[URL="http://ubuntuforums.org/showthread.php?t=2291335"]http://ubuntuforums.org/showthread.php?t=2291335
[/URL]
 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/) 
      
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body) [ ]("http://ubuntuforums.org/showthread.php?t=2291335")       [ ]("http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757")

---

### Post by #&amp;thj^% on 2016-09-19
Hey Vent depending on bios from  Acer Aspire E1-572P-6616
See if this helps: [http://askubuntu.com/questions/813232/stuck-while-installing-ubuntu-along-side-windows-10](http://askubuntu.com/questions/813232/stuck-while-installing-ubuntu-along-side-windows-10)
And the Wiki : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
oldfred usually watch's these threads with a keen eye.
And speaking of oldfred here he is now..ninje'd

---

### Post by ventrical on 2016-09-19
@oldfred

I don't understand this language here..

> 
not sure turn off windows fast start-up necessary
for sure not necessary disable Secure Boot in bios in my case <a lot of advice stress the importance of this


for sure not necessary disable> so that means it doesn't matter if secure boot is on or off?

regards..
rdit:

ah . ok.. I think I got it .. :) .. long day.. :)

---

### Post by ventrical on 2016-09-19
> **1fallen said:**
> Hey Vent depending on bios from  Acer Aspire E1-572P-6616
See if this helps: [http://askubuntu.com/questions/813232/stuck-while-installing-ubuntu-along-side-windows-10](http://askubuntu.com/questions/813232/stuck-while-installing-ubuntu-along-side-windows-10)
And the Wiki : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
oldfred usually watch's these threads with a keen eye.
And speaking of oldfred here he is now..ninje'd

thanks lfallen. The PC belongs to a business - used for both personal and business and they need all Windows crappity's working if you get my meaning. The install is 'alright' by Windows standards but it has developed the inherent Windows 'spinner-ware' when starting and shutting down (slow performance). I am trying to approach this install from a perspective (since Canonical and Microsoft are now partners of sorts) that perhaps I may be able to actually fix Windows 10 without  reverse engineering it plus be able to  share the fantastically best operating system on the planet with individuals who have very large footprints in this part of North America. My trepedation is that I might break the bootloader ... but I am determined to give all of this a try.. I know it works in BIOS mode but these little tweakity Acers  can be tough nuts to crack :)

heheheh ..

Regards..

---

### Post by oldfred on 2016-09-19
If you really want Secure Boot, then you need to have it on when you install. With new UEFI systems there are three versions of grub & kernels. UEFI with Secure Boot, UEFI and BIOS. 
Only the Secure boot version uses the signed kernels and needs grub's shim. And grub-efi-am64 is for UEFI boot and grub-pc is for BIOS boot.

Many systems with Secure boot on, then require extra settings to allow USB boot as that is not secure. There may be some other settings also under the Supervisory password. Those settings do not show until password set in UEFI. Do not have an Acer so do not know details other than posts above.
But Secure Boot is primarily marketing by Microsoft. A company that has had for years headlines saying a new virus has attacked it, now has Secure Boot. Just that secure boot is not related to 99% of the virus' attacts. And the only major Boot virus attack was actually released by Sony to add DRM to all systems so Sony Music could not be played unless purchased.
In the future we may need Secure boot, but for now I do not use it.
       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 
    
You do need to have Windows fast start up off, as that is hibernation which prevents the Linux NTFS driver from mounting & seeing any NTFS partition on system. Then Ubuntu install may erase system if install forced. Also best to have UEFI fast boot off, that assumes no changes to system and on warm reboot it assumes system has not changed. Until all changes are final best to have that off. My system allows a 3 sec delay, which I use after all changes, just so later I still have time to press a key to get into UEFI. Otherwise I have to totally power down & cold boot just to change UEFI or even boot flash drive.

---

### Post by ventrical on 2016-09-19
> **oldfred said:**
> 
    
You do need to have Windows fast start up off, as that is hibernation which prevents the Linux NTFS driver from mounting & seeing any NTFS partition on system. Then Ubuntu install may erase system if install forced. Also best to have UEFI fast boot off, that assumes no changes to system and on warm reboot it assumes system has not changed. Until all changes are final best to have that off. My system allows a 3 sec delay, which I use after all changes, just so later I still have time to press a key to get into UEFI. Otherwise I have to totally power down & cold boot just to change UEFI or even boot flash drive.

Yes.. this is where I want to start. I will investigate  further an get back. 

Regards..

---

### Post by ventrical on 2016-09-19
BIOS mode -- UEFI
Secure Boot   ON
Super PSWD - Clear

so .. yes I would have to create super pswd to disable those.. it also has the F12 bootloader start up option.  I wonder if I can just make a persistent drive and let the client boot from there.

---

