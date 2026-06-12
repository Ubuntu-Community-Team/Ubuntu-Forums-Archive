---
title: "Matrox G200 AGP 4 Head Video card Ubutu 8.04"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by thesheff17 on 2008-05-01
I'm trying to get my Matrox G200 AGP 4 head video card to work with ubuntu 7.10 or 8.04 and neither seem to work.  I have tried to modify the xorg a billion times and I will restart X and just tell me that it starts up in low graphic modes.  I also have 2 AL2216w acer monitors that support 1680x1050 but can't get any thing working beyond the one monitor.

I see all the matrox stuff through lspci and I see that Ubuntu sees the separate card when in Ubuntu under screens and display.  

PLEASE HELP!:confused:

---

### Post by mark1softie on 2008-05-04
This worked for me in Gutsy Gibbon [6.10], but not for Hardy Heron [8.04], with one G400 dual-head adaptor.

Check the "/etc/log/Xorg.0.log" file.
It will probably include an error message:
"(EE) MGA(1): This card requires the "mga_hal" module for dual-head operation
        It can be found at the Matrox web site <http://www.matrox.com>"

If so, download and install a matched pair of "mga_drv.so" & "mga_hal_drv.so" drivers:

(0) Download the latest Matrox MGA v4.4.3 drivers:

- Browse to the website "http://tuxx-home.at"
- Goto [from RHS links] "categories" "Matrox MGA Drivers"
- Select "2007/03 - Tiny update to the Unofficial MGA driver"
- Save "matroxdriver_mga-x86_32-4.4.3-installer.run" 32- or 64-bit, as needed for your kernel] to disk.

(1) Extract the files:

$ cd <directory holding the saved file>
$ chmod +x matroxdriver_mga-32.4.4.3-installer.run
$ ./matroxdriver_mga-32.4.4.3-installer.run --extract_only

(2) Save the original driver:

$ sudo mv /usr/lib/xorg/modules/drivers/mga_drv.so /usr/lib/xorg/modules/drivers/mga_drv.so-orig

(3) Install the latest driver version:

$ cd matroxdriver_mga-x86_32-4.4.3/xserver/7.1.0
$ sudo cp -p mga_drv.so mga_hal_drv.so /usr/lib/xorg/modules/drivers
$ sudo chmod 644 /usr/lib/xorg/modules/drivers/mga_*drv.so
$ sudo chown root:root /usr/lib/xorg/modules/drivers/mga_*drv.so

(4) Set up the "/etc/X11/xorg.conf" Xorg configuration file.
- In 'Section "Module"', add:
    Load "mga_hal"
- Enable the Xinerama dual-screen facility, with:
'Section "ServerFlags"
    Option "Xinerama" "true"
EndSection'
- Set up "device", "screen" and "monitor" sections for your second monitor, if they are not already present.
- Ensure the 'Section "Serverlayout"' includes both screens.  Mine says:
'Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" leftof "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
 EndSection'

(5) Log out from your user account.

(6) from the "options" menu of the login screen, change the highlighted selection from "GNOME failsafe" to "GNOME".

(7) Reboot the computer [just logging in didn't work, for me].

If your xorg.conf is set up correctly, the second screen should come to life.

---

### Post by mkeuter on 2008-08-02
Your answer is almost correct, it helped me a lot.. 
Just remove the line:
     Load mga_hal

after this you have to add this in the Section "ServerFlags" to get past the next error:

     Option "IgnoreABI" "True"

And all should be fine.

this info can be found on [http://forum.tuxx-home.at/viewtopic.php?f=10&t=78](http://forum.tuxx-home.at/viewtopic.php?f=10&t=78)

thx to get me started in the right direction..

---

### Post by thesheff17 on 2009-06-08
I have tried this card again with ubuntu 9.04 and still no luck.  I just don't have time to troubleshoot this with so much other sys admin work to do.  Someday a quad port card will work out the box with ubuntu.......someday

---

