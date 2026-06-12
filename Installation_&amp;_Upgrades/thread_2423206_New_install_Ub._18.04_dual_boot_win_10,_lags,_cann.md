---
title: "New install Ub. 18.04 dual boot win 10, lags, cannot login, crashes, boot acts weird"
date: 2019-07-19
forum: Installation &amp; Upgrades
---

### Post by kattemageren on 2019-07-19
Hello,

[B]TL;DR:
New install of ubuntu lags in the login screen, and I cannot login, and the keyboard lags and sometimes doesn't work.[/B]

I have tried installing ubuntu twice today, by freeing up HD space with windows 10, and booting/installing ubuntu from a flashdrive. Booting from flashdrive works very well. Plays youtubevideos, finds all my monitors and sound outputs. Installation proces goes smoothly as well. I found some guides on youtube and followed them thusly: Partitions: 20gb root "/" ext4, 8gb swap, 65gb home "/home" ext4. I clicked yes to installing 3rd party proprietary drivers.

When I reboot, the following (of suspicious nature) happens:
Normal boot splash screen (I can press F2 or del access the bios.)
*BEEP* weird splash saying "no keyboard found*
Ubuntu boot loads with four options - but my keyboard doesn't respond, so I wait for three seconds and it chooses to boot ubuntu for me.
Login screen loads on my tv, ubuntu background on my monitor - there's no fade in of the login screen, it just appears.
When I click on my user, it jerks the input open. The mouse lags, the keyboard lags (and sometimes doesn't work). I enter my password - it doesn't login. I try again. Still no....

I have tried the following: 
Boot > F2 > advanced boot > ubuntu boot > ubuntu: Same result - although my keyboard works in the boot option menu.
Boot > F2 > advanced boot > ubuntu boot > system system > instant shut down of computer.
Boot > F2 > advanced boot > ubuntu boot > Advanced options for ubuntu > Safe-mode > Repair GNU: "Yess, no lag - better reboot to see if it works": Same problems on reboot again.

Specs:
x64-based PC
Processor: Intel Core i7-8700K CPU @ 3.70GHz, 3696 Mhz, 6 core, 12 Logic processors
BIOS: American Megatrends Inc. 0802, 01-11-2017 
SMBIOS-version 3.0 - UEFI - ASUSTeK COMPUTER INC. 
Ram 16gb 
NVIDIA GeForce GTX 1070 Ti 
High Definition Audio-controller
500gb SSD harddrive
Microsoft Windows 10 Home
Secure boot off 
2 monitors on: 1 though Display, and one through HDMI -> reciever -> tv screen

---

### Post by oldfred on 2019-07-19
Have you updated UEFI?

Are you using nomodeset boot parameter, or did nVidia proprietary driver get installed?
 New versions of Ubuntu will now install a nVidia driver if you check the install proprietary drivers. It used to just install codecs, but not drivers.

Does system work ok when using live installer in live mode?

---

### Post by kattemageren on 2019-07-19
Thank you for replying!

I have done nothing except try to install ubuntu. I don't know whether that is supposed to happen automatically. How do I update my UEFI, and why is it necessary?
I also don't know what nomodeset boot parameters mean. During installation I checked the box, that was supposed to install third party drivers and software. I don't know whether that means, it installed nVidia nor whether it works. Is there any way to check that?
I don't know what live installer in live mode means. I restarted the computer - booted ubuntu from the flash drive - it runs, I can use firefox, see youtube etc. I then ran the installer during that boot from the icon on the desktop of ubuntu :"Install 18.04...".

As you can probably tell, I'm not the brightest bulb in Aladdins lamp, so pixiebook level explanations are very much appreciated. And thank you again very much for replying!

---

### Post by oldfred on 2019-07-19
The live installer has two modes, one where it works and one where it installs. If it worked then that is good.

Usually you even had to use nomodeset to boot live installer. And then on first boot or until you installed the nvidia driver into your install. 

You can try nomodeset boot parameter at grub menu. But should not be required once nVidia driver installed. If you do not get grub menu, you can press escape key right after UEFI system screen. If UEFI fast boot setting is on, then you may not have time to press any key.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
       Spectre virus
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.  
Both Windows & Linux have updated kernels, but they keep finding new versions, so regular updates may be required.

---

