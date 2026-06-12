---
title: "Wacom Tablet Calibration in 9.10 Karmic"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mbeichorn on 2009-10-15
I did the switch to Karmic Beta this week on my Thinkpad X61t and I attempted to get my touch screen recalibrated, but the 9.04 work around to get wacomcpl to function does not seem to work.

I followed the instructions from: help.ubuntu.com/community/X61T

These did work in 9.04, but no longer, I have a sneaky suspicion that this might have to do with the hal depreciation as wacomcpl used hal to work with the devices.

Has anyone gotten wacomcpl to work?

Cheers!

---

### Post by Favux on 2009-10-15
Hi mbeichorn,

Does:
```
xinput --list
```
show your stylus?  With some Fujitsu tablet pc's the stylus seems to be missing.  Since the "work arounds" work with the usb tablets I'm wondering if there isn't a serial specific problem.

---

### Post by juancarlospaco on 2009-10-15
Theres a GUI to do that, i sucesfully installed, but its for Wacom only.

---

### Post by Favux on 2009-10-15
Hi juancarlospaco,

These are Wacom digitizers/tablets we're talking about.

---

### Post by mbeichorn on 2009-10-17
For the record
xinput --list
Did show Wacom Touch, Stylus, and Eraser and they do function.

The problem is I cannot calibrate the touch as it is way off at the edges of the screen. Previously I was able to get wacomcpl to work by messing with its HAL interface, but this time it did not work.

I am trying to find a way to get the touchscreen calibrated.

---

### Post by Whoopie on 2009-10-17
Hi,

to get the old-fashioned names "stylus", "eraser", ... that are used by wacomcpl or xsetwacom, I use a HAL fdi rule on my X61t.

Put the following file as "wacom.fdi" in /etc/hal/fdi/policy:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
         <merge key="info.product" type="string">eraser</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```I also attach it here.

Best regards,
Whoopie

---

### Post by mbeichorn on 2009-10-17
[FONT=Verdana][SIZE=2]Many Thanks!

For the record it works for the X61t when modified:

Put the following file as "wacom.fdi" in /etc/hal/fdi/policy:

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
         <merge key="info.product" type="string">eraser</merge>
      </match>
      <match key="input.x11_options.Type" contains="touch">
         <merge key="info.product" type="string">touch</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]
Of course it is important to set up the computer to restore settings on reboot.

```

sudo gedit ~/.xintric

```[/SIZE][/FONT][FONT=Verdana][SIZE=2]

and comment out

```

. /etc/X11/xinit/xinitrc

```Go to System>Preferences>Startup Applications and create a new entry named whatever you want. 
The command should be:

```

sh /home/yourusername/.xinitrc

```Thanks All![/SIZE][/FONT]

---

