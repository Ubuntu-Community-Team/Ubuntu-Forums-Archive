---
title: "Screen resolution on Dell mini 12 with Jaunty alpha6"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jcoglan on 2009-03-24
Hi all,

Just installed Jaunty alpha 6 on a Dell Mini 12. All seems to work fine save for the screen resolution, which only goes up to 1024x768. Does anyone know how to get the 1280x800 resolution, and can they explain to an absolute beginner? I've only done a couple of Ubuntu installs before and never had any issues.

---

### Post by markbuntu on 2009-03-24
Jaunty is still in development and testing and many items do not work/need to be fixed before release. If you are not an experienced user participating in testing/bug reporting you should not be using it.

---

### Post by jcoglan on 2009-03-24
Fair enough, though Jaunty is the first release I've managed to install -- Hardy couldn't see my hard drive and Intrepid couldn't start X. Obviously I'm happy to stick with a mostly-working alpha set up but I'd be grateful if someone could tell me whether this is likely to be fixed in the final release.

---

### Post by markbuntu on 2009-03-24
You could go lurk around in the Development and Testing forum.

---

### Post by nanog on 2009-03-25
I set up a friends mini 12 with the jaunty netbook edition and had no problems. Have you checked /var/log/dmesg to make sure your intel driver is loaded properly. How did you install?

You could try using xrandr:

xrandr --auto
xrandr --addmode VGA 1280x800
xrandr --output VGA --mode 1280x800

edit your xorg.conf (you really should not have to do this):

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

---

### Post by WhiskoKid on 2009-03-28
The issue here isn't the screen resolution being incorrect, rather that there is no video driver available for the Mini 12, and the display falls back to the unaccelerated, VESA mode.

See this thread: [http://ubuntuforums.org/showthread.php?t=1079011](http://ubuntuforums.org/showthread.php?t=1079011)

I recently installed Jaunty beta on my Mini 12 and everything BUT the video driver worked well, sound, wireless, bluetooth, suspend/hibernate.  And because of the VESA driver, the video is quite slow.  Unfortunately it looks like it could be a long wait before an updated Linux driver for this graphics hardware is released.

---

