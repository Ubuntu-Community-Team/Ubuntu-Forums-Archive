---
title: "UEFI boot troubles, boot-repair only mildly successful"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by beau-thehenderson on 2013-08-27
Boot-Repair output: [http://paste.ubuntu.com/6034878/](http://paste.ubuntu.com/6034878/)

I've installed 13.04 alongside windows 8 with Legacy mode enabled and secure boot disabled in the BIOS, fastboot enabled in windows as well.

The system continued to boot directly to windows ( no sign of grub ) post initial install of Ubuntu.

I booted to liveUSB and ran boot-repair with default options. The machine still continues to boot directly to windows with the HP boot screen -> Windows 8. I am able to get to Ubuntu by loading the boot menu when starting up and then selecting the Ubuntu option from there. I am then directed to the Grub menu which does have Ubuntu set and configured as default. Once I select Ubuntu it only boots 50% of the time and I was initially fooled by the screen brightness defaulting to extremely dark ( thought it was black screening ) every time it boots.

The laptop is a HP Envy 15-j028TX Notebook

Any advice would be appreciated!

---

### Post by oldfred on 2013-08-27
Other Envy threads.

 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
      
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

    
From above thread it seems your HP only has two boot modes, UEFI with secure boot and CSM which may boot from efi or CSM mode. But does Windows boot with secure boot off? Some systems do not.

If you have to have secure boot on, you have to install Ubuntu with secure boot on, or use Boot-Repair with secure boot on and update Ubuntu with Microsoft signed grub shim file & signed kernels.

      
 One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

HP also has a lot of efi files in the efi partition. Boot-Repair adds boot entries for all of them. You may or may not need those entries, but some info on housecleaning them out is in the thread in my signature.

---

### Post by beau-thehenderson on 2013-08-28
Hi Oldfred,

Thanks for the information!

I've re-enabled secureboot and compatibility mode ( which I suspect is what you mean by CSM ? ), booted into windows8 ( which does work fine with secureboot disabled and also fine when compatibility mode is enabled ).

With the above in mind, I have just now for the 5th time in a row attempted to boot into the LiveUSB by first loading windows -> PC Settings -> General -> Reboot into USB -> USB w/ UEFI.

I am presented with standard Grub menu options to Try or Install Ubuntu. I have attempted to fire up both options 5 times in a row using the above exhausting method with similar results. The boot process begins, I brighten the screen and hit the down arrow key to get command line output of what's going on. It stalls each and every time and never at any particular stage in the boot up process. I'm not seeing it kernel panic or anything out of the ordinary. It's just stalled and won't go anywhere. I can't switch terminals and once it gets to this stage the brightness function doesn't do a thing either.

Any further guidance would again be most appreciated!

---

### Post by oldfred on 2013-08-28
If you have nVidia, you need at grub menu to add nomodeset. Sometimes other parameters are also required.
At grub menu:
Press e, for edit and scroll down to linux line, replace quiet splash with nomodeset. Without quiet splash it will also post booting process and you can see where it stops. Usually not the last posted but a few above it.

First examples are BIOS boot, then the examples for booting with grub after install are the same as UEFI grub boot.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

It looks like one of the above threads was only able to install Ubuntu in CSM/BIOS/Legacy mode. Then use Boot-Repair to convert to UEFI.
I would update UEFI/BIOS to latest version from vendor also. Vendors are also finding issues and fixing them.

---

### Post by beau-thehenderson on 2013-08-29
> **oldfred said:**
> If you have nVidia, you need at grub menu to add nomodeset. Sometimes other parameters are also required.
At grub menu:
Press e, for edit and scroll down to linux line, replace quiet splash with nomodeset. Without quiet splash it will also post booting process and you can see where it stops. Usually not the last posted but a few above it.

First examples are BIOS boot, then the examples for booting with grub after install are the same as UEFI grub boot.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


It's a Dual GPU with both Intel (onboard) and the Nvidia. I've found that when I have got it to boot via previous means to Ubuntu the Intel is configured whilst the the Nvidia is left unconfigured ( which I know can be addressed with bumblebee ). With that said, nomodeset doesn't help, I get the same result. I've reviewed the other available options and can't seem to find any that might be of any use unfortunately.


> **oldfred said:**
> 
It looks like one of the above threads was only able to install Ubuntu in CSM/BIOS/Legacy mode. Then use Boot-Repair to convert to UEFI.
I would update UEFI/BIOS to latest version from vendor also. Vendors are also finding issues and fixing them.

This is how I had it installed previously whereby I would need to manually enter into the startup menu ( Pressing Esc. at boot up ) and manually select the Ubuntu install. Whilst this is a solution, it's really really annoying having to do this, but I'm beginning to think I'm going to have to live with it.

Thanks again!

---

### Post by oldfred on 2013-08-30
Often the last 5 or ten commands posted when booting without splash quiet give some clue to boot parameters as it may mention device with issue.

Can you use camera, shrink to screenshot size and upload? You can use the Advanced Editor and just click on the paperclip icon to add a file. Size limits do restrict what you can upload.

---

### Post by beau-thehenderson on 2013-08-30
Yeah, the unfortunate thing is, nothing in the output is suspicious, just standard startup procedure. I'm very well versed in that department as I'm a systems admin by trade. Absolutely nothing out of the ordinary, it just freezes at random points in the bootup process and I have to hard power it off.

---

