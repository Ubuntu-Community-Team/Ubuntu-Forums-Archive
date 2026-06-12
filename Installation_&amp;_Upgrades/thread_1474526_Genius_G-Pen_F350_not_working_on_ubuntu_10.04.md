---
title: "Genius G-Pen F350 not working on ubuntu 10.04"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Solorflare on 2010-05-06
I got the G-pen F350 graphics tablet finally to work on ubuntu 9.10.
But alas back to square one now I have installed ubuntu version 10.04....
The fix that I found on the internet for 9.10 doesn't work on 10.04... didn't expect it to but hey I thought there wasnt any harm trying.

Now I can get the cursor to fly around the screen in 10.04 i can even press it down and drag and draw, but as soon as i go to lift the pen up (hovering) and place it somewhere else the cursor doesnt follow it until I either take the pen totally away from the graphics tablet then place it back over it hovering, or it stays put until i press down again and the cursor zooms to the new position... both are annoying.

Is there anyone else with this problem?
And does anyone know how to fix this?

Thank you...

---

### Post by dino99 on 2010-05-06
sudo update-pciids && update-usbids

sudo dpkg-reconfigure xserver-xorg-input-wacom  ( might be installed)

sudo dpkg --configure -a
sudo apt-get update && install -f

BETTER solution: add this ppa and install xserver-xorg-input-wizardpen

[https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

---

### Post by Solorflare on 2010-05-08
tried all of that didn't work... thanks anyways.

---

### Post by Solorflare on 2010-05-10
Could it be the fact that i am using a laptop with a touch pad?
I have this nagging feeling thats why...
I tried to disable the pad by the keyboard button and the graphics tab still behaved oddly... i even uninstalled the mouse driver in synaptics and still had the issue...

---

### Post by Lily1990 on 2010-09-14
Can you please write me how you made it work on Ubuntu 9.10? I've been trying to install it but whatever i do it doesn't work... Did you find an already compiled drive? Can you send me the link please?

---

### Post by Tango91 on 2010-09-18
I have the same tablet with the same problem, i'll try the things above and report back. i'll be interested to know what's causing it.

The tablet's certainly usable, but having to lift the pen an inch away from the tablet after every click is irritating.

EDIT: i fixed it although i'm not sure how. the last thing i did was  change both instances of  MatchDevicePath in 70-wizardpen.conf to  "/dev/input/event6"

i'm not sure quite why this is favoured over the device name in this  field, as specified in the howto, but it seems to work now. I've been  playing with it for hours but apparently this was the magic combination.

i'll post the entirety of my 70-wizardpen.conf just in case anyone is in a similar situation.

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event6"

    Option        "Device"    "/dev/input/event6"
    Option        "TopX"        "158"
    Option        "TopY"        "185"
    Option        "BottomX"    "10000"
    Option        "BottomY"    "6000"


   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event6"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

---

