---
title: "Ubuntu 18.04 Installation Crashes"
date: 2018-06-18
forum: Installation &amp; Upgrades
---

### Post by jsc39 on 2018-06-18
I have been trying to install Ubuntu 18.04 on my Acer Nitro 5 (an515-51) [Dual - booting with Windows]. As soon as I boot from a bootable USB it takes me to the installation page and after some time around the Wifi Detection Page the keyboard and touchpad stop working. I have the same problem of touchpad and keyboard not working on OpenSuse TumbleWeed Installation as well as Anarchy Installation.
I tried changing the touchpad settings from advanced to basic still the touchpad doesnt work.
Any help appreciated..

---

### Post by oldfred on 2018-06-18
Since it has nVidia, are you using nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Once installed all Acer have needed "Trust" and updates to UEFI.
Have you updated UEFI from Acer? May also help on your other issues.
       
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
           
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by jsc39 on 2018-06-18
Thanks for the help. I was able to install Ubuntu but the brightness control was not working. I tried installing Nvidia Drivers using the command
[COLOR=#2F4F4F][FONT=monospace]
[/FONT][/COLOR][COLOR=#666666][FONT=Lato][LEFT][COLOR=darkslategray][FONT=monospace]sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
[COLOR=#666666][FONT=Lato][LEFT][COLOR=darkslategray][FONT=monospace]sudo apt-get install nvidia-390
[/FONT][/COLOR]
[/LEFT]
[/FONT][/COLOR]
Then I rebooted the system but the boot got stuck 
[https://imgur.com/AjV7q6T](https://imgur.com/AjV7q6T)
Screenshot is attached[/FONT][/COLOR]


[/LEFT]
[/FONT][/COLOR]

---

### Post by oldfred on 2018-06-18
That is not showing any errors?
Have you tried recovery mode from grub menu?

---

### Post by jsc39 on 2018-06-18
The above mentioned screen is where the boot stops.
What should I do in the Recovery Mode??

---

### Post by oldfred on 2018-06-18
Does recovery mode boot?
If so it gives a menu with options to try to resolve issues using command line or just continuing boot from there.

---

### Post by jsc39 on 2018-06-19
Thanks was able to boot into recovery and uninstall those drivers.
Brightness control is not working. 
Can you guide me here

---

### Post by oldfred on 2018-06-19
Google found multiple but old threads which may not now apply.

[COLOR=#000000]
[https://ubuntuforums.org/showthread.php?t=1962255](https://ubuntuforums.org/showthread.php?t=1962255)
[https://wiki.archlinux.org/index.php/backlight](https://wiki.archlinux.org/index.php/backlight)

[https://askubuntu.com/questions/180819/how-to-control-brightness-on-acer-laptop](https://askubuntu.com/questions/180819/how-to-control-brightness-on-acer-laptop)
[/COLOR]

---

### Post by jsc39 on 2018-06-19
[https://postimg.cc/gallery/2tuakuhg8/](https://postimg.cc/gallery/2tuakuhg8/)

Here is some information

---

### Post by oldfred on 2018-06-19
Once you install the proprietary nVidia driver from Ubuntu repository, you do not use nomodeset.
Normally you then do not add nomodeset to /etc/default/grub, but just manually when booting as only needed on first boot. It may prevent nVidia driver from working correctly.

       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946) 
            [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen 
    
You can easily attach screen shots with Forum's advanced editor and the paperclip icon.
But if text or terminal output better to just copy & paste and if longer include in code tags, using # icon.

---

### Post by jsc39 on 2018-06-19
Thanks for all the help.
Was able to install Drivers and brightness settings were restored.

---

### Post by oldfred on 2018-06-19
Glad you got it working. :)

---

