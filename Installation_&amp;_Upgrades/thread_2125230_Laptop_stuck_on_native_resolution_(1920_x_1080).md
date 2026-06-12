---
title: "Laptop stuck on native resolution (1920 x 1080)"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by ABitTooSpicy on 2013-03-13
Upgraded: from 11.10 to 12.04 (32bit)
Laptop: Lenovo w520
Nvidia Driver version: 304.64

I just upgraded from 11.10 to 12.04 and I can no longer change my resolution. My laptop is a Lenovo w520, Nvidia X Server Settings reports 1920 x 1080 as the only option. Which is normally fine but doesn't work when I connect to a projector with lower resolution, as cloning only clones part of the screen to the projection and presentations look pretty messed up! :(

This used to work fine with 11.10 not sure what changed...

Tried a fix I found for a similar issues but it did not work. I used the nvidia X server-settings, saved configuration to X file to create an xorg.conf file. I then added the following line (Option "ModeValidation" "AllowNonEdidModes") to the devices section. This now makes many other resolutions available however none of them work properly. I end up with my desktop duplicated multiple times on the screen anytime I change resolution... 

Please HELP! :)

(PS. I also posted this on [http://askubuntu.com/questions/265594/laptop-stuck-on-native-resolution-1920-x-1080](http://askubuntu.com/questions/265594/laptop-stuck-on-native-resolution-1920-x-1080) but since I didn't get a response I thought I would try here... hope that is ok!)

---

### Post by TK999 on 2013-03-13
Hi! Are you using the **nouveau **open source driver or the **nvidia **proprietary driver? If the former, please run the following command from a terminal:
```

dmesg | grep nouveau

```
and post the results here. Thanks!

---

### Post by ABitTooSpicy on 2013-03-13
> **TK999 said:**
> Hi! Are you using the **nouveau **open source driver or the **nvidia **proprietary driver? If the former, please run the following command from a terminal:
```

dmesg | grep nouveau

```
and post the results here. Thanks!

I am pretty sure I am using the proprietary nvidia drivers:

When I go to the additional drivers section. I see the selected option for "NVIDIA accelerated graphics driver (post-release updates) (version current-updates)"

So ```
 dmesg | grep nouveau 
``` doesn't return anything, but replacing nouveau with nvidia returns the following:

```

admin@admin-w520:~$ dmesg | grep nouveau
admin@admin-w520:~$ dmesg | grep nvidia
[    6.305200] nvidia: module license 'NVIDIA' taints kernel.
[    6.361024] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    6.361030] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    6.361037] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.361045] nvidia 0000:01:00.0: setting latency timer to 64

```

---

### Post by TK999 on 2013-03-13
Try to have nvidia automatically detect your monitor setup. Connect the projector and run the following from a terminal:
```

sudo nvidia-xconfig --twinview

```

---

### Post by ABitTooSpicy on 2013-03-13
No luck:
```

admin@admin-w520:~$ sudo nvidia-xconfig --twinview
nvidia-xconfig: unrecognized option: "--twinview"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.

```

---

### Post by TK999 on 2013-03-13
What does
```

xrandr -q

```
output when running it?

---

### Post by ABitTooSpicy on 2013-03-13
The Twin View option is grey in the GUI as well (Nvidia X Server Settings). However it is enabled once I enable the 2nd monitor (in this case I am testing with a 2nd Dell monitor)

The projector goes to extend mode instead of clone. When I try to clone only a part of the screen is cloned.

---

### Post by ABitTooSpicy on 2013-03-13
xrandr -q returns the following:

```

Screen 0: minimum 8 x 8, current 3200 x 1080, maximum 16384 x 16384
VGA-0 connected 1280x1024+1920+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1920x1080      59.9  
   1680x1050      59.9  
   1440x900       59.9  
   1400x1050      60.0  
   1360x768       60.0     59.8  
   1280x960       60.0  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.0     70.1     60.0  
   960x600       120.0  
   960x540       120.0  
   840x525       139.8    120.0    119.8  
   832x624        74.6  
   800x600        75.0     72.2     60.3     56.2  
   720x450       119.8  
   700x525       149.5    120.0  
   680x384       119.9    119.6  
   640x480        75.0     72.8     59.9  
   512x384       140.1    120.0  
   400x300       144.4  
   320x240       145.6    120.1  
LVDS-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080      60.0*+   59.9     50.0  
   1680x1050      59.9  
   1400x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   960x540       120.0  
   840x525       120.0    119.8  
   700x525       120.0

```

---

### Post by ABitTooSpicy on 2013-03-13
Anyone have any ideas?? :confused:

---

### Post by TK999 on 2013-03-14
Without "extend" or "clone" selected, does
```

xrandr --output VGA-0 --mode 1920x1080

```
help?

---

### Post by ABitTooSpicy on 2013-03-15
> **TK999 said:**
> Without "extend" or "clone" selected, does
```

xrandr --output VGA-0 --mode 1920x1080

```
help?

Tells me mode not found:
```

xrandr: cannot find mode 1920x1080

```

Which makes sense as the external display only goes up to 1280x1024. I changed the command to have that resolution instead and it did the same thing as clone (where part of my laptop screen doesn't show up on the external display).

sigh... i really need to figure this out or else i have to go back to windows... arg!! :(

---

### Post by ABitTooSpicy on 2013-03-15
Ok I think I might have found something that could potentially help... I'm closer, just not there 100%...

I found a command line option that lets me change the resolution to my laptop:
```

nvidia-settings --assign CurrentMetaMode="LVDS-0: nvidia-auto-select @1280x1024 +0 +0 {ViewPortIn=1280x1024, ViewPortOut=1440x1080+240+0}, DVI-I-0: nvidia-auto-select @1280x1024 +0 +0"

```

However if I try to clone or change the resolution on the external monitor VGA-0, then the laptop LVDS-0 goes back to the default 1920x1080.** Is there a way for me to do the nvidia-settings --assign command that lets me hit both displays in one shot instead of having to do them one at a time?**

I'm so close I can feel it!!!...

---

### Post by ABitTooSpicy on 2013-03-15
> **ABitTooSpicy said:**
> Ok I think I might have found something that could potentially help... I'm closer, just not there 100%...

I found a command line option that lets me change the resolution to my laptop:
```

nvidia-settings --assign CurrentMetaMode="LVDS-0: nvidia-auto-select @1280x1024 +0 +0 {ViewPortIn=1280x1024, ViewPortOut=1440x1080+240+0}, DVI-I-0: nvidia-auto-select @1280x1024 +0 +0"

```

However if I try to clone or change the resolution on the external monitor VGA-0, then the laptop LVDS-0 goes back to the default 1920x1080.** Is there a way for me to do the nvidia-settings --assign command that lets me hit both displays in one shot instead of having to do them one at a time?**

I'm so close I can feel it!!!...

FIGURED IT OUT!!  :-D

```

nvidia-settings --assign CurrentMetaMode="LVDS-0: nvidia-auto-select @1280x1024 +0 +0 {ViewPortIn=1280x1024, ViewPortOut=1280x1024+240+0}, VGA-0: nvidia-auto-select @1280x1024 +0 +0"

```

I realized that xrandr was showing my 2 displays as LVDS-0 and VGA-0 and I was putting in DVI... so obviously it wouldn't work! Hopefully this helps someone else as well! =)

---

