---
title: "Reasons why I love Wine in Jaunty..."
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tom Mann on 2009-03-31
:popcorn:

---

### Post by Eisenwinter on 2009-03-31
ok, so you can run a game on it.

---

### Post by Rokurosv on 2009-03-31
Can you play The Witcher on it ? O_o

---

### Post by Moustacha on 2009-03-31
How well does it run though? :S

---

### Post by ghindo on 2009-03-31
What sorta hardware are you running?

---

### Post by Tom Mann on 2009-03-31
Not any game,  my current addiction, Left 4 Dead :)

I'm on an X2 6400+ with 9600GT, it's a little choppy but playable with no configuration (works nicely in full screen too) with compositing on. Sure it should run quicker, but this should mark the death of Windows.

@Eisenwinter: A year ago this would never have worked...
@Rokurosv: I had the understanding The Witcher had a Linux client?

---

### Post by darthmob on 2009-03-31
I'm still hoping that the rumours are true and Valve is porting the source engine to linux. on release I would immediately buy the ultimate pack with all games. :)

PS: why is it running choppy? it should be running at steady <insert pretty high fps value> with your hardware!

---

### Post by ghindo on 2009-03-31
It's probably choppy because he has compositing enabled...

---

### Post by Tom Mann on 2009-03-31
> **ghindo said:**
> It's probably choppy because he has compositing enabled...

Indeed, I haven't switched it off yet, I'll try to find the command line for the game tonight and give a Windows/Wine with Compositing/Wine without compositing FPS value tonight.

---

### Post by Naz_Farooq on 2009-03-31
How did you do that?
Is it possible in ubuntu 8.10?

---

### Post by Mehall on 2009-03-31
> **Naz_Farooq said:**
> How did you do that?
Is it possible in ubuntu 8.10?

Should be. It'll depend on your version of wine, not on your version of Ubuntu, and you can just add the official Wine repo to get the latest version.

(Though I'm getting 111 errors from the Intrepid repo just now. :/ That's Connection Refused for anyone not in the know.)

---

### Post by Tom Mann on 2009-03-31
Ouch! 10fps in Linux @ 1680x1050...

That said I think I may have a configuration problem with my GFX card, as my youtube videos stutter too (Ubuntu 64bit, Flash 10 64Bit)

60fps locked in Windows - guess it's cause I have VSync on...

I'm going to play with Wine tonight see if I can run it any faster.
([http://www.winehq.org/download/deb](http://www.winehq.org/download/deb))

---

### Post by tdrusk on 2009-03-31
I love how WINE keeps getting better. I can't wait until I can run everything in it.

---

### Post by Mehall on 2009-03-31
> **tdrusk said:**
> I love how WINE keeps getting better. I can't wait until I can run everything in it.

They're doing good with DirectX 10.

Yeah, WINE will support Dx10, and XP doesn't xD

---

### Post by Tom Mann on 2009-03-31
I agree... I've just found out I was running Wine 1.0.1 (Jaunty has Wine 1.0.1?) Installed 1.1.18 from the offical repo and increased my framerate. It still shudders sometimes but it's a lot better. Plus I added ```
Option "RenderAccel" "True"
``` to xorg.conf and it's smooth too!

This is actually quite playable now! :)

@tdrusk: As long as they don't emulate any spyware...

---

### Post by Mehall on 2009-03-31
The reason why Jaunty has 1.0.1 (same as Intrepid) is because that's the official "stable" version, and the newer ones are officially "testing".

First thing I do is add the wine repo, even if I don't think I'll be adding wine on a PC. just simpler.

---

### Post by wingnux on 2009-03-31
I installed L4D yesterday here but it ran pretty slow, I guess my hardware isn't good enough to run it trhough wine but it installed and ran flawlessly btw! =)

---

### Post by Polygon on 2009-03-31
i'll stick with windows for my videogames, though its cool that it works.

---

### Post by Tom Mann on 2009-04-01
I'm well impressed with Wine now - I found a bug report on WineHQ so I'llbe watching that carefully.

I will try and turn film grain off in left4dead's settings tonight - see if it makes a difference...

---

### Post by Naz_Farooq on 2009-04-01
thanks a lot. but there is something wrong. whenever i try to import files from my windowsXP c:/ drive, it shows only "iexplorer" and nothing else. I want to run other exe* files but it is not showing anything. only notepad is there to run, why can I not install other programmes from WindowsXP c:/ drive

---

### Post by pt123 on 2009-04-01
so what frame rate are you getting with wine 1.18

---

### Post by Naz_Farooq on 2009-04-01
> **pt123 said:**
> so what frame rate are you getting with wine 1.18

Would you mind telling me where to check "frame rate"

---

### Post by ruik on 2009-04-01
> **Naz_Farooq said:**
> thanks a lot. but there is something wrong. whenever i try to import files from my windowsXP c:/ drive, it shows only "iexplorer" and nothing else. I want to run other exe* files but it is not showing anything. only notepad is there to run, why can I not install other programmes from WindowsXP c:/ drive

Do not try to run anything from your Windows drive, it probably won't work. If you want to use WINE, (re)install your programs with it.

---

### Post by ruik on 2009-04-01
> **Tom Mann said:**
> @tdrusk: As long as they don't emulate any spyware...

If it runs in Windows, it will (eventually) run in WINE too.

---

### Post by Naz_Farooq on 2009-04-01
> **ruik said:**
> do not try to run anything from your windows drive, it probably won't work. If you want to use wine, (re)install your programs with it.

thanks. But will "wine" show dvd rom drive & programmes in it.

---

### Post by Tom Mann on 2009-04-01
Wine will see anything Linux can; it is not an emulator, but an emulation layer.

I'm getting around 20fps, but strangely it feels like more...
I'm going to turn off vsync and see if it helps.

---

### Post by GARoss on 2009-04-01
Any progress with installing Net Framework 3.0 with WINE? My video editing software & probably lots of gaming software is dependant on it.

---

