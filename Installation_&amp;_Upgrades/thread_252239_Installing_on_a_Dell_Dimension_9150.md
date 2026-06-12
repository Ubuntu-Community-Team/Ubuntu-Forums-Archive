---
title: "Installing on a Dell Dimension 9150"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by voidmain on 2006-09-06
Okay, I'm installing Ubuntu Dapper 6.06 on my Dell Dimension 9150. This is WAY more painful that installing on my Inspiron 700m, so I'm going to write it all down for folks:

1. Boot using the desktop CD and safe graphics mode. My display is widescreen so it doesn't display anything until the entire live cd is loaded into memory and X starts, so be patient if you don't see anything.

2. I had an old redhat install on there. Redhat does really tricky things with hard drives, so I had to manually partition the disk to remove the redhat garbage. I removed all partitions and created two new partitions. The first one is everything except 3G and is ext3. The second is swap.

3. Next, I rebooted. The driver that X is using right now should be vesa. If you have a wide-screen monitor as well, it might not display anything until X is started again. Once x starts, you should be able to open a terminal and edit you /etc/X11/xorg.conf file (make an orig copy first). Change the Driver definition in the "Device" section like this:

> 
Section "Device"
  ...
  Driver    "radeon"
EndSection


Change the maximum resolution section so that the resolution for your display appears there. Since I have a 21" widescreen, mine looks like this:

> 
SubSection "Display"
  Depth     24
  Modes     "1680x1050" "1280x1024" ...
EndSubSection


This will allow you to change the resolution and have it behave correctly (this might not actually be necessary, but I did it just in case). Once the X changes have been made, all pseudo terminals should also work. No clue why they don't otherwise. Must be how Ubuntu sets up the display and the driver probably foobars the video bios or something.

4. Restart X using ctrl-alt-backspace. Things should now display correctly.

Everything else seems to work. I'll update this as I find other stuff.

---

### Post by Sammi on 2006-10-07
Thanks. That helped me :D

---

### Post by MepisReign on 2006-10-10
Actually I ordered the same system, mine its a XPS 400 which is basically the same, the only difference is the tag (Dimension 9150) at the top front of the tower. My Mepis installation is having issues with the display, an E196FP, 19 inches flat panel, I can't adjust the color depth to "millions of colors". I have an Geforce 7300 LE installed on that system :(

Regards, 

MepisReign

---

### Post by voidmain on 2006-10-10
I have a Radeon and that was the main source of pain for me. The Radeon driver doesn't seem to quite correctly output all the display formats. My color depth is set to 24 right now and everything works fine, but only after the system has started X. If X doesn't start then nothing shows up on the display.

---

### Post by jimbonnet on 2006-10-25
My 9150 installed OK however I'm running the ATI card with 24" monitor. I ended up grabbing the fglrx driver as I never could get the ATI driver to give me full resolution on the 24"

otherwise this box is running great.

--jim

---

