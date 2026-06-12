---
title: "Corrupted Graphics and Machine Lockup on Install"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by BlackHatRob on 2006-09-21
Greetings,

I am trying to install 64bit Ubuntu on my desktop at home and when it begins to load the GUI, the loader splash is corrupted and a few seconds into it, everything except the mouse is frozen solid. The keyboard stops responding but the mouse can still be moved.

If I boot using the failsafe graphics, it loads fine and installs fine, but when I try to make my display 1680x1050, the same problem occurs.

I was wondering if anyone had any ideas as to what could cause this?

-Running:
AMD64 3700
Asus A8N-SLI
Nvidia GeForce 7800 GT
2048 MiB Ram

---

### Post by BlackHatRob on 2006-09-21
bump...

I've noticed that in /etc/X11/xorg.conf if I specify my driver to be vesa, everything works fine but the resolution is limited to 1280x1024, if I switch it to nv, the resolution is able to be higher, but that's when the lockups happen

any ideas?

---

### Post by BlackHatRob on 2006-09-21
I have remedied the problem.

For any users that may have the same symptoms as me, or even if you are having graphic problems in genereral, try the following:
```

sudo nvidia-glx-config enable

```

After doing that, you will need to edit your /etc/X11/xorg.conf file and replace your current video driver (either nv or vesa) with nvidia:
```

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        VideoRam        256000
EndSection

```

And since I didn't install the nvidia-glx drivers and couldn't use them out of the box, I wonder if this might be a bug in the Ubuntu LiveCD?

Hope this helps someone...

---

