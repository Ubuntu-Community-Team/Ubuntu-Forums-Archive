---
title: "gtk-recordmydesktop issues with opensource radeon drivers"
date: 2009-12-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-12-31
First i did a search and there was no thread on lucid regarding this issue

Fullscreen screencasting on my phenom2 x3 gives crappy output both compiz enabled and disabled but on metacity the live preview isn't bad but the output is

[http://depositfiles.com/files/6uetozz3j](http://depositfiles.com/files/6uetozz3j)

Can anyone confirm this?

---

### Post by n3had on 2010-01-01
```
$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1920    Height:1080
Adjusted recording window is set to:
X:0   Y:4    Width:1920    Height:1072
Your window manager appears to be compiz


Detected compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device default
Recording on device default is set to:
1 channels at 22050Hz
Capturing!
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.

```

---

### Post by ranch hand on 2010-01-01
I know know nothing about it but your link is bad.

---

### Post by LeifAndersen on 2010-01-01
Although I don't know enough to help you with this, I can say that most of the people I've talked to have told me to give up on recordmydesktop, and switch to ffmpeg's x11grab.  (Also, webcamstudio may also do what you need)

---

### Post by n3had on 2010-01-27
> **LeifAndersen said:**
> Although I don't know enough to help you with this, I can say that most of the people I've talked to have told me to give up on recordmydesktop, and switch to ffmpeg's x11grab.  (Also, webcamstudio may also do what you need)

Hi once again for the past two weeks i've tried

gtk-recordmydesktop with old libtheora 1.0.1 (as recordmydesktop is not yet compatible with latest theora)

kdenlive which uses recordmydesktop

recompiled ffmpeg with x11grab

tried istanbul

and webcamstudio which doesn't have full screen capture mode (i reckon)

and recordmydesktop maxes out cpu with the above error and records the screen at 2 or less fps 

x11grab more or less gave me same result

istanbul around 2 again but with crappier quality

webcamstudio is good for webcam recordings i guess

and lastly cheese also bailed me out giving around 10 fps for my webcam recordings.

I love making tutorials and helping others but since i got this new chipset its been a disaster, proprietary drivers on karmic never helped me so went for the opensource on lucid still the same(for screencasting).

So all you people who are using opensource radeon drivers using xorg-edger's ppa having same issues? 

Any help would be appreciated 

peace

---

### Post by Predrag on 2010-04-12
Yes I have the same problem with Ati x1100. I hope that somebody fix it.

---

### Post by ranch hand on 2010-04-12
It would help if folks knew what chip set you are talking about.

Your link goes to a screen saying that the file has been removed
> 
Such file does not exist or it has been removed for infringement of  copyrights. 		


---

