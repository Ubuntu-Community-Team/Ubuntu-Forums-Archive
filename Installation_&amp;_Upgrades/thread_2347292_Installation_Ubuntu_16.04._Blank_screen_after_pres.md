---
title: "Installation Ubuntu 16.04. Blank screen after pressing Install. Windows 10."
date: 2016-12-23
forum: Installation &amp; Upgrades
---

### Post by auroragrace on 2016-12-23
Hello, when I go to install Ubuntu 16.04 on Windows 10 I get a blank screen after pressing 'install Ubuntu'. Please help.

---

### Post by Bashing-om on 2016-12-23
auroragrace; Hello; Welcome to the forum .

What we often see here with that issue is there is no graphic's driver available.
We can tell the system to disregard and load a fall back driver .. that will do until we can do better (install the proper driver) .
Now we need to know what the hardware is that we are to try and march a driver for:
Post back - between code tags - the output of terminal command:
From the liveDVD(USB)
```

lspci -k|grep -iEA5 'vga|3d'

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So we see where we go from here .

[INDENT][INDENT]sometimes, ya got to step away from the box
[/INDENT][/INDENT]

---

### Post by auroragrace on 2016-12-24
Hello, thank you. 

When I make this command it says 'Syntax Error' and 'Incorrect Command'.

---

### Post by Bashing-om on 2016-12-24
auroragrace; Hey .. hey ..

Copy and paste for best results, or check for typos, as the command must be exact. 
It is valid as given:
> 
sysop@x1604:~$ lspci -k|grep -iEA5 'vga|3d'
06:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 710B] (rev a1)
	Subsystem: eVga.com. Corp. Device 2712
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
06:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
	Subsystem: eVga.com. Corp. GK208 HDMI/DP Audio Controller
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
sysop@x1604:~$ 

is my output for your reference.

[INDENT][INDENT]computers are so ... literal
[/INDENT][/INDENT]

---

### Post by auroragrace on 2016-12-24
Hey. I typed it exactly as it is, and tried a number of times and ways. I am typing it into the command line at the startup where it says 'try Ubuntu' or 'Install Ubuntu', so I am unable to copy and paste it (as far as I am aware). Is that what you meant by 'from the live USB'?

---

### Post by Bashing-om on 2016-12-24
auroragrace; Hey;

Let's get you on the same page that I am on:
Boot the liveDVD
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time;
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
At the desktop key combo crl+alt+t to activate a terminal.
In this terminal execute:
```

lspci -k|grep -iEA5 'vga|3d'

```
All we are doing here is looking and finding out what the graphic's hardware is . Once the hardware is identified we can move on to the next step to insure a proper driver is installed in the actual install.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by auroragrace on 2016-12-26
I can't seem to get to that page. I am running Ubuntu from USB. I get to the startup page where it says 'Try Ubuntu' or 'Install Ubuntu'. If I press either I get the Purple screen with just a row of dots on and 'Ubuntu', then everything goes blank. There are no stick figure keyboard emblems on this screen. 

I hit any key at the purple screen and then I get white text on a black screen saying loads of things, I noticed 'No matching machine driver found'. Then nothing happens. 

I cannot get to the booting options screen to select 'nomodeset'.

---

### Post by Bashing-om on 2016-12-26
auroragrace; K;

In this case perhaps we have a EFI endowed machine, In this case it is the escape key that grub looks for.
As soon as the firmware screen clears, spam the escape key to get grub's attention. There is but a 3 second window of opportunity; if at 1st you do not succeed, try try again.

different manufacturer ;
different architecture ;
[INDENT][INDENT][INDENT]different process
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-12-26
Which of these screens do you initially get, grub menu on black screen or BIOS menu?
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And if newer UEFI system, you can boot in either UEFI or BIOS mode, but want to boot installer in same mode as Windows, UEFI or BIOS. UEFI should show 2 choices to boot flash drive if Secure Boot is off. If secure boot is on, then only UEFI is shown.

---

