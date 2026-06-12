---
title: "Resolution too Big"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Torri on 2009-11-13
I just installed Xubuntu after trying Ubuntu, which ran slow and kept freezing. Xubuntu seems better, but I'm having a problem with the resolution being too large for the screen. I had the same problem in Ubuntu. I found [this thread ]("http://ubuntuforums.org/showthread.php?t=1249829&highlight=resolution+gateway")that talks about the problem, but when I tried the solution given, it didn't work. I'm working on an oldish Gateway 3215 laptop.
 
This is my very first time on Linux, so I feel like a preschooler dumped in with a bunch of college kids! I'm sure I'm doing something wrong, but I have no idea what. Help???

---

### Post by kerry_s on 2009-11-13
on the specs it only says 14", so i'm going to assume it's suppose to be 1024x768.

press: **alt+f2**
type: **gksudo mousepad /etc/X11/xorg.conf**
add to the screen section:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
[B]	SubSection "Display"
	Modes		"1024x768"
	EndSubSection[/B]
EndSection
```

log out & back in

---

### Post by Torri on 2009-11-13
Oh no, I tried that and now I can't get back to my desktop. I logged out and tried to get back in, and it's stuck at [EMAIL="name@name-laptop:~$"]name@name-laptop:~$[/EMAIL] ??? what does that mean?

---

### Post by audiomick on 2009-11-13
Torri, don't panic. Your x-server is broken. I'm sorry I can't tell you how to fix it, but I can tell you, all is not lost.

---

### Post by Torri on 2009-11-13
My x-server? I'm embarrassed to not know what that is. I knew the learning curve was steep on this but man, it's like I've never seen a computer before.
 
Maybe I should just reinstall the os. Anyone know how to fix this?

---

### Post by kerry_s on 2009-11-13
> **Torri said:**
> My x-server? I'm embarrassed to not know what that is. I knew the learning curve was steep on this but man, it's like I've never seen a computer before.
 
Maybe I should just reinstall the os. Anyone know how to fix this?

type: **sudo dpkg-reconfigure -phigh xserver-xorg**
type: **sudo reboot**

you'll be right back where you started.

---

### Post by Torri on 2009-11-13
I tried this, but it took me right back to name-laptop login, which takes me back to [EMAIL="name@name-laptop:~$"]name@name-laptop:~$[/EMAIL] . 
 
Any other ideas?
 
> **kerry_s said:**
> type: **sudo dpkg-reconfigure -phigh xserver-xorg**
type: **sudo reboot**
 
you'll be right back where you started.

---

### Post by audiomick on 2009-11-13
hallo.
The x-server is the bit that translates between what is happening inside and what you see on the screen.

[http://en.wikipedia.org/wiki/X_window_system](http://en.wikipedia.org/wiki/X_window_system)

If it is not running, you get a black screen with a cursor; what you described. It is a distinct advantage over windows, that the computer is, at this stage, not broken forever. If you know what you are about, you can still use it in this state. 

However...

You said you had just installed. If that is the case, and there is nothing on the computer you would lose, you may as well re-install now. You will then be back where you started, with the big resolution.

Kerry_s was probably on the right track. Probably, the x-server ( there it is again... ) is not dealing with your screen properly. What Kerry told you to do should have forced the x-server to use a configuration that matched your screen. I can't help you too much further, the last time I had to do with this was about 4 years ago, and I've forgotten it all again. Try searching the forums using your laptop model name as the search term. That is how I solved my problems in this regard.

---

### Post by Torri on 2009-11-13
Okay, I'm reinstalling. I haven't found a thread yet that deals with the resolution issue for this laptop, but I found a couple that are similar. Maybe they will work. What's the worst than can happen at this point? I will just have to reinstall again. (This is #4).
 
Some of the threads say to download the drivers, but Xubuntu's not recognizing my Wireless either.

---

### Post by Torri on 2009-11-13
And thanks for the x server explanation. :) That helps.

---

### Post by Torri on 2009-11-13
Allright, I have reinstalled.
 
I found a couple threads on this for similar systems, but their suggestions didn't seem to work. I think I am going to have to get my internet working first, so I can get the driver for the video card. I think.
 
It does not find my network at all. I tried updating the driver through the applications (ndiswrapper), but it said it couldn't for my computer. Any ideas?

---

### Post by Torri on 2009-11-14
Anyone have any ideas? I tried installing Zenwalk instead, but it had the same problem. Worse, actually, because I couldn't even get past the login screen due to the resolution.
 
I'm still hoping to get Xubuntu to work. If anyone has any other ideas about how to fix the resolution without the drives (still no wireless), that would be awesome.

---

