---
title: "seeking video details for &quot;external&quot; display"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2010-09-20
Folks,
    If I use **xdpyinfo** I see details for the internal display for my laptop. 

[highlight]Q1:[/highlight] Where do I find the details for the "external monitor" port so that I might connect a reasonable projector or monitor? 

[highlight]Q2a:[/highlight] Do those details exist only AFTER I connect something? [highlight]Q2b:[/highlight] Are there risks if the external something doesn't match up with what the video port supports? [highlight]Q2c:[/highlight] Are there risks to the laptop presented by whatever external something I connect?

Merci d'avance,
~~~ 0;-Dan

---

### Post by uRock on 2010-09-21
What you are able to connect to is dependent on the video card. If you are refferring to a laptop with an RCA video output, it should work with any monitor/projector that has an RCA in for video. 

I don't think connecting any monitor into a video port will harm either the monitor nor the PC, the device most likely just won't work.

I have connected my laptop to a 50" plasma and watched Netflix as well as connecting it to the school's projector to run a slide show for a HW assignment. For the most part, if it connects then it should work.

---

### Post by SaintDanBert on 2010-09-22
My laptop has a female DB15 connector -- two actually: one on the laptop and one on the docking station.

**lspci** reports
```

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

**xdpyinfo** reports (about the built-in LCD display)
```

dimensions:    1400x1050 pixels (245x184 millimeters)
resolution:    145x145 dots per inch
depths (7):    24, 1, 4, 8, 15, 16, 32

```

Are modern monitors suitably "multi-sync" such that they will discover what my port is saying and work with it ... or give up?

My readings tell me there are numerous tricks to get **dual display** to work with X11. Is there some way to create a static default config for 1024x768 for a second display?

I'm using Jaunty (v9.04) on one box and Lucid (v10.04 LTS) on the others. It looks like config steps are wildly different between them.

Merci,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-09-22
Bump 8d;-{

---

### Post by efflandt on 2010-09-22
With Intel (or ATI) video chips, I believe if you boot with an external display connected, the BIOS automatically switches to the external display (but nVidia does not).  But when Ubuntu X starts, it tries to mirror both displays in a resolution that it thinks both can handle.  But Linux is not always able to determine details of a VGA display, so it is not necessarily automatically optimum resolution for either display.

If you connect an external display after booting, a quick way to get X to recognize that it is there is to log out of X and back in (no need to power down, just out and back into X).

For example if I boot my laptop with Intel video, Ubuntu picks 1024x768 for both, even though laptop display is 1280x800 and external VGA might be 720p or 1080p HDTV.

So I use a script of xrandr commands to set a proper resolution for external display, turn off my laptop display, and activate the external display.  And the script runs with one or two clicks by either putting a launcher in the top panel, or on the desktop.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

