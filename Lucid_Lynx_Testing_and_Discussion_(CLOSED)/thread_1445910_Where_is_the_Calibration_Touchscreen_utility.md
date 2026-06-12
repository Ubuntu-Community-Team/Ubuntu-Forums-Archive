---
title: "Where is the Calibration Touchscreen utility??"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NCLI on 2010-04-03
I've installed it from the Software Center, purged and reinstalled it from Synaptics, and it's still not showing up! Anyone else experiencing this!?

---

### Post by andrew frank on 2010-04-08
same problem. touch screen works (sort of) but needs calibration. where is the utility?
i have opened a bug in launchpad -- #557923 
andrew

---

### Post by mcduck on 2010-04-08
Have you tried starting it from a terminal? Do you get any errors? Have you checked the Menu Editor, perhaps the menu entry is there but it's disabled?

---

### Post by NCLI on 2010-04-12
Nope, it's simply not there.

---

### Post by wsgts on 2010-04-14
Bump..

Anyone has a status of this issue?  

T

---

### Post by Leed on 2010-04-21
Same thing, used to be there in Jaunty UNR

---

### Post by Leed on 2010-04-22
Could perhaps anybody explain how to calibrate the touchscreen via terminal? Been searching for hours in Google, there must be some way?

---

### Post by sintacto on 2010-04-22
I have been using touchcal-0.31
downloaded it long ago you must run it with out x running
then it gives values to put into a xorg.conf
I just pasted it where it used to go and it works
some one surely knows a better way than this
so ill check back.

here is what my xorg.conf looks like for touch screen i have.

Section "InputDevice"
        Identifier "ELO Touchscreen"
        Driver     "elographics"
        Option     "Device"     "/dev/ttyS0"
        Option     "AlwaysCore"
        Option     "screenNo"    "1"
        Option     "MinX" "335"
        Option     "MaxX" "3724"
        Option     "MinY" "511"
        Option     "MaxY" "3665"
        Option     "UntouchDelay" "5"
        Option     "ReportDelay" "1"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    InputDevice    "ELO Touchscreen"
EndSection

---

### Post by Leed on 2010-04-23
Thanks, but there is no xorg.conf in Lucid

---

### Post by cariboo on 2010-04-23
You can create an xorg.conf file by typing in a terminal:

```
sudo touch /etc/X11/xorg.conf
```

---

### Post by Leed on 2010-04-28
and that still works with the new Xorg?

---

### Post by mcoleman44 on 2010-04-28
If you are using wacom and referring to 
```
wacomcpl
``` 
This wont work with the latest version of Wacom for lucid. Plus, in Lucid evdev controls touch so you could do what cariboo907 mentioned. And yes, it still works.

---

### Post by mcoleman44 on 2010-04-28
What type of touchscreen do you have?

---

