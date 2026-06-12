---
title: "Karmic Koala UNR and the Elantech Touchpad"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cylverbak on 2009-10-19
I'm using an EeePC 1000 (EeePC 901) which has the elantech touchpad. Does this release support this hardware? I am not able to turn it off or disable when typing which I find very frustrating. I've tried using the "System>Mouse>Touchpad>Disable while typing" to no effect. Is there some tweaking necessary that I've missed?

---

### Post by deathsshadow77 on 2009-10-19
I am also using an eee pc with an elantech touchpad and I have to say that the driver is pretty terrible. Compared to how the touchpad is supposed to work, the touchpad under karmic is jumpy. Middle click and right click are switched for some reason (middle click is supposed to be 2 fingers and right click is 3 but in karmic, right click is 2 and middle click is 3). Also, this has nothing to do with the driver but I hate how by default 2 finger scrolling is disabled and tap to click is disabled.

---

### Post by cylverbak on 2009-10-19
Found an app called gpointing-device-settings that recognizes the elantech touchpad and at least gives me the option of turning it off. There are scroll options as well that I may play with later. I normally use a bluetooth mouse on the netbook.

Can't find an icon for it in UNR so am running it from terminal with "gpointing-device-settings".

---

### Post by deathsshadow77 on 2009-10-19
yeah I tried it too but it didnt change much of anything

---

### Post by midnightflash on 2009-10-24
Indeed very disappointing... 
On the other hand... the only thing really disturbing, after I found a workaround for the yelling fan.

---

### Post by cylverbak on 2009-10-25
Hi midnightflash, how did you manage to tame your yelling fan?

---

### Post by midnightflash on 2009-10-25
In short: install lm-sensors (to get fancontrol) and powernowd (just to drop idle-threads).

Then make a new file:
```
$ sudo nano -w /etc/fancontrol
```
and fill it with:

```
INTERVAL=5

FCTEMPS=hwmon1/pwm1=hwmon0/temp1_input
FCFANS=hwmon1/pwm1=hwmon1/fan1_input
MINTEMP=hwmon1/pwm1=55
MAXTEMP=hwmon1/pwm1=70
MINSTART=hwmon1/pwm1=50
MINSTOP=hwmon1/pwm1=50
```
```
I think it's not necessary... but make sure fancontrol is started in the runlevels. [CODE]$ sudo sysv-rc-conf
```[/CODE]

After a reboot you should be able to enjoy the silence. (Least as long as your EeePC is not working to hard.)

---

### Post by midnightflash on 2009-10-25
Sorry for the doublepost... but there is another workaround:

To get the middleclick working with an 901:```
$ xinput set-int-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 8 0 3 0 0 1 2 3
``` At least it does the right way for me now.

In fact the last two (the "2" for middleclick and the "3" for rightclick) are turned wrongwards by default in Karmic.

If the line above works for you... you can put it in the startup programs.

---

### Post by dreamersbrow on 2009-10-28
@midnight flash: Thanks for posting this.  I was trying to figure out how to get those switched.  

I was under the impression that while X no longer requires and xorg.conf file, if there was one it would follow the instructions contained therein.  This is what I have in my xorg.conf file:

```
Section "InputDevice"
    Identifier  "ETPS/2 Elantech Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"        "/dev/psaux"
    Option      "Protocol"      "auto-dev"
    Option      "HorizScrollDelta"  "0"
    Option      "MaximumTapTime"        "200"
    Option      "ClickTime"     "50"
    Option      "VertTwoFingerScroll"   "1"
    Option      "HorizTwoFingerScroll"   "1"
    Option      "VertEdgeScroll"    "0"
    Option      "HorizEdgeScroll"   "0"
    Option      "SingleTapTimeout"  "400"
    Option      "FastTabs"          "0"
    Option      "VScrollEmuOff"     "1"
    Option      "VertScrollDelta"   "80"
    Option      "SHMConfig"         "1"
    Option      "CircularScrolling" "1"
    Option      "CircScrollTrigger" "8"
    Option      "CircScrollDelta"   "0.14"
    Option      "TapButton3"        "3"
    Option      "TapButton2"        "2"
EndSection    

```I copied this directly from my xorg.conf file in eeebuntu3 (which as I understand is just a modified jaunty.)  Can someone tell me why this failed to switch my taps around?

Thanks

---

