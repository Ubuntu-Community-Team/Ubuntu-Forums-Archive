---
title: "Booting with Ubuntu stuck at Black Screen after HP Laptop BIOS Upgrade"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by AJITESH_MADAI on 2016-04-03
I have dual boot setup of Windows 8.1 & UbuntuGnome 15.10 on my HP ENVY Laptop (15-u110dx)

I upgraded the BIOS to the latest firmware from Windows 8.1.

After successful BIOS upgrade, I am able to boot into Windows, 
but on selecting the "Ubuntu" option from the Grub menu I am presented with only a blank screen.:(

Please help me to resolve this boot issue.

Regards,
Ajitesh

---

### Post by oldfred on 2016-04-03
An UEFI/BIOS update reset all the settings you changed in UEFI to make Ubuntu work.
With my old BIOS system I had to use a camera to remember all the screens.
New UEFI system lets you take screenshots and save them, so I know my standard settings.

It probably turned on UEFI secure boot. Not sure what else you may have changed. USB settingsBoot order settings. Probably with HP you have to use the fallback or hard drive boot entry as HP violates UEFI spec that says not to use description. And only valid description is "Windows Boot Manager".  Did you add fallback before, the /EFI/Boot/bootx64.efi?

---

### Post by AJITESH_MADAI on 2016-04-05
@oldfred, I tried the following but still no luck. the blank screen is still displayed (no cursor, no nothing) after selecting Ubuntu from grub menu.

1) Edited "Ubuntu" entry with 'nomodeset' :(
2) Disabled "Secured Boot" in BIOS :(
3) Enabled "Legacy mode"(Bios says this is CSM mode for older operating systems) in BIOS :(
4) Booted from Ubuntu USB disk in UEFI mode with 'nomodeset' :(
5) Booted from Ubuntu USB in Legacy mode -> can see a cursor at top blinking, no progress :(

Finally out of frustration, I have roll backed by BIOS image to previous version, thankfully my BIOS allows me to do this very easily..Its fixed for now :D  

I would be very glad to know what was the issue, and how can I fix it...

Thanks

---

### Post by oldfred on 2016-04-05
If something in HP's UEFI, only someone with your model & version of UEFI may know.

Some other HP, do not know if somewhere in comments is something helpful or not.
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 
      
 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)

---

