---
title: "[SOLVED] upgrade ibm t42 8.04 to 8.10 video lowres only!"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by chchandler on 2008-11-11
Upgraded my T42 thinkpad from 8.04 to 8.10 and now it can't detect any displays.  I can only start in low res mode.  :confused:

---

### Post by chchandler on 2008-11-11
On boot I get fuzzy graphics then msg 

"Ubuntu is running in low graphics mode.  Your screen, graphics card and input device settings could not be detected correctly.  You will need to configure these yourself."

My original 8.04 install had no problem finding them all and setting them up right first try.  Thus, I have no idea how they were set up.  Sigh.  This Thinkpad has the 1450x1080 screen, IIRC.  

Also, my blue center button doesn't scroll anymore.  Used to be a quick edit of xorg.conf (I think) fixed that but 8.10 supposedly detects all that stuff differently.  

It's different, all right!

Xserver log file contains II lines for cant find core pointer, core keyboard.  It loads the Radeon module with drivers for the 9600, which IIRC is what I have.  

:0.log ends with EE No input driver/identifier specified
EE config/hal:NewInputDeviceRequest failed.

---

### Post by chchandler on 2008-11-11
Screen resolution gave me 2 choices... 800 x 600 and 640 by 480 I think.  Tried changing that and now even a re-boot won't get me low res graphics... just a diagonal smear of my wallpaper.

---

### Post by chchandler on 2008-11-11
lspci | grep ATI says ATI RV350 Mobility Radeon 9600 M10.  I know I saw that driver listed in the Radeon Module in xorg log.

---

### Post by chchandler on 2008-11-12
bump.  I know the wizards are busy, but I'm off-line with nothing - not even lo-res - until there's a fix.  

First, I need to know how to, via CLI, re-set the lo-res graphix to the 800x600 or something so I can see the gui.  Then I need to figure out how to make 8.10 see the hardware.  Or, I need to re-install 8.04 from the CD.

Or, I need to re-install XP and live with it.

---

### Post by chchandler on 2008-11-12
OK, I think it has been solved enough for me to *WORK* on my machine again.  

From the page for Bug # 284408:

Hali wrote - 

for my radeon 9700 TX the following instructions in a duplicate thread worked:
1. sudo apt-get remove --purge fglrx*
2. sudo apt-get remove --purge xserver-xorg-video-ati
xserver-xorg-video-radeon
3. sudo apt-get install xserver-xorg-video-ati

So, that worked for me as well.

---

