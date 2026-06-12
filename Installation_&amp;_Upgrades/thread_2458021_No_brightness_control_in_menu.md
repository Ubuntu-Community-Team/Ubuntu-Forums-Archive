---
title: "No brightness control in menu"
date: 2021-02-14
forum: Installation &amp; Upgrades
---

### Post by dorpapst on 2021-02-14
I have newly installed Ubuntu and everything works fine, except for the fact that changing brightness is not available at all.
[ATTACH=CONFIG]287963[/ATTACH]
Usually I have a slider next to those for the microphone and the sound in the upper right corner, but there is nothing there.

It isn't possible to change it inside the Settings either, that was usually possible under Display or Power. 

Do I need to install something more to archive that? Or is that a known bug?
The graphic card is an GeForce GTX 1650 and I am using the nvidia-driver-460 for it.

Many regards and thanks,
Lukas

---

### Post by username2758 on 2021-02-15
Hey,

I have this very issue too, which got unanswered.

The brightness slider on Ubuntu and other Linux distributions never really worked on any of my graphics cards unfortunately (AMD and Intel).

My workaround has always been install brightness-controller. It has always worked regardless of graphics card.

Hope you find the solution to your problem.

---

### Post by ActionParsnip on 2021-02-15
Does the system have a make and model please?

---

### Post by dorpapst on 2021-02-16
I have built the system myself.
Its a Gigabyte B550M Aorus Elite motherboard, AMD Ryzen 5600X CPU and a GeForce GTX 1650 GPU.

I know of the existence of the brightness slider Add-on, but still, that isn't the best solution as it resets itself after suspend and restarts.

---

### Post by dorpapst on 2021-02-16
I have got one more interesting information:
When I use that command here:
```
sudo find /sys/ -type f -iname '*brightness*'
```

I get the following output:
```
/sys/devices/pci0000:00/0000:00:08.1/0000:07:00.3/usb5/5-1/5-1:1.0/0003:046D:C328.0001/input/input2/input2::numlock/brightness
/sys/devices/pci0000:00/0000:00:08.1/0000:07:00.3/usb5/5-1/5-1:1.0/0003:046D:C328.0001/input/input2/input2::numlock/max_brightness
/sys/devices/pci0000:00/0000:00:08.1/0000:07:00.3/usb5/5-1/5-1:1.0/0003:046D:C328.0001/input/input2/input2::capslock/brightness
/sys/devices/pci0000:00/0000:00:08.1/0000:07:00.3/usb5/5-1/5-1:1.0/0003:046D:C328.0001/input/input2/input2::capslock/max_brightness
/sys/devices/pci0000:00/0000:00:08.1/0000:07:00.3/usb5/5-1/5-1:1.0/0003:046D:C328.0001/input/input2/input2::scrolllock/brightness
/sys/devices/pci0000:00/0000:00:08.1/0000:07:00.3/usb5/5-1/5-1:1.0/0003:046D:C328.0001/input/input2/input2::scrolllock/max_brightness
```


Which is very weird, because those are only those three small lights for capslock, scrolllock and numlock

---

### Post by Holger_Gehrke on 2021-02-16
Since you say that you built the system yourself I'm going to assume that it's not a laptop and has some kind of external display. In that situation the brightness of the display (or more specifically the intensity of the backlight) is not under direct control of the system, which is why there's not brightness slider in that menu.
You can usually set the brightness through the on-screen-display menu of the display.
Another way would be to use the brightness option of xrandr (see 'man xrandr' in a terminal) but this works by changing the colours in memory, so it can't be used to increase the maximal brightness.
And then there's ddccontrol which uses the display data channel (an i2c bus that's part of all modern display connectors) to control the display. There's a graphical frontend for ddccontrol named 'gddccontrol'. 
xrandr is installed by default, ddccontrol and gddccontrol are available from the repositories.

Holger

---

### Post by him610 on 2021-02-17
I have a monitor that has a default brightness that is absolutely too bright. I use xgamma to dim my monitor to an acceptable level.  It will adjust Red, Green, and Blue levels.

This one dims the monitor
```

xgamma -gamma 0.8 

```
This one restores to original brightness
```

xgamma -gamma 1.0 

```
This one brightens the monitor
```

xgamma -gamma 1.2

```

You can play around with the values to see which you like best. I wound up putting my final settings in a executable script that is called by my .bash_aliases file whenever I open a terminal the monitor dims.

There is note in the xgamma man file that says, "Note  that  the  xgamma  utility is obsolete and deficient, xrandr should be used with
       drivers that support the XRandr extension."
For me, xgamma works. If it is ever completely deprecated or removed, I guess I will have to figure out how to use xrandr.

---

