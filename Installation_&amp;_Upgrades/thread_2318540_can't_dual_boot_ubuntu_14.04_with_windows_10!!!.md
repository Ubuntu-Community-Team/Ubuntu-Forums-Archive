---
title: "can't dual boot ubuntu 14.04 with windows 10!!!"
date: 2016-03-27
forum: Installation &amp; Upgrades
---

### Post by steven60 on 2016-03-27
ok so i'm trying to dual boot windows 10 and ubuntu 14.04.
the computer is a hp pavilion g7
the computer will not boot from usb in uefi mode (believe me i've tried) so i've switched bios to legacy mode...
booted from usb just fine. installed just fine. but i cannot boot into ubuntu...
things ive tried...
boot-repair
efibootmngr

both give me errors that i must be in uefi mode to use them.
but i cannot boot the live usb with out being in legacy mode.
please help me.:confused::confused:

---

### Post by Bucky Ball on 2016-03-27
Well, you have one installed in UEFI and the other in BIOS. No, its not going to work. I think Boot Repair has an option to change it to all EFI, but there are others who are more au fait with that.

Did you boot into Windows and switch off hibernation before you tried installing in UEFI? The computer must be completely shutdown first otherwise Windows remains mounted and you can't access the drive. Just a thought.

---

### Post by revolutionkiteman on 2016-03-27
ok, new here but it seems you had similar probs to me, check out my thread as its all fine now.
1. shrink your volume on windows, if you have unbuntu installed i would suggest deleting it and starting again.
2. i found the best way was to download your iso then extract with 7zip to your usb, then check with disk management if its an active partition, i bet its not and its grey out, use the console to change it
3. set fast boot to off in power options
4. leave secure boot on and legac off in your bios, but move up the boot order so usb is top, and after installing ubuntu put the unbuntu package to the top in the os boot menu(also in the bios settings)
see how you go then :)

---

### Post by oldfred on 2016-03-27
Couple of choices. Use UEFI as boot manager and ignore grub.
If Windows is UEFI and Ubuntu BIOS/CSM/Legacy then you can only choose which system to boot from UEFI boot menu or one time boot key.
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

Or you can use Boot-Repair to convert Ubuntu install to UEFI using advanced options. It uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI).
But HP has not been UEFI dual boot friendly. The violate UEFI spec that says not to use description as part of UEFI boot. And of  course only description is "Windows Boot Manager". But we have many work arounds depending on configuration.

      
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

