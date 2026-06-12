---
title: "simulating two finger scrolling on touchpad doesn't work in lucid as it did in karmic"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by miegiel on 2010-03-02
**Solved:**
> **tnat said:**
> open a Terminal and paste

```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 32 6
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Two-Finger Scrolling" 8 1
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 32 150

```

i created a script and put it into the startup-apps!

cheers

**touchpad.sh** edited
```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
#
# Some useful commands :
#	xinput list
#	xinput list-props "SynPS/2 Synaptics TouchPad"
#	xinput test "SynPS/2 Synaptics TouchPad"
#	xinput test-xi2 "SynPS/2 Synaptics TouchPad"
#
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
#xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9                                       # swap left and middle click, gives you middle click on the left button and left click on tap. - values: lb, mb, rb, b4, b5, etc.
exit
```

For problems with the script loading at startup see : [http://ubuntuforums.org/showthread.php?p=9154700#post9154700](http://ubuntuforums.org/showthread.php?p=9154700#post9154700)

_==================================================_

***Original post :***

In karmic I used a *.fdi* file (/etc/hal/fdi/policy/11-x11-synaptics.fdi) to simulate 2 finger scrolling. Modern touchpads that don't support two-finger scrolling, but do support "gestures" will register 2 fingers as a wider touch than a single finger. The width of the touch is what I used to simulate a 2 finger touch.

Besides the 2finger scrolling I also used the *.fdi* file to make the touchpad better recognize double clicks. It takes 2 or 3 attempts now before the pad gets it. And to make the left button act as a middle button. The middle button is to functional in linux to do without and simulating the middle button by pressing the left and right button simultaneously is a drag.

Anyway, I suspect it all has to do with the *hal removal* (though hal is still installed it seems). I would really like to know what the new lucid way is to get my touchpad tweaks up and running again. Or else, how to resurrect hal.

For the curious : /etc/hal/fdi/policy/11-x11-synaptics.fdi
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
[COLOR="DimGray"]<!-- external mouse
  <device>
     <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">mouse</merge>
        <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
           <merge key="input.x11_driver" type="string">evdev</merge>
           <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
           <merge key="input.x11_options.ButtonMapping" type="string">2 1 3</merge>
        </match>
     </match>
  </device>
-->[/COLOR]
  <device>
     <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
[COLOR="DimGray"]<!-- 
           DON'T USE SHMConfig (unless you must, for example to run 'synclient -m 10'),
           obsolete (in karmic and later at least) and a security risk.
        <merge key="input.x11_options.SHMConfig" type="string">On</merge> -->
<!-- 
           The following is an example of swapping buttons on the Synaptics
           TouchPadthat DOESN'T WORK anymore. See the end of 'man synaptics'
        <merge key="input.x11_options.Buttons" type="string">3</merge>
        <merge key="input.x11_options.ButtonMapping" type="string">2 1 3</merge>

           NOTES :
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>          disable tap-right-top-corner button
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>          disable tap-left-top-corner button
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>          disable tap-left-bottom-corner button
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>            For pads that support true multitouch
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>            For pads that support true multitouch
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>            For pads that support true multitouch
-->[/COLOR]
        <merge key="input.x11_options.TapButton1" type="string">2</merge>              [COLOR="Red"]<!-- set tap-click to middle mouse button, run 'xinput set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3' to swap buttons 1 and 2. This gives you middle click on the left button and left click on tap. -->[/COLOR]
        <merge key="input.x11_options.TapButton2" type="string">0</merge>              [COLOR="DimGray"]<!-- disable 2 finger tap-click, 2 finger tap-click to menu = 3 -->[/COLOR]
        <merge key="input.x11_options.TapButton3" type="string">0</merge>              [COLOR="DimGray"]<!-- disable 3 finger tap-click -->[/COLOR]
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>          [COLOR="DimGray"]<!-- disable tap-right-bottom-corner button (is on by default on my machine) -->[/COLOR]
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>          [COLOR="DimGray"]<!-- disable edge scrolling -->[/COLOR]
        <merge key="input.x11_options.EmulateMidButtonTime" type="string">0</merge>    [COLOR="DimGray"]<!-- effectivelly disable middle button emmulation -->[/COLOR]
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">4</merge>    [COLOR="DimGray"]<!-- set 2 finger emulation presure -->[/COLOR]
        <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>    [COLOR="DimGray"]<!-- set 2 finger emulation pinch width -->[/COLOR]
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>     [COLOR="DimGray"]<!-- enable 2 finger scrolling -->[/COLOR]
        <merge key="input.x11_options.JumpyCursorThreshold" type="string">150</merge>  [COLOR="DimGray"]<!-- stabilize 2 finger tapping and 2 finger scrolling -->[/COLOR]
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">50</merge>       [COLOR="DimGray"]<!-- make doubletap more responsive -->[/COLOR]
     </match>
  </device>
</deviceinfo>
```

---

### Post by tretle on 2010-03-02
Go to System/Preferences/Mouse

Click on the touchpad tab and you can select two finger scrolling under the scrolling heading. 

You can also enable horizontal scrolling.

Hope this helps.

---

### Post by miegiel on 2010-03-02
> **tretle said:**
> Go to System/Preferences/Mouse

Click on the touchpad tab and you can select two finger scrolling under the scrolling heading. 

You can also enable horizontal scrolling.

Hope this helps.

I did manage to make my doubletap a bit more responsive. I'm using xubuntu now, but from the last time I used ubuntu, I remember you only had that option if you had a touchpad with true multitouch.

In xubuntu 10.4 I don't have a two finger scrolling option in my mouse/touchpad preferences (I might have if I had a true multi-touch-pad :-k). But I don't mind hopping back to ubuntu for a while. It only takes 30min to install the basics.

---

### Post by Sashin on 2010-03-03
Two fingers is greyed out.

---

### Post by tnat on 2010-03-03
open a Terminal and paste

```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 32 6
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Two-Finger Scrolling" 8 1
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 32 150

```

i created a script and put it into the startup-apps!

cheers

---

### Post by Sashin on 2010-03-03
Nice, I have two finger functionality back. This is awesome.

---

### Post by miegiel on 2010-03-03
> **tnat said:**
> open a Terminal and paste

...

Great, thanks mate. Now I only need my middle-button back, but I think I can figure that out with this push in the right direction.

edit:
Heh, my side-scrolling is still on, but I'll figure that out too.

---

### Post by tnat on 2010-03-04
> **miegiel said:**
> Great, thanks mate. Now I only need my middle-button back, but I think I can figure that out with this push in the right direction.

edit:
Heh, my side-scrolling is still on, but I'll figure that out too.

You could disable side-scrolling in the gnome-mouse-properties :)

---

### Post by miegiel on 2010-03-04
> **tnat said:**
> You could disable side-scrolling in the gnome-mouse-properties :)

Yet again, not in xubuntu :-k But I can turn it off with *xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' ...* too. I found a nice [list of synaptics device properties]("http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4"). [s]The last thing I need to figure out is to make my left-button below the pad my middle button again. I used to do that by making 1 finger tap my middle button and then swapping the middle and left "click"[/s]. OK, fixed that too :D Time to make the script.

**Enable simulated two finger scrolling**
```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 32 4
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 32 **[COLOR="Red"]7[/COLOR]**
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 8 **[COLOR="SeaGreen"]1[/COLOR]** **[COLOR="Blue"]1[/COLOR]**
```
[COLOR="Red"]Below width 1 finger touch, above width simulate 2 finger touch.[/COLOR] [COLOR="SeaGreen"]Enable vertical[/COLOR] and [COLOR="Blue"]horizontal scrolling.[/COLOR]

It turns out I don't need :
```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Two-Finger Scrolling" 8 1
```

**Disable edge scrolling :**
```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Edge Scrolling" 8 **[COLOR="Red"]0[/COLOR] [COLOR="SeaGreen"]0[/COLOR] [COLOR="Blue"]0[/COLOR]**
```
[COLOR="Red"]vertical[/COLOR], [COLOR="SeaGreen"]horizontal[/COLOR], [COLOR="Blue"]corner[/COLOR]

**Stabilize 2 finger actions :**
```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 32 250
```

**Set/disable buttons and shuffle left and middle click  :**
```
xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Tap Action" 8 **[COLOR="Red"]0 0 0 0[/COLOR] [COLOR="Blue"]2 0 0[/COLOR]**
xinput set-button-map '"SynPS/2 Synaptics TouchPad"' 2 1 3
```
[COLOR="Red"]pad corners rt rb lt lb[/COLOR] [COLOR="Blue"]tap fingers 1 2 3[/COLOR] - values: 0=disable 1=left 2=middle 3=right etc.(can't _*simulate*_ more then 2 tap fingers AFAIK)

---

### Post by miegiel on 2010-03-05
*man xinput* said *--set-int-prop* is deprecated and to use *--set-prop* instead. So I changed the command a bit.

Final script:
**tochpad.sh**
```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
#
# Some useful commands :
#	xinput list
#	xinput list-props "SynPS/2 Synaptics TouchPad"
#	xinput test "SynPS/2 Synaptics TouchPad"
#	xinput test-xi2 "SynPS/2 Synaptics TouchPad"
#
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 2 8 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9                                       # swap left and middle click, gives you middle click on the left button and left click on tap. - values: lb, mb, rb, b4, b5, etc.
exit
```

---

### Post by jtholb on 2010-03-24
The script works great for me, but I'm having trouble getting it to run at startup.  Putting it in Startup Applications doesn't seem to be working for me and I still have to open up terminal and run it myself every time I restart the computer.  Any suggestions?

---

### Post by miegiel on 2010-03-24
> **jtholb said:**
> The script works great for me, but I'm having trouble getting it to run at startup.  Putting it in Startup Applications doesn't seem to be working for me and I still have to open up terminal and run it myself every time I restart the computer.  Any suggestions?

Are you still using jaunty? Just curious ;) it's good to know what versions this works for.

In any case, what are exactly the commands you use to run it in a terminal and to start it with "Startup Applications"?

For both I use :
```
sh touchpad.sh
```
The script is saved in my home directory (not in a sub dir of my home) as *touchpad.sh*

---

### Post by jtholb on 2010-03-24
No, sorry, I'm using lucid.

I also have the script located in my home directory.  Under *command* in the "Startup Applications" I have ```
/home/user/touchpad.sh
```

Per your recommendation I've also tried the following but I don't have the two finger scroll functionality after a reboot.```
sh /home/user/touchpad.sh
``` 

At that point I just open up the terminal and run the following and things are beautiful until the next reboot. ```
/home/user/touchpad.sh
```

---

### Post by miegiel on 2010-03-24
> **jtholb said:**
> No, sorry, I'm using lucid.

I also have the script located in my home directory.  Under *command* in the "Startup Applications" I have ```
/home/user/touchpad.sh
```

Per your recommendation I've also tried the following but I don't have the two finger scroll functionality after a reboot.```
sh /home/user/touchpad.sh
``` 

At that point I just open up the terminal and run the following and things are beautiful until the next reboot. ```
/home/user/touchpad.sh
```

What happens if you run
```
[COLOR="Red"]**sh**[/COLOR] /home/user/touchpad.sh
```
in a terminal ?

And try
```
sh touchpad.sh
```
too. You shouldn't need to give the full path if the script is in your home dir.

Also check for typos ;) I just noticed I named the script *tochpad.sh*, luckily I made the typo in *Startup Applications* too.

---

### Post by jtholb on 2010-03-26
The first works, the second doesn't (you have to specify the directory).

But my problem isn't running the script from the terminal, it's getting it to run from the Startup Applications, or just getting it to run after I've logged in...any ideas?  Thanks.

---

### Post by miegiel on 2010-03-26
> **jtholb said:**
> The first works, the second doesn't (you have to specify the directory).

But my problem isn't running the script from the terminal, it's getting it to run from the Startup Applications, or just getting it to run after I've logged in...any ideas?  Thanks.

Only trying
```
sh /home/user/touchpad.sh
```
in *Startup Applications*. But there must be other ways to start a script than through *Startup Applications*. Just don't ask me how ;)

It's strange though. Commands that work in a terminal always work in *Startup Applications* for me.

---

### Post by jtholb on 2010-03-27
I find it odd as well.  I put a short script in Startup Programs that I wrote that runs fine when I start up (it just prints the date in a text file), but this touchpad script isn't happening.  No idea why.

---

### Post by jtholb on 2010-03-31
After updating Lucid beta with the latest packages (I'm sorry to admit that I don't know which one did it) I'm getting

```
unable to find device "SynPS/2 Synaptics TouchPad"
```

for each xinput line when I run the script in terminal.  Anyone else run into this after updating the beta to the latest packages?

---

### Post by miegiel on 2010-03-31
> **jtholb said:**
> After updating Lucid beta with the latest packages (I'm sorry to admit that I don't know which one did it) I'm getting

```
unable to find device "SynPS/2 Synaptics TouchPad"
```

for each xinput line when I run the script in terminal.  Anyone else run into this after updating the beta to the latest packages?

The syntax for devices in xinput has changed. I changed the script (see 1st post), for example :
```
xinput --set-prop --type=int --format=32 [COLOR="Red"]'[/COLOR]"SynPS/2 Synaptics TouchPad"[COLOR="red"]'[/COLOR] "Synaptics Two-Finger Pressure" 4
```
changed to
```
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
```

I also bumped into this post in another thread today :
> **uljanow said:**
> It is required to use udev. Try something like the following in /etc/udev/rules.d :

```
ACTION!="add|change", GOTO="xorg_synaptics_end"
KERNEL!="event*", GOTO="xorg_synaptics_end"

ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="xorg_synaptics_end"

ENV{x11_options.TapButton1}="1"
ENV{x11_options.TapButton2}="2"
ENV{x11_options.TapButton3}="3"
ENV{x11_options.HorizEdgeScroll}="1"
ENV{x11_options.RBCornerButton}="3"

LABEL="xorg_synaptics_end"
```
Seems there is another method :D

---

### Post by jtholb on 2010-04-01
Thanks for the help--I really appreciate it.  I'm also going to take a look at the other option you suggested.

---

### Post by miegiel on 2010-04-01
> **jtholb said:**
> Thanks for the help--I really appreciate it.  I'm also going to take a look at the other option you suggested.

you're welcome :D

---

### Post by omne on 2010-04-01
This script used to work two days ago, but it stop after the last update of the synaptic package.
The script send me : ```
unable to find device "SynPS/2 Synaptics TouchPad"
``` for each command 
and 
```
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 40
```

don’t give me error but don’t work.
Do you have the same isues ?

---

### Post by miegiel on 2010-04-01
> **omne said:**
> This script used to work two days ago, but it stop after the last update of the synaptic package.
The script send me : ```
unable to find device "SynPS/2 Synaptics TouchPad"
``` for each command 
and 
```
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 40
```

don’t give me error but don’t work.
Do you have the same isues ?

Yes, I was.

> **miegiel said:**
> The syntax for devices in xinput has changed. I changed the script (see 1st post), for example :
```
xinput --set-prop --type=int --format=32 [COLOR="Red"]'[/COLOR]"SynPS/2 Synaptics TouchPad"[COLOR="red"]'[/COLOR] "Synaptics Two-Finger Pressure" 4
```
changed to
```
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
```

I also bumped into this post in another thread today :
[QUOTE=uljanow;8997937]It is required to use udev. Try something like the following in /etc/udev/rules.d :

```
ACTION!="add|change", GOTO="xorg_synaptics_end"
KERNEL!="event*", GOTO="xorg_synaptics_end"

ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="xorg_synaptics_end"

ENV{x11_options.TapButton1}="1"
ENV{x11_options.TapButton2}="2"
ENV{x11_options.TapButton3}="3"
ENV{x11_options.HorizEdgeScroll}="1"
ENV{x11_options.RBCornerButton}="3"

LABEL="xorg_synaptics_end"
```

Seems there is another method :D[/QUOTE]

---

### Post by jtholb on 2010-04-21
Adding ```
sleep 5
``` to the beginning of the script (just before the first xinput line) to add a delay solved my issues of not having the script load at login in case anyone else has similar issues.

---

### Post by miegiel on 2010-04-21
> **jtholb said:**
> Adding ```
sleep 5
``` to the beginning of the script (just before the first xinput line) to add a delay solved my issues of not having the script load at login in case anyone else has similar issues.

Thanks :D I added a note to the 1st post.

---

