---
title: "Installation failure of UbuntuStudio 8.04 LTS"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Robgrief on 2008-05-14
Installation runs fine until booting up from the hard disk for the first time just after the "Ubuntu studio" graphic display.

Thereafter the system crashes completely - both the screen and the keyboard dies. The power needs to be switched off and then back on again to bring back the PC to life.

The above is duplicated when the "startx" command is issued from the command line.

On my Linux system (hda6 is 'swap', hda7 is '/' and hda8 is '/home'), I cannot find the files XF86Config and Xconfigurator, and the file xfree86 (in 'xkb' folder) is not populated with any meaningfull data.

As a matter of interest, I use 3 other operating systems on the same PC and they run fine:

1)
MS-DOS + Win3.11 on hda1, 

2)
WinXP on hda5 (although I have to use a 'generic graphic card' for WinXP to run),

3)
'Knoppix' and 'graf-pup' - both live distros from CD run fine on Xorg with the user having a selection of CRT resolutions.

Perhaps a clue is in the attached extract of the installation log showing 'FATAL' errors of a missing 'generic' Kernel module.

It is my first time for using both Ubuntu and Debian, and my limited knowledge is exhausted - can anyone help?

Regards,
Rob

---

### Post by teaker1s on 2008-05-17
As you have not received any better advice:-

**just a suggestion** if you have a wired internet connection you could 
you could try these two commands 
```
sudo apt-get install ubuntustudio-desktop
```
```
sudo apt-get install ubuntu-standard
```

i think your installation has not gone well and is corrupted or failed to properly install

Hopefully this will drag the missing modules and repair the errors.

---

### Post by Robgrief on 2008-05-20
Success! Problem was solved with the 3rd Graphics card I tried, which was a Nvidia GLX5500.

UbuntuStudio looks great - much appreciation and thanks to all the UbuntuStudio contributors out there!

---

