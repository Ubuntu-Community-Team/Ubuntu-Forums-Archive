---
title: "Installing Ubuntu get blank screen"
date: 2017-03-20
forum: Installation &amp; Upgrades
---

### Post by miquael on 2017-03-20
Installing Ubuntu 16.04 (UEFI mode) on my custom made PC.  When I get to the GRUB whatever I select (try Ubuntu, Install Ubuntu, etc), the system restarts but nothing happens, just a black blank screen.

[FONT=Verdana][COLOR=#131313]I found these instruction in a different post here, but it did not work for me:

[/COLOR][/FONT]```
[COLOR=#000000]Boot the liveUSB;[/COLOR]
[COLOR=#000000]As soon as the EFI splash screen clears spam the escape key to get the boot loader's attention ->[/COLOR]
[COLOR=#000000]Language screen -> escape key to accept the default ->[/COLOR]
[COLOR=#000000]Booting options screen -> F6 key (other options) -> arrow down to the preset option(s); space or enter to accept and then the escape key to exit; [/COLOR]
[COLOR=#000000]Try "nomodeset" at this time;[/COLOR]
[COLOR=#000000]enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.[/COLOR]
[COLOR=#000000]Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.[/COLOR]
[COLOR=#000000]If this works in the liveUSB, we know what to do for the install .

[/COLOR]
```

None of this appear available for me. [FONT=Verdana][COLOR=#131313]Instead, escape key brings me to GRUB but none of the options described above appear to be available.  It's just a command line UI (?)[/COLOR][/FONT]

I'm generally familiar with a command line (OSX), but new to Linux.  

[COLOR=#131313][FONT=Verdana]Any insights into this?  How do I get this Ubuntu USB to work?[/FONT][/COLOR]

[COLOR=#131313][FONT=Verdana]System specs:[/FONT][/COLOR]
[COLOR=#131313][FONT=Verdana]- Intel Core i7[/FONT][/COLOR]
[COLOR=#131313][FONT=Verdana]- ASUS Z97-A Mobo[/FONT][/COLOR]
[COLOR=#131313][FONT=Verdana]- AVGA GForce GTX 970[/FONT][/COLOR]
[COLOR=#131313][FONT=Verdana]- UEFI BIOS [/FONT][/COLOR]
[COLOR=#131313][FONT=Verdana]- Samsung SSD[/FONT][/COLOR]
[COLOR=#131313][FONT=Verdana]- Seagate HD[/FONT][/COLOR]

---

### Post by alexandari on 2017-03-21
The system starts or "restarts"? Please make it clear

---

### Post by miquael on 2017-03-21
@alexandari  okay, good clarification ...

the system does not restart, but the display screen does, or it flashes for a moment and displays a pop-up window for just a second saying ("entering power save mode").  This is usually what the display does when the system restarts.  But the computer it self does not restart.

---

### Post by RobGoss on 2017-03-21
Before you attempted to install Ubuntu on this machine was there any other OS on this machine?

Are you able to boot in to the Ubuntu's Live desktop using a USB drive?

---

### Post by miquael on 2017-03-22
> **RobGoss said:**
> Before you attempted to install Ubuntu on this machine was there any other OS on this machine?

Are you able to boot in to the Ubuntu's Live desktop using a USB drive?

yes, I had installed Linux Mint last year ... but it has no network connection, so have not been using it at all ... that's one reason i'm trying Ubuntu now, as I hear that Ubuntu usually is compatible with most network hardware.

But yes, Mint is still on the SSD.  I was going to try Ubuntu off the USB first to see if it gets network connection, then if so, go ahead and install it (and write over Mint).  

So I went into BIOS and changed the disk boot order so that the system boots off the Ubuntu USB.  I am not seeing Ubuntu's Live desktop.  All I see if a black GRUB screen with option to install Ubuntu or try it out etc.  No matter which option I choose, then the screen goes blank (as described above).

Any insights?  Would it help to reformat the drive or remove Mint?

---

### Post by ubfan1 on 2017-03-22
The black grub menu screen used on UEFI machines requires you to edit the grub commands, not select a choice from some function key like legacy grub.  The editing instructions are at the bottom of the grub menu screen -- type "e" to edit. Use the arrow keys to move to the line beginning with "linux" and replace the "quiet nosplash" with nomodeset.  There may be other options required, but that's the first one to try.  Boot with control X (again instructions at bottom of screen).

---

### Post by miquael on 2017-03-23
That worked ubfan1! Thank you! :D

---

### Post by miquael on 2017-03-23
Now I just need to figure out how to configure the network settings.

---

### Post by ubfan1 on 2017-03-23
After you get the networking working, run software updater/Settings button/ Additional Drivers tab and install the proprietary Nvidia drivers so you don't have to go through the nomodesest business again.

---

