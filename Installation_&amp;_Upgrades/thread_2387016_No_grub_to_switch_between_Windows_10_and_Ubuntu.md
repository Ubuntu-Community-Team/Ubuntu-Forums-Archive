---
title: "No grub to switch between Windows 10 and Ubuntu"
date: 2018-03-13
forum: Installation &amp; Upgrades
---

### Post by jswilson on 2018-03-13
So I just installed Ubuntu LTS alongside my windows 10 on a HP Pavilion x360 m3. The installation went perfect and after it was done it said to reboot to take effect, after the reboot it went directly into my windows 10 with no option to switch between the two OS's. I made sure to switch my UEFI order from having USB at top to the OS Boot Manager being at top and that had no effect. After that I tried disabling Secure boot as well but that didnt seem to fix it either. I then opened Ubuntu just off of my USB and ran Boot-repair, and it gave me this error [http://paste.ubuntu.com/p/MhmY6DDgC6/](http://paste.ubuntu.com/p/MhmY6DDgC6/). I also wanted to note, that before disabling secure boot I was actually able to reach my ubuntu partition through a weird path. I would have to log into my windows > go to Change Advanced startup > then click Restart now >  select Use a  device  > Ubuntu. For some reason this would bring  me to grub even though  my install USB wasnt't even plugged in. Does anyone know how to fix this or is my best bet just to delete my ubuntu partition and retry setting it up? Im by no means an advanced user so I might have just made an error in the installation, but it definitely seemed to go smooth. Thank you for any help!

Edit: Just checking now I am still able to get to my Ubuntu through the method listed above, but now when I get to where I press Ubuntu, there are two options of Ubuntu.

---

### Post by oldfred on 2018-03-13
You have an HP.
HP is not particularly UEFI dual boot friendly.
Can you boot from Escape f8 or f9 whatever is correct for your system?
Some live with that work around.
But since you ran Boot-Repair, it copied shimx64.efi (grub's boot loader) to /EFI/Boot/bootx64.efi. That is a hard drive or fallback boot entry.
Can you boot your hard drive entry?
And it may let you set that hard drive entry as first in boot order, but will not let you set "ubuntu" entry as first.
HP violates UEFI spec that says not to use description as part of boot. And only valid description is "Windows Boot Manager". But fallback/hard drive may work also.

Other work arounds are in link in my signature. Many manually copied shimx64.efi, but now Boot-Repair does that automatically.

       Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[URL="http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789"]http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789

[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 


[URL="http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789"]
[/URL]

---

