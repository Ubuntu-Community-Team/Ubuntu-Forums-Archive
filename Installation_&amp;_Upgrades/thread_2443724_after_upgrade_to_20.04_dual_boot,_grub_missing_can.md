---
title: "after upgrade to 20.04 dual boot, grub missing can't access windows 8.1"
date: 2020-05-19
forum: Installation &amp; Upgrades
---

### Post by amindafreyja on 2020-05-19
I haven't used Ubuntu in about 8 years, so I'm pretty much a newbie again. I hope I am posting this in the correct place. 

I installed Ubuntu 18.0 4 using a bootable usb. Seemed to work fine except for an error that would come up. 

Error stated: An issue has been detected- Cancel/Report Now?  

I reported the issue a couple of times. It never told me what exactly was wrong. 

I decided to upgrade to 20.04. I downloaded the new iso and updated my bootable usb. I used the stick to boot up my laptop to try 20.04. Everything seemed to work fine, so I proceeded to upgrade to 20.04. After the installation was complete, the computer rebooted and went straight into windows 8.1 without showing the grub. 

A friend of mine suggested this, so I used the following link to see if I could fix the issue: [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)
In my windows command prompt I entered the following: bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
The command line showed that the boot manager had been updated.
I restarted the computer and got the following message: System BootOrder not found. Initializing defaults. 
The laptop will now start into Ubuntu, but the grub does not come up and give me the option to boot into windows. 

This is the information that I know about my computer: 
Toshiba Satelite C55-A
Intel core i3
Was originally installed with Windows 8.1 Home and worked fine with 18.04. 

Please let me know what information you need from me to help you help me. 

Thanks

---

