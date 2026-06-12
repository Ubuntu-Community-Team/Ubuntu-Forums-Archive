---
title: "Startup question"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by holz on 2007-04-07
Hi all

Total newbie, after some painful startup i finally got the 945M Intel video chip to work on my Toshiba T2050. I downloaded the 915resolution, and in order to get the 1440 900 resolution I am executing the line sudo 915resolution 38 1440 900 16. I have to do this with every boot, then get out of X and return. How do I do this automatically before X starts?
TIA

Holz ](*,)

---

### Post by sharke on 2007-04-07
Goto /etc/default/915resolution and edit with your settings reboot and your sweet
Regards
Sharke

---

### Post by holz on 2007-04-07
No luck (if I did the right thing...)
It created a new file, added the line but no luck. What other option do I have?](*,)

---

### Post by sharke on 2007-04-07
You should not have created a new file thecommand i gave should have opened a existing file.Here is the instructions which you can find in /usr/share/doc/915resolution.

 No luck (if I did the right thing...)
It created a new file, added the line but no luck. What other option do I have?


915resolution for Debian
------------------------

915resolution changes the resolution of an available vbios mode.

1. First, you need to check available modes by:

# 915resolution -l

2. You will get a mode list such as:

Intel 800/900 Series VBIOS Hack : version 0.4.7

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x768, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x768, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x768, 32 bits/pixel

3. Write the mode number and resolution which you want to use to
   /etc/default/915resolution. For example:

MODE=3c
XRESO=1400
YRESO=1050

# optional setting
BIT=32

4. Reboot or run "/etc/init.d/915resolution start" by hand.

5. To use specified resolution, you need to modify your X configuration
   file (If you use Xorg, it's /etc/X11/xorg.conf)

SubSection "Display"
    Depth           24
    Modes           "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection




915resolution with suspend/resume function:

If you are planning to use the suspend/resume mechanism and you are using a 
video mode that requires to run 915resolution, it's quite possible that your 
video card requires you to run 915resolution also on resume. If you use the 
hibernate package there is an option to call 915resolution on resume.
If you want to use it just activate it in the file "etc/hibernate/common.conf" .
There is an uncommented line called "# Runi915resolution yes" .


  -- Steffen Joeris <steffen.joeris@skolelinux.de>, Thu, 15 Jun 2006 17:18:41 +0200

Pick a mode that is not being used and edit the /etc/default/915resolution to suit.

Regards
Sharke

---

### Post by holz on 2007-04-07
Sharkee

I did a search on the net and found the auto915resolution, [http://roland-lopez.blogspot.com/]("http://roland-lopez.blogspot.com/")
This fixed the issue,but thank you very much for taking the time and trying to help.

---

### Post by sharke on 2007-04-08
Glad you fixed your problem thanks for that link will come in handy.
Regards
Sharke

---

