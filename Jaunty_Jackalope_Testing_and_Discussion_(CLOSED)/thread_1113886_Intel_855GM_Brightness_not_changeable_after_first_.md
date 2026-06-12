---
title: "Intel 855GM: Brightness not changeable after first suspend"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cywhale on 2009-04-02
Hello,

after a fresh reboot/boot of Jaunty beta changing brightness on my Acer Travelmate C110 using FN-left/right or brightness applet works fine.

However after first suspend to ram/resume I am not able to adjust the lcd brightness. Pulling AC does not result in screen dimming as intended, too. 

I'm searching for a soultion to this issue for weeks now (same issue with Arch Linux, came back to Ubuntu with Jaunty beta after one year Arch Linux) - but nothing seems to work. 

Last time brightness worked 100% for sure was with Ubuntu Gutsy (Intrepid not tested).

Driver: xf86-video-intel, Jaunty repo
Xorg: Jaunty repo, xorg.conf-device-section unchanged (default)
Kernel: Jaunty repo
```
echo <value>|sudo tee -a /sys/class/backlight/acpi_video0/brightness
```
Works fine after fresh boot, not after suspend/resume.

- unloading module 'video' did not work
- unloading module 'acerhk' did not work (didn't think so but tried)
- using 'video brightness_switch_enabled=1' in /etc/modules did not work
- using most recent Xorg/intel driver (with Arch Linux) did not help
- using Xorg 1.4 and old intel drivers did not work

This is the last issue with Linux on this little TabletPC so any help would be greately appreciated...

---

### Post by Zorael on 2009-04-02
Kernel bug? There are 2.6.29 kernel packages available at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29) if you want to give those a go.

---

### Post by cywhale on 2009-04-02
Just tried this kernel - X-display ist totally distorted so I went back to 2.6.28. Thank you for this suggestion anyway...

Edit: xrandr --output LVDS --set BACKLIGHT_CONTROL legacy does not change anything, too. Going back searching...

Edit 2: A similar bug has been filed for Debian and kernel 2.6.26 but I'm not able to find a solution: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499449]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499449")

---

### Post by marijus on 2009-04-02
you might have to disable tiling with 2.6.29 kernel to get rid of the distortion...

---

### Post by cywhale on 2009-04-02
Nope,

OPtion "ColorTiling" "false" (garbeled screen with 2.6.29) and
Option "BiosHotKeys" "true" (FN-keys/brightness changing does not work on 2.6.28 )

also do not make any difference :(

---

### Post by cywhale on 2009-04-08
I think I'll give up on this - this makes a notebook not very usable - combined with acpi_cpufreq compiled into kernel and not beeing able to save some energy via undervolting anymore...

The last options to try:
- revert to ext3 and install older kernel (not nice)
- recompile recent kernel (est. 5 hours) (does anyone know which backlight options did change between 2.6.24 and 2.6.28/29 ?), including compiling acpi_cpufreq as module, last time I tried this Ubuntu freezed after 5 hours...

---

