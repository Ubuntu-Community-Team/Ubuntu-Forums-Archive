---
title: "Pre-installation issues."
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by ndDxpGY on 2014-06-18
Hi, I have a Samsung laptop np300e4e with W8 preinstalled (currently W8.1 with all the updates) in UEFI and secure boot.

I had read the official guide(s) plus a lot of other stuff, so for a first try, I disabled the fast boot, then I went directly to the bios (No W8 advanced restart) and disabled the secure boot, when booting from a 64 bits Ubuntu 14.04 (burned in a DVD, and checked also), the first message I get is 

*Could not open* "\*EFI*\*BOOT*\*fallback.efi*": [I]14

[/I]
Then some messages that are so fast to read, and immediately after the grub menu with the options to try, install, oem and check for defects. TRying the system, it worked well,then I restarted the system into W8, Then I reboot into Lubuntu 14, and the same message above appeared, but the system worked, I restarted again and everything was ok.

So, that message made me think something's not right, and I tried the steps to configure UEFI from within W8 (the advanced restart and all that stuff), that just loads the bios with the same configuration it already had, BUT when trying to restart from the DVD from within W8, the screen just went black, and nothing else.

Fearing the worst (The bricked laptop ghost from Samsung), I shut it by force. When restarting, Ubuntu boots the same (including the message of fallback), but when restarting the system, It goes to the part of ""*Please remove installation media* and close the tray (if any) then press Enter.", I did it, close tray and enter, but nothing happened, I have waited some time, and the animation just goes on and on, so I had to shut it down with the power button.

I have tried many times and is always the same, the live disc can't restart or shut down normally. BTW, W8 seems to be ok.

¿Any idea of what's going on? ¿Can I install Ubuntu safely in dual boot?
¿And what about the fallback message? I tried the methods you can find with google to test this and the live disc seems to boot in EFI mode.

---

### Post by grahammechanical on 2014-06-18
> [COLOR=#000000] when trying to restart from the DVD from _within W8_[/COLOR]

Please explain. We do not load the ubuntu/Lubuntu live session from within Windows. Are you trying to install using Wubi.exe? That is not compatible with Windows 8. We do not need to turn off secure boot as Ubuntu/Lubuntu has Linux kernels that meet the Microsoft secure boot requirements.

This
> [COLOR=#000000] ""[/COLOR]*Please remove installation media and close the tray (if any) then press Enter."*

appears when we shut down a live session. Yet you speak of "restarting the system." It confuses me. If pressing Enter does not shut down the machine then use the machine's power button to shut off the machine. That is what I do. 

I test Ubuntu development versions and in the early weeks of development of a new version of Ubuntu the live session will often fail to restart or shut down the machine. It happened to me this morning.

Regards.

---

### Post by ndDxpGY on 2014-06-18
Hi [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")

The advanced restart in windows 8 lets you choose the bootable media to restart the machine.

About the secure boot, I found that enable/disable does not affect the Ubuntu booting. But, the Fallback warning it's still there, that made me try every option.

And the "live" system can't restart, that's what I meant, but it could do it before I tried to restart from within W8. I wonder if this failing to shutdown/restart could extend to the final installation.

UPDATE:

Well, I guessed that crappy W8 did something to the bios so I just flashed it, log in live session and the restart function worked perfectly.

Still, ¿Any comment/experience/advise on this?
```

*Could not open* "\*EFI*\*BOOT*\*fallback.efi*": *14*
```

---

