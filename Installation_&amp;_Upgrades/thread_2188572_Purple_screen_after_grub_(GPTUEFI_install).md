---
title: "Purple screen after grub (GPT/UEFI install)"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by jhoanegar on 2013-11-17
Hi! I'm posting here as a last resource since I can't figure out what's wrong with my ubuntu.
I hava a new laptop toshiba satellite and since day one I tried to install ubuntu 12.04 LTS to dual boot with windows 8 x64. I disabled secure and fast boot and tried to install in a new partition as usual but the first time I installed the bootloader in sda/ and everything went wrong. Boot-repair made things worse since it leaved me with a black screen with no grub and no way to boot ubuntu nor windows 8.
Today, I tried a different approach, I installed the bootloader in the EFI partition as suggested in many threads and surprise!! I couldn't boot again so I tried boot-repair and it fixed the grub and Windows will boot normally but if I try to boot into ubuntu (even in recovery mode) I get a purple screen with no errors (even with --verbose option in grub). 
I think I've done the hard thing (leaving windows intact) but it's so frustrating not being able to start ubuntu... Anyway, I hope you have some ideas of what should I do.
It is worth mentioning that when installing I had no problems whatsoever with hardware.
Finally this is my last boot-repair log
[http://paste.ubuntu.com/6435309/](http://paste.ubuntu.com/6435309/)

Thank you for reading.

---

### Post by oldfred on 2013-11-18
What video card/chip do you have?
Often nomodeset works but most new Intel need different boot parameters.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

At grub menu press e, for edit, scroll down to linux line and replace quiet splash with nomodeset.

Some users with Intel have reported one of these work instead of nomodeset, but it may vary by chip??
      
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by jhoanegar on 2013-11-18
Replacing quiet splash for nomodeset did the trick and now I see the problem. Apparently I forgot to check the "install restricted extras" option during the installation and now I have no video nor network drivers. The first time I installed ubuntu I checked that option and everything worked fine, is there a way to install the drivers from the live cd to my system?

EDIT: I solved the problem after a couple of hours. For future reference this is what happended and how I solved it.

My problem had nothing to do with the installation, the problem was that I didn't had an internet connection at the moment of the installation so ubuntu couldn't activate the drivers needed for my graphics card so here is a summary of everything I did.
  - Install the boot loader of Ubuntu in the EFI partition of windows (without formatting).
  - If after installing you can boot ubuntu but not windows use boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
  - That should leave you with a complete dual boot, but, if you have the same problem as me:
    - In grub select your ubuntu installation and type 'e', search your linux line and delete everything after quiet splash and replace it for nomodeset.
    - Now login and connect to a wired network like this [http://askubuntu.com/questions/174603/how-to-connect-to-wired-connection-from-the-terminal](http://askubuntu.com/questions/174603/how-to-connect-to-wired-connection-from-the-terminal)
    - Now type jockey-text -l
    - You should see the name of the missing driver, type: sudo jockey-text -e <name of the driver>
    - Reboot your system with: sudo reboot.
    - Everything should be working fine.
But all this wouldn't be possible without oldfred's help who pointed me to the right direction. Thank you man!
Cheers.

---

### Post by oldfred on 2013-11-18
Glad you got it working. :)

---

