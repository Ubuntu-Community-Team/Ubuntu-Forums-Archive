---
title: "dapper install: monitor goes into no-signal and won't come back"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by rozilla on 2006-12-24
i've been using ubuntu for like a couple of months now. i had it on an old Dell desktop. now i got a new pc:

```
Mercury PVCLE266M-L motherboard with VIA C3 CPU onboard. This motherboard integrates the VIA 

CLE266 Northbridge and 8235 Southbridge chipsets that support DDR 266MHz, Ultra DMA 

33/66/100/133 function. 

AC'97 Codec
AMI BIOS

Display adapters: VIA/S3G CLE266
Onboard VGA. Integrates a 128-bit 3D/2D graphics engine that clocks up to 133MHz decoupled 

from memory clock, and a high-performance 3D accelerator.

Samsung SV0411N 40GB harddisk and 256MB RAM
```

i put in my dapper cd and choose Start/Install ubuntu, then the installation starts. usually after all the loadings done the screen goes black and is then supposed to show the busy icon or the X icon to load the gui, right? well, in this case the screen goes black and right into that no-signal standby mode. what i mean is normally when i shutdown my pc and leave the monitor on, the LED indicator goes from steady green to blinking orange.
it's this same blinking orange i get when the gui is supposed to start loading. 

the CD-ROM drive light stays on, tho and there's activity in the drive, plus the HDD light blinks, showing that there's still stuff going on. so i don't get why my monitor pretends like my pc has just been shutdown.

i tried in safe graphics mode, and that didn't help either. same issue.

i've posted two threads on other topics here that didn't get me anywhere. but i'm hoping that this third time will be the charm :)

so please help me, if u can.

---

### Post by meng on 2006-12-24
LCD monitor I'm guessing, probably a refresh rate issue. Press ctrl-alt-f1 for a console: do you see anything?
If you know that you want to install Ubuntu (and not just take it for a spin) then use the Alternate CD to install (the installer is text-based). Then you may still have some fiddling (not much) post-install, to reconfigure the x server.

---

### Post by rozilla on 2006-12-26
damn that was silly of me to talk about a monitor problem and not mention the monitor LOL

it's not an LCD. it's a normal 15" AMAX AMM-1502. 

Dot pitch: 0.28mm
Freq: 50/60Hz
Power: 70W
HScan: 30-56kHz
VScan: 50-85kHz
Max res: 1024x768

but i'll try CtrlAltF1, too

---

### Post by harrington on 2006-12-27
I am having the same problem with my LCD monitor!! It goes into stanby right before it loads up, I am new and I need basic instructions on how to resolve this monitor issue... PLEASE HELP

---

### Post by glasscleaner on 2006-12-27
same problem here

6600GT AGP with a Acer AL2016W

the same problem with my Acer AL1715

i can see the console when i hit ctrl-f1, but i dont know what to reconfigure

---

### Post by rozilla on 2006-12-27
exactly. i hit CtrlAltF1 and get the linux prompt. what do i do to get the installation going again from there? and is there a way i can switch to X from the CtrlAltF1 console?

---

### Post by glasscleaner on 2006-12-29
ctrl-f7


let me know if you found a way to fix that

---

