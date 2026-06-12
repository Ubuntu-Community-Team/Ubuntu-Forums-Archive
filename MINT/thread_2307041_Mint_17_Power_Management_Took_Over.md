---
title: "Mint 17 Power Management Took Over"
date: 2015-12-21
forum: MINT
---

### Post by victor-hatley on 2015-12-21
[COLOR=#323D4F][FONT=Lucida Grande]I have a problem with a blank screen. I have posted in the HP Support Forum, Linux Mint Forum, Reddit, etc... Here's the computer specs:

[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]HP P7-1254[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]MOBO: AAHD-2HY
BIOS: HP Setup Utility Version ??[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]A6-3620 Processor with integrated Radeon HD6530D[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]1 TB HDD[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]8 GB RAM[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Windows Home Pro 7 SP1 dual boot - Linux Mint 17 (cinnamon Rafael)

[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]The Symptoms:[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]The computer will momentarily ( .5 second flash) display the BIOS splash screen then go black. After a few moments the disk indicator starts flashing indicating loading Mint (I assume, as it is the first entry on the Grub boot loader) and after a few seconds of disk activity, the monitors activity indicator flashes yellow for a few seconds then goes green. That is when the desktop and pointer flashes for about a half a second then black again. IF i leave the computer alone and wait til (again I assume) Mint goes into sleep mode (monitor indicator turns yellow,) and shake the mouse I get the desktop for about the same half a second then black again.

[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]Here's what led up to it:[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]I installed Linux Mint 17 (cinnamon, Code Name: Rafael) in a dual boot situation on the HDD from a USB stick, verified that ALL systems were up-n-running...booted into Win 7 AND Mint and surfed the internet, etc. in both OSes. Went into Mint and set up Power savings options to NEVER turn off ANYTHING...I thought. I updated and upgraded the Mint system, then installed Chrome to Mint. I went to the bathroom...and when I came back the computer (booted into Mint) has went to sleep. I shook the mouse, pressed different wake up key combinations, and finally tried rebooting via holding the power button til shut down and power back on...now everything is as described above.

[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]I am presently operating on my wife's laptop, but can boot the live version I used to install the Mint originally. I assume that I could probably network into the desktop from the laptop using a cable, but I have never done this, so I would need pretty explicit directions on what to do to achieve this.

I assume that somehow the Mint 17 Power Management doesn't play well with UEFI as the problem starts with BIOS loading...and my research has led me that direction. So I have tried to find the EXACT procedure to set the defaults there, but haven't had any success there either.

ANY help, or input would be greatly appreciated...I really need this computer, and have posted this issue all over...

EDIT:
t 
The computer IS booting into the first entry on the GRUB boot loader...Mint 17. IF I hit cnt+alt+t and open a terminal, then wait til the computer sleeps so I can get the half second desktop to verify the terminal is open then enter "sudo reboot" hit enter, enter my password, hit enter, the computer reboots.

I need a way to reload the driver and desktop session from terminl. I have tried startx, kill then startx, tried to disable the power saver in terminal, but I have tried to use the full screen terminal, ctrl+alt+F2, but the computer won't sleep in this state so I can't get a verification of anything when the computer sleeps...ANY ideas?? It seems tha I have the folks in this forum stumped...it seems

[/FONT][/COLOR]

---

