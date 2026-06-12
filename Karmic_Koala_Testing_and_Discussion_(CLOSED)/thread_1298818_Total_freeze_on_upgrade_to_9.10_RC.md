---
title: "Total freeze on upgrade to 9.10 RC"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lolwhites on 2009-10-23
I just upgraded from 9.04 to 9.10 RC. At first it worked but Compiz settings were disabled, and when I tried to enable them, the machine hung and needed REISUB to get it going again. Now it hangs whenever I log in, regardless of the account I use. I now have to use Gnome failsafe mode to log in.

Any files or settings I should post here?

---

### Post by Peter09 on 2009-10-23
Have you tried going to recovery mode and selecting the - recover your video sttings - or something similar. If than fails post the output of

```
lshw -C video
```

here

---

### Post by lolwhites on 2009-10-23
Contents of *lshw -C video*

>   *-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fea40000-fea7ffff


---

### Post by lovinglinux on 2009-10-23
It's probably a graphics card issue. Do you have nvidia card? If yes, then login from terminal or whatever and rename /etc/X11/xorg.conf and reboot. This should allow you to boot properly. Then make sure you update and install nvidia driver using jockey ( "System >> Administration >> Hardware Drivers" ). If the driver installation fail and it doesn't ask for a reboot, then you might need to install the nvidia packages ( nvidia-185-kernel-source, nvidia-185-modaliases, nvidia-glx-185 and nvidia-kernel-common ) manually from Synaptic before rebooting.

---

### Post by lolwhites on 2009-10-23
No, I use the onboard Intel chipset. I upgraded to 9.10 RC because I thought they'd resolved the graphics problems in the new release.

---

### Post by lovinglinux on 2009-10-23
> **lolwhites said:**
> No, I use the onboard Intel chipset. I upgraded to 9.10 RC because I thought they'd resolved the graphics problems in the new release.

You could try to rename xorg.conf anyway, since it looks like a graphics driver issue.

---

### Post by lolwhites on 2009-10-23
> You could try to rename xorg.conf anyway, since it looks like a graphics driver issue.

Didn't work

---

### Post by regala on 2009-10-23
> **lovinglinux said:**
> You could try to rename xorg.conf anyway, since it looks like a graphics driver issue.

it is, but renaming or unlinking xorg.conf won't change anything in the driver, which will be used anyway.
The freeze is triggered by the use of compiz, and he activated it. It's activated in his session startup config files, and he needs to prevent compiz from starting when logging in.
he needs to try looking into ~/.config/autostart/ directory in your home dir, and delete the link/file referring to compiz.desktop or whatever looks to be the culprit.
The driver is faulty, but no editing of any files, will ever be able to fix a driver bug. The OP should report it on Launchpad, this is a serious issue, as it may impact on many Ubuntu users.

---

### Post by lolwhites on 2009-10-23
I tried removing files from ~/.config/autostart/, but it still hangs. Not entirely surprising as the same happened when I logged in as another user. Worse still, I tried booting from a live USB and it still hangs!

Edit - reported on Launchpad

---

### Post by ikisham on 2009-10-23
The bug reports must be tied with a certain package. So just pick one (since we don't know exactly which is the culprit), like compiz.

If you can log in in failsafe mode, press Alt+F2 and type
```
ubuntu-bug compiz
```
and it'll take you to Launchpad.

---

### Post by lolwhites on 2009-10-23
Done. Have also purged Compiz, so I can now log in. I lose the effects, but at least I have a working system.

---

