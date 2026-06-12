---
title: "Monitor doesn't like Ubuntu splash/bargraph screen"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by hbquikcomjamesl on 2010-02-11
Now that I've got GRUB fixed on my box, and I've almost got a GRUB background screen up, I have another problem:

When the Ubuntu bar-graph splash screen comes up, my fairly new ViewSonic LCD monitor blanks with an "out of range" message.

Plugging in a handy CRT monitor gives me a horizontal frequency of 46.2 kHz, and a vertical frequency of 86.5 Hz, resolution unknown.

Once the normal screen comes up, the horizontal frequency is 67.7 KHz, and the vertical is 74.8 Hz, resolution 1152x864 (I don't think that's the native resolution of the monitor).

How do I either make the splash screen come up in a way the monitor likes (the live CD boot looks just fine!), or disable it entirely?

---

### Post by hbquikcomjamesl on 2010-02-12
Good news: I figured out how to suppress the bargraph/splash screen entirely.

But can it be set to a refresh rate the monitor can handle? The maximum rated vertical frequency is 85Hz.

Native raster is 1280x1024

---

### Post by ironclaw on 2010-02-12
> **hbquikcomjamesl said:**
> Now that I've got GRUB fixed on my box, and I've almost got a GRUB background screen up, I have another problem:

When the Ubuntu bar-graph splash screen comes up, my fairly new ViewSonic LCD monitor blanks with an "out of range" message.

Plugging in a handy CRT monitor gives me a horizontal frequency of 46.2 kHz, and a vertical frequency of 86.5 Hz, resolution unknown.

Once the normal screen comes up, the horizontal frequency is 67.7 KHz, and the vertical is 74.8 Hz, resolution 1152x864 (I don't think that's the native resolution of the monitor).

How do I either make the splash screen come up in a way the monitor likes (the live CD boot looks just fine!), or disable it entirely?

Edit /boot/grub/menu.lst as the root user and look for the line beginning with
```
# defoptions=
```
and remove 'splash' and 'quiet' from that line.

Then run
```
sudo update-grub
```

That should disable the splash screen during boot up, and display text instead.

Alternatively, I think you can look at adding vga=xxx (where xxx is a 3 digit code) to defoptions to tell Ubuntu to boot up in a specific resolution.

---

### Post by ironclaw on 2010-02-12
> **hbquikcomjamesl said:**
> Good news: I figured out how to suppress the bargraph/splash screen entirely.

But can it be set to a refresh rate the monitor can handle? The maximum rated vertical frequency is 85Hz.

Native raster is 1280x1024

If the problem is from an unsupported resolution, you can try putting defoptions=vga=795 in menu.lst. That puts the resolution during boot up to 1280x1024.

---

### Post by hbquikcomjamesl on 2010-02-12
The biggest problem is the 86.5 Hz.

Something else: I've put in a GRUB splashimage file, and a corresponding line in the menu.lst file, but I get an error message to the general effect that it can't load the file.

I followed the instructions to the letter, from the number of colors to the type of file (including GZIPping it), but all I get is an error message.

---

