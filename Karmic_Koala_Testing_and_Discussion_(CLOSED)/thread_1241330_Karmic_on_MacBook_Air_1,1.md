---
title: "Karmic on MacBook Air 1,1"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kosumi68 on 2009-08-15
With the recently released Alpha 4, Karmic is approaching a state of general usefulness, and here is a first stab at making it work on my MacBook Air 1,1. Until today it was running Intrepid almost flawlessly, and the Karmic development will be logged at the community help pages ([https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)).

UPDATE 22AUG2009:

Karmic is now on par with Intrepid, the initial larger regressions either being solved or worked around. The lingering issues are basically two:

* Although there are several workarounds, the keyboard backlight functionality is hanging, there currently being no clear path as how to integrate it with the gnome desktop.

* The microphone is still not working, but it never did on this machine.

[I]
OUTDATED INFORMATION BELOW:

The first impression of Karmic is that there is a considerable amount of regression going on. Here is a list of things that used to work, but does not currently. Perhaps some of these problems have been resolved during the Jaunty cycle?

**Suspend/resume**
 
The kernel (2.6.31) has gotten a lot of cleanup regarding suspend/resume, and as a result, suspend to ram, which has been working well since the Hardy days, does not work. The computer hangs on suspend, although there seems to be some progress coming in the next kernel version (-rc6), which suspends but instead does not come up again.

**LCD backlight**

With ubuntu slowly moving away from hal in favor of the devicekit suite, the LCD backlight functionality seems to have been left out in the cold. Which route to take to make this work is somewhat unclear, but using the kernel backlight support seems fairly straight-forward. Now we only need to find a way to map the keys... ?

**Keyboard backlight**

Just as for LCD backlight, the keyboard backlight functionality suffers from the HAL deprecation. However, there are plenty of possiblities to make this work using the sysfs kernel filesystem. Again provided a way to map the keys.

**IR remote**

In intrepid this worked out-of-the box thanks to the appleir module, which has since then been removed from the distribution. I do not know where to begin with this one. Any suggestions?

Apart from these regressions (and the microphone not working, but it never did), everything seems to work as well or better than it did in Intrepid. Yay.
[/I]

---

### Post by kosumi68 on 2009-08-16
The LCD backlight issue can be resolved in two ways:

1. Add the "nomodeset" boot option. This tip was taken from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/397617](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/397617). Simply edit the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub, and run "sudo update-grub". Viola, F1/F2 works again. However, the brightness scale is rough (see [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/289520](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/289520)).

2. Install good ol' pommed. This option actually has some virtues while X is not grabbing the F1/F2 keys. It works also in text consoles, and the brightness scale is much smoother. Only problem seems to be that pommed consumes a lot of cpu. It seems pommed is capturing too many unrelated events (ambient light). Oh, and pommed makes keyboard backlight work too. :-)

---

### Post by kosumi68 on 2009-08-16
There is now a pommed package for karmic in the Mactel PPA, with changes to reduce the cpu consumption. Patches sent to Julien, the maintainer.

---

### Post by kosumi68 on 2009-08-16
A patched version of gnome-power-manager yielding smoother brightness, especially at low brightness levels, is now available in the Mactel PPA. The patch is attached here as well.

---

### Post by _mario_ on 2009-08-17
> **kosumi68 said:**
> A patched version of gnome-power-manager yielding smoother brightness, especially at low brightness levels, is now available in the Mactel PPA. The patch is attached here as well.

(welcome back, wherever you've been.)

thanks. this is great. i always hated gnome-power-manager for scaling 1024 levels offered by my nvidia_bl driver down to 20. however, since i need my machine for everyday work, i don't want to upgrade to karmic right now (maybe in a month). can you please also upload a fixed package for jaunty as well if it's not too much work.

in addition, an idea i had in my mind for a while: is it possible to use 2 different step sizes? i mean: larger steps by pressing BRIGHTNESS_UP / BRIGHTNESS_DOWN and half the step size by pressing Shift + BRIGHTNESS_UP / Shift + BRIGHTNESS_DOWN. if i'm remembering correctly, this is what OSX does. is it possible with gnome-power-manager, too?

ciao,
Mario

---

### Post by kosumi68 on 2009-08-17
> **_mario_ said:**
> 
thanks. this is great. i always hated gnome-power-manager for scaling 1024 levels offered by my nvidia_bl driver down to 20. however, since i need my machine for everyday work, i don't want to upgrade to karmic right now (maybe in a month). can you please also upload a fixed package for jaunty as well if it's not too much work.


When looking at the gnome-power-manager_2.24.2-2ubuntu8 package, which seems to be the current package for Jaunty, it seems the mactel fixes are already in there. What package version are you using?

---

### Post by _mario_ on 2009-08-17
> **kosumi68 said:**
> When looking at the gnome-power-manager_2.24.2-2ubuntu8 package, which seems to be the current package for Jaunty, it seems the mactel fixes are already in there. What package version are you using?

i'm using gpm 2.24.2-2ubuntu8. but maybe i misinterpreted your previous posts a bit. i don't observe the effect of 20000 brightness calls freezing gpm at startup as described in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/289520") (you linked above).

i'm complaining about the step size in general: if the driver supports 1024 levels, gpm uses a step size of 51 to give 20 levels to the user. but it's minimum level 51 is still too bright in dark environments.

or did you really patch gpm to use exponentially increasing step sizes? (which would be nice.)

ciao,
Mario

---

### Post by kosumi68 on 2009-08-17
> **_mario_ said:**
> i'm using gpm 2.24.2-2ubuntu8. but maybe i misinterpreted your previous posts a bit. i don't observe the effect of 20000 brightness calls freezing gpm at startup as described in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/289520") (you linked above).

i'm complaining about the step size in general: if the driver supports 1024 levels, gpm uses a step size of 51 to give 20 levels to the user. but it's minimum level 51 is still too bright in dark environments.

or did you really patch gpm to use exponentially increasing step sizes? (which would be nice.)

ciao,
Mario

The bug describes one problem we had with intrepid, but the patchset in .24.2-2ubuntu8, the official jaunty version, contains several other patches in addition; basically all patches I made for intrepid in mactel seems to be present. The brightness stepping strategy I implemented is non-linear, yielding a geometric progression of the step size from zero up to full brightness. But it is for the XRandR method only. I guess you have the nvidia graphics with no xrandr support, so running the via-hal-to-/sys/backlight method?

---

### Post by kosumi68 on 2009-08-17
Suspend/Resume: I managed to finally both suspend and resume using the linux v2.6.31-rc6 kernel, so chances are good the regression will be gone after the next rebase of the ubuntu kernel (presumably Ubuntu-2.6.31-7). :-)

---

### Post by kosumi68 on 2009-08-17
Remote Control: the method of choice is LIRC. Simply install the lirc package. It is possible to setup the lircd daemon to inject configured key codes into X, thereby simplifying matters considerably if you only want the keys of your remote to become an extension to your keyboard. :-)

For details, see the IR remote section of [https://help.ubuntu.com/community/MacBookAir1-1/Karmic](https://help.ubuntu.com/community/MacBookAir1-1/Karmic)

---

### Post by _mario_ on 2009-08-18
> **kosumi68 said:**
> The brightness stepping strategy I implemented is non-linear, yielding a geometric progression of the step size from zero up to full brightness. But it is for the XRandR method only. I guess you have the nvidia graphics with no xrandr support, so running the via-hal-to-/sys/backlight method?

yep. it's an nvidia graphics adapter. why can't this strategy applied to the hal method as well?

ciao,
Mario

---

### Post by kosumi68 on 2009-08-22
Suspend/Resume: Solved

Apparently, having quirks for the usbhid module somehow disrupts the suspend flow. I used to have those for intrepid. One can search for quirks with
```

modprobe -c | grep usbhid

```
If anything with the name quirks shows up, go to /etc/modprobe.d and find the file which contains the line, comment or remove it. Then update
```

sudo depmod -a
sudo update-initramfs -u -v -k `uname -r`

```

---

### Post by kosumi68 on 2009-08-25
> **_mario_ said:**
> 
[...]
i always hated gnome-power-manager for scaling 1024 levels offered by my nvidia_bl driver down to 20.
[...]


Are we talking about drivers/video/backlight/mbp_nvidia_bl.c? Isn't that driver limited to 16 levels?

---

### Post by _mario_ on 2009-08-26
> **kosumi68 said:**
> Are we talking about drivers/video/backlight/mbp_nvidia_bl.c? Isn't that driver limited to 16 levels?

it is. but i wrote a better driver for machines incorporating Nvidia graphics (nvidia_bl), which supports up to 1024 levels.

---

### Post by kosumi68 on 2009-08-26
Oh I see. I always thought it was the same driver. To answer your question about scaling, there is nothing to prevent such an implementation. However, it might not be needed; have you checked out the kernel control method for xrandr?

```

xrandr --output LVDS --set BACKLIGHT_CONTROL kernel

```

This instructs the xrandr code to use the sysfs interface. The implementation might not work on your x driver, I could not say, but it works on my intel graphics machine (after patching xserver-xorg-video-intel to recognise the mpb_backlight sysfs interface).

---

### Post by _mario_ on 2009-08-27
> **kosumi68 said:**
> Have you checked out the kernel control method for xrandr?
```

xrandr --output LVDS --set BACKLIGHT_CONTROL kernel

```


unfortunately:
```

> xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
X Error of failed request:  174
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  19
  Current serial number in output stream:  19

```

i assume this is due to the Nvidia X driver not implementing the Xrandr 1.3 extension. afaik intel does. is this feature Xrandr 1.3 specific?

ciao,
Mario

---

### Post by kosumi68 on 2009-08-27
Ok, so no luck there. I can't find a single trace of the kernel method in the xserver-xorg-video-nv package. I don't know when this feature appeared in the xrandr specification, but apparently it is not ubiquitous yet.

---

