---
title: "Lates update nvidia driver, now get 60 fps from glxgears, was 3500."
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-04-02
Not good.

---

### Post by glasen on 2009-04-02
1. "glxgears" is not a benchmark!

2. Check if VSYNC is enabled!

---

### Post by fooman on 2009-04-02
same here...been like that for the last 2-3 drivers (while using intrepid) for me.  upgraded to jaunty last week,  installed the manual way and still the same 60fps

8800gt....manual install x-86_64-180.44

apart from the low glxgears....everything else seems to be working fine.

---

### Post by Therion on 2009-04-02
> **glasen said:**
> 1. "glxgears" is not a benchmark!

2. Check if vsync is enabled![color="white"].
.[/color]
**[indent]! ! ![/indent]**
[color="white"].
.[/color]

---

### Post by philinux on 2009-04-02
> **glasen said:**
> 1. "glxgears" is not a benchmark!

2. Check if VSYNC is enabled!

Explain?

I know its not a benchmark but 3500 to 60 is.
Same result with compiz off.

---

### Post by philinux on 2009-04-02
Just rebooted again.

Noe get 9000 fps with compiz off
3500 with it on. Weird.

---

### Post by Eclipse. on 2009-04-02
Turn "Sync to VBlank" off and you will get the results your looking for.Glxgear is not a benchmarking tool though like has been already said.

---

### Post by glasen on 2009-04-02
> "VSYNC"

Sorry, i meant "Sync to VBlank". :oops: :oops:

---

### Post by philinux on 2009-04-02
Turning that off makes no diff. already got 3800fps from reboot.

---

### Post by psyke83 on 2009-04-02
> **philinux said:**
> Turning that off makes no diff. already got 3800fps from reboot.

If you see a FPS rate of 60, 70, 75, 80 or a rate compatible with your monitor's refresh rate, then it's almost always due to VSync being enabled. There is *no* performance regression; instead, the application is restricting the amount of frames displayed to the amount your monitor can display each second. This has the advantage of eliminating horizontal tearing in applications.

In other words, it's a minor configuration issue that can be solved via nvidia-settings (in the OpenGL section, not the video playback section).

---

### Post by kodiakmax on 2009-04-02
I think everyone knows glxgears is not a benchmark by now.  However, when you see a drop of -2000 something is wrong lol.

As a side note you can use Furmark via wine as an opengl benchmark.  I get similar results when run natively through windows.  It is actually faster in linux lol.

---

