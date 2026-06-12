---
title: "GT 420M weird driver issues"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by 3602 on 2010-12-31
**NOTICE: Thread marked SOLVED because although no real solution is given, no real solution is available  because nVidia is not working on a driver for Optimus on Linux.**

Hello all,

I don't know whether I should open an independent post, if any Mods believe this is inappropriate then please treat it as you see fit.
Well, here's my portable computer, running Ubuntu 10.10. It has a GeForce GT 420M card.
After some of the installation issues that I went through, all the problems now seem to be with the driver in the "Additional Drivers" for the nVidia. After installing that then my Ubuntu would boot into kernel and not GUI.
The computer is a Gateway ID59C. I don't know whether this is a 64-bit computer, but it came with 64-bit Windows 7 pre-installed. I installed a 32-bit Ubuntu so maybe it's that?
Anyway. I did:
```
$ glxinfo | grep rendering
```And I got:
```
direct rendering: Yes
```However, when I do:
```
glxgears
```I see three gears, and FPS at around 59.8, 59.9 and such. 
From what I have read, a card that is properly 3D-accelerated can have numbers of this test get into the thousands. So I don't have 3D acceleration, then why is Rendering coming back as positive?
Or: Do I install the 64-bit Ubuntu and all will be well? Actually I want the driver to work so I can adjust the screen brightness. I'm stuck will full brightness as of now.
Thank you very much.

EDIT: Also the touchpad doesn't glow except during boot, but that's very minor compared to the screen.

---

### Post by grahammechanical on 2010-12-31
It may seem illogical but a 32bit OS will run fine on a 64bit processor. It is just not optimized for the processor. But try it the other way around and it won't work. Installing 64bit Ubuntu will not solve the problem.

Your problem is with the Nvidia driver. You can deactivate it. I presume that you did get into a GUI until you activated this driver. You will not have 3D desktop effects but you will have a working desktop until you can work out this problem.

Regards.

---

### Post by 3602 on 2010-12-31
> **grahammechanical said:**
> It may seem illogical but a 32bit OS will run fine on a 64bit processor. It is just not optimized for the processor. But try it the other way around and it won't work. Installing 64bit Ubuntu will not solve the problem.

Your problem is with the Nvidia driver. You can deactivate it. I presume that you did get into a GUI until you activated this driver. You will not have 3D desktop effects but you will have a working desktop until you can work out this problem.

Regards.


So the 32-bit Maverick is fine then? I won't be doing anything "Heavy Duty" with this computer anyway (all the specs are overkill, I know).
Yes, after two installations it seems that it's the driver that's bugging. If I don't activate this then it boots into GUI fine and all runs fine. Also this morning (right now) I just booted the computer and I am getting correct brightness controls. Interesting. All hail the great Tux.
I've read a couple of threads/articles regarding the nVidia driver issues. It seems like GT 420M just doesn't do well with Ubuntu? Well at least my system works (I had good times a while ago with Jaunty).

Thank you very much.

---

### Post by 3602 on 2010-12-31
> **grahammechanical said:**
> It may seem illogical but a 32bit OS will run fine on a 64bit processor. It is just not optimized for the processor. But try it the other way around and it won't work. Installing 64bit Ubuntu will not solve the problem.

Your problem is with the Nvidia driver. You can deactivate it. I presume that you did get into a GUI until you activated this driver. You will not have 3D desktop effects but you will have a working desktop until you can work out this problem.

Regards.


So the 32-bit Maverick is fine then? I won't be doing anything "Heavy  Duty" with this computer anyway (all the specs are overkill, I know).
Yes, after two installations it seems that it's the driver that's  bugging. If I don't activate this then it boots into GUI fine and all  runs fine. Also this morning (right now) I just booted the computer and I  am getting correct brightness controls. Interesting. All hail the great  Tux.
I've read a couple of threads/articles regarding the nVidia driver  issues. It seems like GT 420M just doesn't do well with Ubuntu? Well at  least my system works (I had good times a while ago with Jaunty).

Thank you very much.

---

### Post by 3602 on 2010-12-31
So the 32-bit Maverick is fine then? I won't be doing anything "Heavy  Duty" with this computer anyway (all the specs are overkill, I know).
Yes, after two installations it seems that it's the driver that's  bugging. If I don't activate this then it boots into GUI fine and all  runs fine. Also this morning (right now) I just booted the computer and I  am getting correct brightness controls. Interesting. All hail the great  Tux.
I've read a couple of threads/articles regarding the nVidia driver  issues. It seems like GT 420M just doesn't do well with Ubuntu? Well at  least my system works (I had good times a while ago with Jaunty).

Thank you very much.

---

### Post by 3602 on 2010-12-31
So the 32-bit Maverick is fine then? I won't be doing anything "Heavy  Duty" with this computer anyway (all the specs are overkill, I know).
Yes, after two installations it seems that it's the driver that's  bugging. If I don't activate this then it boots into GUI fine and all  runs fine. Also this morning (right now) I just booted the computer and I  am getting correct brightness controls. Interesting. All hail the great  Tux.
I've read a couple of threads/articles regarding the nVidia driver  issues. It seems like GT 420M just doesn't do well with Ubuntu? Well at  least my system works (I had good times a while ago with Jaunty).

Thank you very much.

---

### Post by 3602 on 2010-12-31
So the 32-bit Maverick is fine then? I won't be doing anything "Heavy  Duty" with this computer anyway (all the specs are overkill, I know).
Yes, after two installations it seems that it's the driver that's  bugging. If I don't activate this then it boots into GUI fine and all  runs fine. Also this morning (right now) I just booted the computer and I  am getting correct brightness controls. Interesting. All hail the great  Tux.
I've read a couple of threads/articles regarding the nVidia driver  issues. It seems like GT 420M just doesn't do well with Ubuntu? Well at  least my system works (I had good times a while ago with Jaunty).

Thank you very much.

---

### Post by 3602 on 2010-12-31
What's up with the multiple posts? So sorry.

---

### Post by realzippy on 2010-12-31
Think the 64 bit ubuntu will not help.Problem might be the optimus technology;do you have intel graphics also?
what is the output from:

```
lspci | grep VGA
```

---

### Post by 3602 on 2010-12-31
> **realzippy said:**
> Think the 64 bit ubuntu will not help.Problem might be the optimus technology;do you have intel graphics also?
what is the output from:

```
lspci | grep VGA
```


What I got from that was:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1)

```
So you're saying that I have an integrated chip *and* the GT 420M? I real somewhere that nVidia said that they are not developing Optimus drivers for Linux "at this time". So either A) My computer can't fully integrate Ubuntu or B) Somebody call Megatron?

---

### Post by realzippy on 2010-12-31
a and b.

If you have no "Intel/Nvidia switch" in your BIOS,bad luck.
Even worser:
As you might have noticed (battery capacity),the nvidia gpu is running,although you cannot use it.Also the nouveau driver cannot be used...

Also bought a nvidia laptop for my GF.Bad trap.

---

### Post by 3602 on 2010-12-31
I'll try booting into BIOS and see what's there.
So if there isn't said switch, then I'll have to live with it, eh (until a solution is found)?

---

### Post by realzippy on 2010-12-31
yep,waiting for at least an ugly hack
[Here]("http://linux-hybrid-graphics.blogspot.com/") you go for news ..

---

### Post by 3602 on 2010-12-31
> **realzippy said:**
> yep,waiting for at least an ugly hack
[Here]("http://linux-hybrid-graphics.blogspot.com/") you go for news ..


Although I cannot understand much of the stuff in that link (fearing another crash), thank you for providing me with it anyway.
Oh, there is no graphics card switching in BIOS. But can I still play Tux Racer? I need to try that.

---

### Post by lithopsian on 2010-12-31
This laptop is designed to automatically switch between the two graphics chips depending on the situation.  You may find that you can force the switch by changing the power saving settings.

I have no experience of this within Linux.  I imagine things would work best if you keep using the same card throughout an X server session.  You can look in /var/log/Xorg.0.log to see what X has loaded and whether it is confused.

Drivers for the Intel card (do you know exactly which one you have?) are available in Linux repositories.  The package will be xorg-xserver-video-intel or some such, possibly plus a few related things.

The glxgears speed is very low even for software rendering or non-optimal drivers.  At 60fps more or less it sounds like you are configured with vsync on and the speed is being tied to your monitor refresh rate.  Tux Racer might be a better test of the 3D graphics you have.  Bad drivers or software rendering is likely to be just a few frames a second, while either card should be able to draw at many tens of frames per second properly configured.

---

### Post by 3602 on 2010-12-31
> **lithopsian said:**
> This laptop is designed to automatically switch between the two graphics chips depending on the situation.  You may find that you can force the switch by changing the power saving settings.

I have no experience of this within Linux.  I imagine things would work best if you keep using the same card throughout an X server session.  You can look in /var/log/Xorg.0.log to see what X has loaded and whether it is confused.

Drivers for the Intel card (do you know exactly which one you have?) are available in Linux repositories.  The package will be xorg-xserver-video-intel or some such, possibly plus a few related things.

The glxgears speed is very low even for software rendering or non-optimal drivers.  At 60fps more or less it sounds like you are configured with vsync on and the speed is being tied to your monitor refresh rate.  Tux Racer might be a better test of the 3D graphics you have.  Bad drivers or software rendering is likely to be just a few frames a second, while either card should be able to draw at many tens of frames per second properly configured.

I don't know which Intel card I have. Prior to this I didn't even know I had an Intel card inside.
I don't know how to read that log file and I believe it is too long to be posted here.
On Extreme Tux Racer, Practice Run, I am getting a FPS that is constantly above 30 (I saw 46).

---

### Post by realzippy on 2010-12-31
*This laptop is designed to automatically switch between the two graphics chips depending on the situation.*

Yeah,in Windows this works;not in X...

---

### Post by 3602 on 2010-12-31
Little update: 
Earlier today I played Tux Racer at 800x600. Now I just tried at 1366x768 (max resolution), 32 bits. Although I no longer see FPS 46, I get solid values at around 29-31. Game runs finely smooth and real fast, smoother than yes, Need for Speed on PC.
I didn't turn on FSAA, not knowing what that is. Anti-aliasing?
So if I get such smooth game-play, that means my card(s) is "properly configured"? But glxgears is still Vsync at 59.9 FPS... What's up?
Unrelated side note: Got headphone jack working (didn't know it didn't work). Conexant piece of PITA.

EDIT: While Googling "glxgears", I came upon this:
[http://ubuntuforums.org/showthread.php?p=9977322](http://ubuntuforums.org/showthread.php?p=9977322)
Post #2 is exactly my problem. Seems like I'm terminated. Ah well at least Tux Racer can keep me busy.

---

### Post by 3602 on 2010-12-31
Marking thread as "SOLVED" because:
Although no real solution is given, no real solution is available because nVidia is not working on a driver for Optimus on Linux.

---

