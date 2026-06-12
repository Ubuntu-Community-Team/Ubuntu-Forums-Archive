---
title: "Triple-boot problem after installing Lubuntu 20.04"
date: 2020-06-06
forum: Installation &amp; Upgrades
---

### Post by jet-bundle on 2020-06-06
A few years ago, I installed Lubuntu 16.04 as a dual-boot with Windows 8.1 on an old HP Pavilion dm1 laptop. I had a few problems, and ran boot-repair with the "Recommended" option. This resulted in a system which booted straight into Windows, so I fixed this by interrupting the start-up sequence to boot into Lubuntu, and entering:
```

[LIST=1]
[*]
[LIST=1]
[*]          [COLOR=#ff3333]cd /boot/efi/EFI/Microsoft/Boot[/COLOR] 
[*]          [COLOR=#ff3333]cp -i bootmgfw.efi bkpbootmgfw.efi[/COLOR] 
[*]          [COLOR=#ff3333]cd /boot/efi/EFI/ubuntu[/COLOR] 
[*]          [COLOR=#ff3333]cp -i grubx64.efi         /boot/efi/EFI/Microsoft/Boot[/COLOR] 
[*]          [COLOR=#ff3333]cp -i shimx64.efi         /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi      [y][/COLOR] 
[/LIST]
   
[/LIST]
  
```
I then tidied up the boot menu with Grub Customizer, and all was well. Upgrading 16.04 to 18.04 didn't give any problems.

I've now installed 20.04 alongside the other two OSs, and again needed to run boot-repair; the report is in [http://paste.ubuntu.com/p/znRBrcHK3X/](http://paste.ubuntu.com/p/znRBrcHK3X/). Again, the system boots directly into Windows. This time, though, having entered the same five lines of code as before, the Windows option gives an error:
```
failed to open efi/boot/grub64.efi
```
(I think that's right, it was on screen for just a few seconds as I wrote it down). I can now boot into Windows only by running boot-repair again.

Any advice would be appreciated.

---

### Post by oldfred on 2020-06-06
Years ago it was a work around to rename the Windows UEFI boot file and make it grub or shim.
But then Windows updates overwrite it. And grub only boots working Windows, so it you have issues with Windows it becomes difficult to boot it as the Windows boot file is really grub/shim.

Many with HP, use the fallback or hard drive entry which is /EFI/Boot/bootx64.efi and boot the hard drive entry in UEFI. 
Others have updated UEFI and then they were able to set boot order, but only from within UEFI, not using efibootmgr which grub also uses on install to set grub as first in boot order.

Issues often common across similar models by Brand.
HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP change boot order in UEFI boot
[https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881](https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881)
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)
HP X360 Update UEFI F20
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)

Some with HP also have installed rEFInd. 
I have a couple of old tiny (too small for much else) flash drives with rEFInd for emergency boot.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by jet-bundle on 2020-06-07
Thank you. I'll follow up your suggestions and report back.

---

### Post by jet-bundle on 2020-06-09
I've made good progress, so I'll mark the thread as [SOLVED].

First, a quick summary of the problem. After using boot-repair, the computer would boot straight into Windows. I could get to Grub by pressing Esc within a couple of seconds of power-on, and then pressing F9 and making the selection, but I couldn't make a permanent change to the boot order by pressing F10 instead. I could, though, replace [COLOR=#ff3333]/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi [/COLOR] by [COLOR=#ff3333]shimx64.efi[/COLOR] and then I would reach Grub straight away; the problem then was that the option to boot Windows from Grub then didn't work.

The solution was to use rEFInd.

First, I reverted to the Windows boot arrangement. Then I started Lubuntu by the Esc/F9/Grub route, and installed rEFInd. The computer still booted straight into Windows; but when I restarted Lubuntu I could use [COLOR=#ff3333]mvrefind /boot/efi/EFI/refind /boot/efi/EFI/Microsoft/Boot [/COLOR]and now the computer starts with the rEFInd GUI and I can select Windows, Lubuntu 18.04 or Lubuntu 20.04 as neded. I'll want to do a little more tidying up, and there's the risk that a Windows update will modify the boot order again, but at least I now know how to fix it.

Thanks for the advice.

---

### Post by dragonfly41 on 2020-06-09
[COLOR=#000000]> The solution was to use rEFInd.
+1. I am another rEFInd fan. I have n-boot configuration. Internal drive Win 10 + Ubuntu. External SSD Ubuntu. And other USB drives.
You can also modify the GUI theme of rEFInd.  And tweak settings in refind.conf.

[/COLOR]

---

