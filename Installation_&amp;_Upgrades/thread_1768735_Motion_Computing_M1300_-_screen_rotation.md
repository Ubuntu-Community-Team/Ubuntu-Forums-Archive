---
title: "Motion Computing M1300 - screen rotation"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Heamogoblin on 2011-05-27
Hi h
there

just installed ubuntu 10.04.02 on to my tablet, aside from the dreaded intel video problem. install went ok, but i'm finding now. That when i rotate the screen, the touch screen isnt adjusting to match. I'm not really ubuntu savvy, so any help would be appreciated.

---

### Post by Favux on 2011-05-27
Hi Heamogoblin,

Do you mean rotation of the screen orientation isn't working?  If you have a xorg.conf in /etc/X11 I suspect what you need to do is add:
```
	Option		"RandRRotation"	"on"

```
to get rotation.

See the last post on this thread:  [http://ubuntuforums.org/showthread.php?t=1647181&page=2](http://ubuntuforums.org/showthread.php?t=1647181&page=2)  Although the thread is for Maverick not Lucid I expect it would be the same.

Or do you mean the stylus isn't rotating with the screen?  If so what is the output in a terminal of?:
```
xinput list
```

---

### Post by Heamogoblin on 2011-05-28
Hi thanks for the reply, its the pen thats not rotating with the screen. I've tried reading the forum, been getting confused. Plus with me running Lucid, i'm not find files where some of the guides are saying.

Here is the terminal report:

Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]



btw i just had a looked and cant find an xorg.config file :(

---

### Post by Favux on 2011-05-28
Not having an xorg.conf is probably good news.  It means the default Xorg Intel video driver is able to configure things cleanly without needing one.

To rotate Wacom input tools you need to use **xsetwacom set** commands with the Rotate parameter.  You also need the **xrandr** command to rotate the screen orientation.  So to rotate to the right or clockwise (cw) you would use:
```
# rotate to the right
xrandr -o right
xsetwacom set "Serial Wacom Tablet" rotate  CW
xsetwacom set "Serial Wacom Tablet eraser" rotate CW

```
and to rotate back to normal orientation:
```
# rotate to normal
xrandr -o normal
xsetwacom set "Serial Wacom Tablet" rotate NONE
xsetwacom set "Serial Wacom Tablet eraser" rotate NONE

```
You can set up each in a launcher and if you drag the launcher into a panel it will take just a single click on a launcher to launch the commands.

You can also combine both into a single script.  See method 1 at the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Towards the bottom it tells you how to set up a script in a launcher.

---

### Post by Heamogoblin on 2011-05-28
Thanks for that, i guess the next step will be to try and find a way of making use of the buttons on the M1300. If i could made one go left and one right, that would be pretty sweet. 

Are there any handy apps for alters keys and giving them functions? Lucid seems to have assigned them uses, like back, close ect. 

Cheers for your help, was about to resort to Windows 7 :(

---

### Post by Favux on 2011-05-28
Sure you can use *xev* to find the key codes and then Compiz to bind the keys to a new command.  The Rotation HOW TO talks about that to along with the launcher stuff.  And if you use a method 1 script you'd only need to use 1 button.  Those scripts look at the current orientation and then change to the one you specify.

---

### Post by felmatic on 2011-05-29
Hi i have a question what verzion did you use im having issues getting one to install or run even thanks in adavance.

---

