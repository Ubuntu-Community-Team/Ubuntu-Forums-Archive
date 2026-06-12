---
title: "[Dual Boot Win10 + Ubuntu 18.04] Freezes During Installation (Except Mouse)"
date: 2019-02-11
forum: Installation &amp; Upgrades
---

### Post by piggiesgosqueal on 2019-02-11
[SOLVED]
For those of you having the same issue, read the following:
What is Wrong & How to Fix: [https://ubuntuforums.org/showthread.php?t=2411970](https://ubuntuforums.org/showthread.php?t=2411970) (Specifically: [https://gyazo.com/5496095d84d1af3e1d431534203ae8f9](https://gyazo.com/5496095d84d1af3e1d431534203ae8f9))
Instructions of how to get to where you need to edit a file: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
What is nomodeset? [https://gyazo.com/7010ca7c224fff1ea7569a40b5210c91](https://gyazo.com/7010ca7c224fff1ea7569a40b5210c91)
How to add nomodeset to file: [https://support.reliablesite.net/kb/a240/how-to-set-nomodeset-into-the-grub-bootloader-debian-and-ubuntu-intel-core-i7-3770.aspx](https://support.reliablesite.net/kb/a240/how-to-set-nomodeset-into-the-grub-bootloader-debian-and-ubuntu-intel-core-i7-3770.aspx)

NOTE: After you successfully install Ubuntu, also install NVIDIA drivers THEN (AND ONLY THEN) be sure to remove the `nomodeset` part so your Ubuntu Graphics don't look weird.
_________________________________________________________________________________________________________________________________________

I have Windows 10 and I'm trying to install Ubuntu Desktop 18.04 as a Dual Boot on my laptop. However, when I get into the installation it will either freeze on the selecting language GUI, Keyboard Language GUI, or Internet GUI. My mouse can move fine but nothing else. When I try to click buttons nothing responds even if I wait a while. So eventually I just turn off laptop.


[LEFT][FONT=arial][COLOR=#000000]Here are my specs:[/COLOR][/FONT]
[/LEFT]

[LIST=|INDENT=1]
[*]Computer: i7-8750H CPU @ 2.20 GHz - 32 GB RAM, 500 GB SSD & 1 TB HDD. I think my laptop has a NVIDIA graphics card & searching Geforce makes Geforce experience show up, but when I checked Task Manager it said Intel(R) UHD Graphics 630. So.. Idk.. 
[*]Windows 10 Home 64-bit, 1803 version 
[*]Bios: Asus Republic of Gamers (R.O.G.) BIOS v306 (Not 100% sure if it's just called that or if there's more..) 
[*]Ubuntu Version: ubuntu-18.04.1-desktop-amd64 (ISO file, bootable USB thumb drive with 32 GB of space) 
[/LIST]


- I can successfully boot to see the list of "Try Ubuntu" and "Install Ubuntu". I've tried both to install Ubuntu and they both got stuck. When I did "Try Ubuntu" it would get stuck before loading the Install Ubuntu program button.
- I disabled Windows Sleep after 10min option, so it will never sleep. Then plugged in charger for laptop and did the Rufus part below.
- I used Rufus on my laptop to install the ISO file and checked for bad blocks 1 time. I've reinstalled it multiple times on the USB drive, thinking maybe it didn't work the first time or something. The most recent time I used my desktop instead (to see if it changed anything) & did check for bad blocks again.
- Just before the Ubuntu Loading Screen with the ~5 dots centered in the middle of the screen, there are 2 black terminals or screens? that open very quickly and close very quickly so I can't read anything from them.

[LEFT][FONT=arial][COLOR=#000000]My Installation:[/COLOR][/FONT]
[/LEFT]

[LIST=1|INDENT=1]
[*]Created 70,000 MB (~70GB) 'free space' partition on SSD drive (main drive that Windows is also on). 
[*]Used Rufus to mount Ubuntu 18.04 .iso onto removable 32GB USB-stick 
[*]Did Advanced Startup, then clicked USB drive to run Ubuntu. (Have also just turned off laptop completely and turned it on to start directly in Ubuntu (because boot order is set to USB stick first.) 
[*]Have clicked "Try Ubuntu" and "Install Ubuntu", both froze (aside from mouse). 
[*]I tried clicking alt + f2 to open command prompt like I read online to do, it didn't do anything. 
[/LIST]

Any help would be greatly appreciated. Please keep in mind I am totally new to Ubuntu / Linux so please explain things in an easy to understand way. :P

[COLOR=#000000]
[/COLOR]

---

### Post by oldfred on 2019-02-11
You already show ]Solved], so only those looking for answers may look at thread, not those who may be able to help.

Is your UEFI/BIOS the most current version? Some vendors still use the old "BIOS" even though all systems since Windows 8 in 2012 are newer UEFI based.
If you have an SSD, have you updated firmware also?

Some find one installer or one flash drive just does not work. They try a different one and then it works.
Also did you check  that ISO is correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you have nVidia, you will need nomodeset boot parameter both for live installer & first boot or  until you install nVidia driver from Ubuntu repository.
       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    You may have settings in UEFI on which graphics chip you are using, and it may not just say graphics chip. Check manual on your UEFI from Asus.
 
Many Asus need pci=nomsi in addition to the nomodeset boot parameter.  But you only temporarily need nomodeset, but may always need pci=nomsi. Once installed we can add that to grub configuration file to always include it in grub updates.

    Some older ROG systems, but newer Ubuntu should work better.
      
 ASUS ROG GL552VW-CN104T
[URL="http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters"]http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters
      [/URL]
 Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167) 
            How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221) 
    [URL="http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters"]
[/URL]

---

