---
title: "Cannot adjust screen brightness on laptop with Intel GM965/GL960"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flakeparadigm on 2009-08-29
I am unable to adjust the screen brightness on my laptop which has an Intel GM965/GL960 card.

In Jaunty I was able to use the command "xrandr –output LVDS –set BACKLIGHT_CONTROL native" on start up, but in Karmic it quits showing the possible ways to use xrandr.

Could anyone help me get this figured out? It's hard to use the laptop when the screen is "stuck" at full brightness.

---

### Post by eurythmia on 2009-08-31
I can ditto that. Maybe this should be submitted as a bug report?
I'm getting the error message:
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  27
  Current serial number in output stream:  27

but I've also tried using the hotkey-setup toshutils acpi-support laptop-mode and fnfxd packages, with no love.

---

### Post by andresmh on 2009-08-31
Seems like Karmic so far has regressed in terms of audio and video support. It's still August so hopefully things get better soon.

---

### Post by flakeparadigm on 2009-10-13
Anyone have any ideas?

---

### Post by Shamess707 on 2009-10-14
nvm

---

### Post by flakeparadigm on 2009-10-14
When I try the xrandr command
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
I get this:
```
tyler@tyler-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  24
  Current serial number in output stream:  24

```

The LSPCI for my graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

Any help is greatly welcome, it's hard to look at a VERY bright screen in dark areas.

---

### Post by jfernyhough on 2009-10-14
You'll likely find that from time to time kernel updates break various ACPI and power management features. Screen brightness is one of these.

You could also try adding the X-Swat PPA which has updated stable X packages and video drivers.

From this:> X Error of failed request:  BadRROutput (invalid Output parameter)it sounds like there's no display called LVDS. Again, this could be down to drivers. What does xrandr -q report?

---

### Post by flakeparadigm on 2009-10-14
xrandr -q returns this:
```
tyler@tyler-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0
   832x624        74.6
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        85.0     72.8     75.0     59.9
   720x400        85.0
   640x400        85.1
   640x350        85.1
```

I will look at the X-SWAT thing.

---

### Post by slakkie on 2009-10-14
I have the same card, and brightness is working just fine:

```

xrandr -v -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

The command below works:
```

xrandr --output LVDS --set BACKLIGHT_CONTROL native

```


FWIW

```

lsmod | grep i915
i915                  149164  1
drm                   137920  2 i915
i2c_algo_bit            4860  1 i915
i2c_core               20844  4 i915,drm,i2c_algo_bit,i2c_i801
video                  18044  1 i915

```

You might want to install the xserver-xorg-video-intel-dbg package. Maybe you'll get some additional info.

BTW, i haven't read the full thread, but the last couple of comments could be usefull to you: [http://swiss.ubuntuforums.org/showthread.php?t=1217421&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1217421&page=2)

> 
I had the same problem and fixed it easily by adding "nomodeset acpi_backlight=vendor" as sugested to the kernel line of GRUB2


---

### Post by flakeparadigm on 2009-10-14
> **jfernyhough said:**
> You'll likely find that from time to time kernel updates break various ACPI and power management features. Screen brightness is one of these.

You could also try adding the X-Swat PPA which has updated stable X packages and video drivers.

From this:it sounds like there's no display called LVDS. Again, this could be down to drivers. What does xrandr -q report?

I tried the X-Swat PPA with no luck.

---

### Post by KillerKiwi on 2009-10-14
> **flakeparadigm said:**
> I tried the X-Swat PPA with no luck.

maybe 

```
xrandr --output LVDS**1** --set BACKLIGHT_CONTROL native
```

note the 1 above

---

### Post by flakeparadigm on 2009-10-16
Already tried that one. Gives the same error as in post #2 of this thread.

---

