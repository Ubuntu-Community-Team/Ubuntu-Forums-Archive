---
title: "Make out of Logitech MX518 &quot;+- Button&quot; the &quot;Middle Button&quot;"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Bart Simpson 18 on 2007-05-09
hi guys,

I want to make from the **+ Button ** on my Logitech MX518 mouse the **middle button**.

I need this for animation program I use. I really need this kind of setting because I am used to work with the ¨plus¨ button as the middle button on my Ex-Windows I let go several days ago. ):P 

I already tried to follow the guides with evdev and lomoco but I have not succeeded.
When I use the evdev setting in my xorg.conf Ubuntu does not load the GUI.

**My Operating System is Ubuntu Feisty 7.04** 

Please help

---

### Post by Paradoxdruid on 2007-05-09
I wish you luck.  Feisty was overall an upgrade for me, but caused me evdev problems with my Logitech MediaPlay mouse.

I think I finally have it working again.

You've probably followed all the guides, but here's my process to get it working in brief:
run```
cat /proc/bus/input/devices
``` and scan the results for your mouse.  Copy the Name portion, without quotation marks (case matters!).

Open xorg.conf ( kdesu kate /etc/X11/xorg.conf  in my case) and find your section about the mouse.
Change it to:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "ZAxisMapping" "4 5"
EndSection
```
Make sure that your server layout section looks something like this:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
 EndSection
```

Restart X, and it should boot fine.  If it doesn't undo the above changes- sorry it didn't work.

If it did boot, run ```
xev
``` and move your mouse pointer into the box that opens.  Try your special buttons--  are they registering as key presses?  If so, mark down what button events they are.

To bind those keys to different behavior, I like using a GUI for xkindkeys.  Run ```
sudo aptitude install xbindkeys xbindkeys-config
``` then run xbindkeys-config.  There, you can type a command you want to run and then hit the button you want associated with it.

Good luck!

---

### Post by Bart Simpson 18 on 2007-05-09
thanks man for your help, **but** everytime I write the evdev thing in the xorg.conf -> **Ubuntu graphical interface does not come up** -> only black screen. :( 

Maybe evdev got somehow corrupted on my system. Is there a way to reinstall evdev or something...:confused: 

My system is a Laptop Dell Precision M90
2.33 GHz
2048 MB Ram
QuadroFX 3500M


thx mate

---

### Post by Paradoxdruid on 2007-05-09
Try ```
lsmod | grep evdev
```
does it return anything?  If not, evdev isn't loaded in your kernel and you need to ```
sudo modprobe evdev
```
That might solve it.

Also, if you could post the output of ```
cat /var/log/X.log.0
``` that might help.  I've been having a problem where X doesn't recognize the evdev mouse as a mouse and aborted because there is no mouse loading.  You can see more discussion of that problem [here]("http://zaitcev.livejournal.com/tag/xen").

Good luck!

---

### Post by Bart Simpson 18 on 2007-05-09
thx for your help - appreciate that :) 

After typing the lsmod command I received that evdev is on the system
**evdev                  11008  4 **

thx

---

### Post by Paradoxdruid on 2007-05-09
> **Bart Simpson 18 said:**
> thx for your help - appreciate that :) 

No problem.  I wasn't specific enough, though--  I need your X.log.0 when the graphics won't start.

When you enable evdev and the graphics don't start, hit Ctrl-Alt-F1 to move to tty01.  There should be a login prompt, login with your username and password.  Then ```
cat /var/log/X.log.0 > evdev-xlog.txt
```.  You can then restore your xorg.conf (I always keep a working backup at xorg.conf.backup, like so)```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Then kill your window manager ( ps ax | grep kdm, then kill $PID) and restart X with sudo kdm.  It sounds like you already know all this stuff, but I'd prefer to be thorough in case someone less experienced reads this thread at a later date.

Maybe the non-working log will help diagnose the problem.

---

### Post by Bart Simpson 18 on 2007-05-09
Okay here you got the log :popcorn:

P.S. I am since a week or so Linux User.... so be gentle with me. Bye the way - I use gnome and not kde

---

### Post by Bart Simpson 18 on 2007-05-09
Here you got the xorg.conf - just in case

---

### Post by Paradoxdruid on 2007-05-09
Bart-

You can see in the log that X isn't recognizing the evdev mouse and trying to create a default mouse right here:
```
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
```

However, your log cuts off during graphics initialization, well before it would cut off from mouse problems (mine would end with "No pointer specified" type errors.

So...  I guess that's the end of where I can help--  I'm not sure what's going on.  Maybe post your problem to [this thread]("http://ubuntuforums.org/showthread.php?t=219894") and see if they can help.

Sorry I couldn't help more.

---

### Post by Bart Simpson 18 on 2007-05-09
thx mate, you rock :guitar: 

I try to create a **udev rule** like here
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

Maybe it helps somehow in the initialization of the mouse :)

---

### Post by Rescue9 on 2007-05-12
I understand what you are trying to do, however, I don't think that this is possible in linux yet.

Let me explain.

Mapping buttons is easy enough after you get the mouse working. However, when you mapped the + button to the middle mouse button in windows the Logitech mouse drivers actually did a little extra magic in the background. See...the + and - buttons are "hardwired" to increase or decrease the mouse resolution from 400 to 800 to 1600. This is all done from within the mouse itself. When you mapped the buttons in windoze, the Logitech drivers did one of 2 thing: either they "communicated" with the mouse itself and instructed it not to increase the resolution, or they "captured" the resolution change and altered it on the OS level. Either one of these two would allow you to map the button without constantly changing your resolution.

Now.... since linux doesn't use the Logitech drivers to work properly, there isn't going to be a way for the OS to compensate for the resolution change that will be sent by the mouse every time you press the + button. So... whats going to end up happening is if you use any resolution less than 1600 and you press the mouse button, the mouse movement on screen will jump wildly. The mapped command will still work, but your resolution will constantly change. This may not be a big deal for you if you are usually using 1600 dpi. However, as in my case, i use 400 dpi since the mouse jumps wildly at any other resolution.

From what I've read of lomoco, this feature isn't yet imported. However, I haven't downloaded the program yet. I may try this at work tomorrow to verify.

---

### Post by Klargodut on 2007-05-14
This is my working configuration of my MX518 in xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event2"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

---

### Post by Bart Simpson 18 on 2007-05-15
hey boys,

hmmm, I tried everything I possibly could, but I have not succeeded, yet. I would be a pity, if it could not be done in Linux.

I mainly need the button middle trick mainly for Autodesk Maya and for Firefox browsing. I hate to push the wheel button. 

I started to use Maya on Windows again. I hope that it will stay only a temporary solution.:)


P.s. I am on holiday till 29. of May -> so it's not going to be for me possible to answer. :popcorn:

---

### Post by Rescue9 on 2007-05-15
If you're back to using windoze simply because of a mouse button, then I fear you're stuck in windoze hell forever.

---

