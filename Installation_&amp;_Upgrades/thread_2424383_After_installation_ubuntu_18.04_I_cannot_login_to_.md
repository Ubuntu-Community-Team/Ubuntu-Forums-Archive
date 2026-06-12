---
title: "After installation ubuntu 18.04 I cannot login to my desktop successfully"
date: 2019-08-07
forum: Installation &amp; Upgrades
---

### Post by coffee-milk on 2019-08-07
Hi there
After installation procces I cannot login to my desktop right it's something like LOGIN LOOP and the whole operating system working wronge not the right way , NOTE I have windows 10 in the same hard drive too .

Thank you 

My hardwar 
Nvidia RTX 2070
MSI Z370 pro

---

### Post by oldfred on 2019-08-07
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But it may just be that you need nomodeset boot parameter to boot or MSI needs additional boot parameters also. After you boot you will need to install nVidia driver from Ubuntu repository or ppa (to get very newest driver), not from nVidia directly.

Do you get grub menu? If so can you boot using recovery mode?
Many new systems even though new need UEFI update.
And if SSD, you probably need a SSD firmware update.

       
 MSI Tomahawk Z370 GTX 1070 TI [SOLVED] Grub error during install two NVMe drives
[URL="https://ubuntuforums.org/showthread.php?t=2398599"]https://ubuntuforums.org/showthread.php?t=2398599
      [/URL]
 MSI X370 Gaming Plus used rEFInd
[URL="https://ubuntuforums.org/showthread.php?t=2378837"]https://ubuntuforums.org/showthread.php?t=2378837

      [/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    [URL="https://ubuntuforums.org/showthread.php?t=2378837"]
[/URL] 

    [URL="https://ubuntuforums.org/showthread.php?t=2398599"]
[/URL]

---

### Post by coffee-milk on 2019-08-08
Thank you for your help
my problem is not about grub or booting , it's about the operating system it self , I cannot login to ubuntu successfully , every time when I set my username and password it does't work , It's login loop .
sorry for my English

---

### Post by oldfred on 2019-08-08
Have you then tried recovery mode from grub menu?

---

### Post by coffee-milk on 2019-08-09
I've tried now , now I can log in into my desktop without any problem , thanks 
but the screen resolution not good , what that mean ?

---

### Post by oldfred on 2019-08-09
If you booted with recovery mode, that uses the nomodeset boot parameter. That normally is required to boot if you have not installed the nVidia proprietary drivers from Ubuntu  repository or Ubuntu's ppa (not nVidia directly).  And nomodeset sets it to a lower quality video as nVidia has not been good about providing info for the open source nouveau developers.  They just released a lot of new info, but it will be quite a while before that is in any default open source driver.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
    
       nVidia install, purge older driver, if needed.
[URL="https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336"]https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336
      [/URL]
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
With 18.04, the only way I can get to this now is with Software Updater & Settings.
ubuntu-drivers devices 
    [URL="https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336"]
[/URL]

---

### Post by coffee-milk on 2019-08-12
okay , thank you very much

---

