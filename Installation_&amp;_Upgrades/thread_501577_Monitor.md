---
title: "Monitor"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by DFergATL on 2007-07-15
I am new to Linux and have spent the last few days trying different distros.   I really like Ubuntu, I am having one problem I need help with and I have a couple of question.

The monitor configued by the install is incorrect.  I have a generic monitor and none of the distros got it right.  In others, for example Xandors, there is a drop down box that allows you to manually change the monitor type.  Mine will work fine if used as a "Generic 1024 x 768" with a refresh rate of 70.  I am unable to figure out how to do that in Ubuntu.  I can't find where I can just change the monitor type.  I tried to manual edit the xorg.conf file based on something I had found regarding this very problem in a wiki.   Didn't work out well.  All I need is what I stated before a Generic monitor with a res of 1024 x 768 and refresh of 70.

Also, can anybody tell me what the advantage of purching Ubuntu vs just downloading it?

Dave

---

### Post by jim_p on 2007-07-15
Have you tried installing the appropriate drivers for your vga card?
I had a similar problem.My TFT could run at 1280*1024 with 60Hz refresh rate without drivers (without nVidia's propiertary drivers I mean) but flickering was noticeable here and there. Once I got them installed the flickering was gone and inside nvidia-settings I could see the my monitor's name and loads of other info!

Ubuntu is free.You don't buy Ubuntu, you actually buy an already made cd, with covers etc which is the same thing as if you had burned the .iso to an ordinary cd. This helps if you are on a slow internet connection or... if you have no time to download the iso.

---

### Post by DFergATL on 2007-07-15
Ya, I am sure I have the right driver.  I have this problem with all Linux distros.  It sets my Monito to the lowest common one.  In other distros you can actually manually select your monitor.  in this one it seems that it gets to decide for you and that is it.  If it is wrong...well then tough.  I will keep trying for a while but if I can't fix it then I will have to give it up for an other distro.  It would be a shame, this is the only thing I can't get to work right.

Dave

---

### Post by Wim Sturkenboom on 2007-07-16
Edit your xoirg.conf

Points to pay attention to:[LIST=1]
[*]HorizSync and VertRefresh in the monitor section; they should match the capabilitys of your monitor (so check the monitor's manual). If you only want 1024x768@70Hz and can't find the monitor specs, you can use the following max (in bold) values (fH=**56**kHz and fV=**70**Hz)
[*]Resolutions in the display subsections; remove what you don't need or is not supported.
[/LIST]

```

Section "Monitor"
Identifier   "Monitor0"
VendorName   "DEL"
ModelName    "DELL P790"
HorizSync    31.0 - **92.0** [COLOR="Red"]# set bold to max value[/COLOR]
VertRefresh  50.0 - **150.0** [COLOR="Red"]# set bold to max value[/COLOR]
Option      "DPMS"
EndSection
.....
.....
Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport   0 0
Depth     24
**modes     "1024x768"** [COLOR="Red"]# adjusted for this thread[/COLOR]
EndSubSection
EndSection

```Only pay attention to the bold values/lines; the rest might be specific to my setup.

If you still have problems, please post make and model of video card and monitor as well as the section device, monitor and screen from you xorg.conf file.

---

### Post by DFergATL on 2007-07-17
One more question please.  At one point I played around with the xcon.conf file a messed it up and then was not able to figure out how to fix it.  Normally, I would just make a copy of the file for backup.  When I tried to do this using the "notepad" type of app.  I was told that I didn't have the right permissions.   I learned how to use "sudo nano /etc/x11/xcon.conf" to enter and edit the file.  However I am not sure how to make a backup copy first from the command line, old DOS user here.  And beyond that how to I fix it from the command line once if I need to?   

OK an ohter question, and thanks for helping.  Where can I find a list of the most common command line tools and how to use them?

Dave

---

### Post by DFergATL on 2007-07-17
Here is what my xorg.conf looks like now.  Before I make changes please just take a look.  Some of the things in mine don't match yours and because am not sure of what that may or may not mean.......

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G70 [GeForce 7600 GS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4

---

### Post by DFergATL on 2007-07-17
YEA!!!  I got it!!  

Ok, so in a few days I am getting a new ViewSonic monitor.  What can I expect when I connect it and boot up? Will it autmaticly detect it?  Will I have to redo the whole thing manually??

I hope that in the future the devs put something in here to make things like this eaiser.

Dave

---

### Post by Wim Sturkenboom on 2007-07-18
You have to reconfigure. It will probably autodetect, but the changes that you've made will overwrite it.

The important things when you get your new monitor:
- refresh rates in the monitor section
- resolutions in the screen section (subsection display)

One of the things that you might encounter with your new monitor is that it will not go over 75Hz although it might be able to do so at certain resolutions.
In that case you can add *Option "UseEdidFreqs" "False"* to the *device* section.

There is a command to reconfigure your system, something with *dpkg-reconfigure*. If you want to use it, just search this forum for it.

Enjoy the new monitor.

---

### Post by DFergATL on 2007-07-18
Thanks for the advice.

---

