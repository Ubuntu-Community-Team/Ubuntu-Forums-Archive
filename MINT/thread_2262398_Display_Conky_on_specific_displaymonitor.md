---
title: "Display Conky on specific display/monitor"
date: 2015-01-24
forum: MINT
---

### Post by Meneer Jansen on 2015-01-24
There is no Conky forum so I thought: I'll ask it here. I use a "flavour" of Ubuntu 14.04 (Mint) and I've got two monitors. I use Conky in windowed mode (I start conky w/ the option "*--own-window*"). It doesn't show on my desktop/wallpaper but in a little window. However, Conky always starts on the wrong monitor. There is an option in conkyrc to specify "specify an X display to connect to" (see [conky's documentation]("http://conky.sourceforge.net/config_settings.html")). That option is:
```

display

```
But I do not know how to specify the argument that that option needs. I tried this:
```

display VGA1

```
Because my primary display is called "VGA1" by *xrandr*. But then Conky returns the following error on the command line:
```
Conky: can't open display: VGA1

```
What argument will the setting "display" in Conky accept?

---

### Post by howefield on 2015-01-24
Thread moved to the "*MINT*" forum.

---

### Post by Habitual on 2015-01-24
```
conky  -V | head -1
``` output please.

---

### Post by Meneer Jansen on 2015-01-25
> **Habitual said:**
> ```
conky  -V | head -1
``` output please.
Out put is:

```
$ conky -V | head -1
Conky 1.9.0 compiled Wed Feb 19 18:44:57 UTC 2014 for Linux 3.2.0-37-generic (x86_64)

```

---

### Post by Habitual on 2015-01-26
terminal > ```
xrandr
``` output please.

---

### Post by Meneer Jansen on 2015-01-26
> **Habitual said:**
> terminal > ```
xrandr
``` output please.
The output:
```

~$ xrandr 
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 32767 x 32767
VGA1 connected primary 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      60.0*+
   1400x1050_60.00   60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +   50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1280x1024      60.0  
   1360x768       60.0  
   1152x864       60.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9     59.9  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
The second display (HDMI1) is off right now because else Conky starts on my HDMI television instead of my monitor (I don't have my TV on the whole day, but I do have my PC/monitor on the whole day).

---

### Post by Habitual on 2015-01-27
So, if you have your HDMI1 turned off, and you start conky what happens?
Does it show?
If your HDMI1 is turned on and you edit your conkyrc and *comment out display *
# display VGA1
save and start conky what happens?
How are you starting conky (calling your conkyrc using -c /path/to/conkyrc)?
Have you tried the various other own_window_types?

Please share your conkyrc here.

I usually have to edit gap_x to maneuver my conkies around the dual monitors that I use, (identical DVI-D-[01] ouptuts with identical monitors).

What kind of video card do you have? Are you using proprietary drivers or Ubuntu provided ones for it?
```
lspci | grep -i vga
``` should show us.

I'm kind of stuck, so I'm just looking for the obvious. Sorry about that.

---

### Post by Meneer Jansen on 2015-01-27
> **Habitual said:**
> So, if you have your HDMI1 turned off, and you start conky what happens?
Does it show?

Then it shows up on VGA1 (i.e. my PC monitor, not the TV)
> **Habitual said:**
> 
If your HDMI1 is turned on and you edit your conkyrc and *comment out display *
# display VGA1
save and start conky what happens?

The I get the error from my first post, i.e.:
```

Conky: can't open display: VGA1[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
```
> **Habitual said:**
> 
How are you starting conky (calling your conkyrc using -c /path/to/conkyrc)?
Have you tried the various other own_window_types?

Please share your conkyrc here.

I don't think that'll be of much use. With the option "display VGA1" enabled Conky doesn't even start. Without said option: no probs. The other own_window options can not place Conky on a specific display. The option "display" is meant for that.
> **Habitual said:**
> 
I usually have to edit gap_x to maneuver my conkies around the dual monitors that I use, (identical DVI-D-[01] ouptuts with identical monitors).

I've considered that. But because I start Conky in its own window that won't work. This is because the "gap_x" option will then create a huge empty gap in Conky's window. 
> **Habitual said:**
> 
What kind of video card do you have? Are you using proprietary drivers or Ubuntu provided ones for it?
```
lspci | grep -i vga
``` should show us.

I'm kind of stuck, so I'm just looking for the obvious. Sorry about that.
My gra.card. is the one on my moterboard (the one that's in my Intel CPU actualy). See the output of spci below:
```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
```
The driver (i.e. kernel module) is the open source one. The command "*lsmod*" says that I'm using the kernel module/driver named "_i915_". I sooner think that a modification of my */etc/X11/xorg.conf*  file might help. Conky complains that I'm using the wrong "word" (or: lingo) to point to my display. The names *xrandr* gives to my displays are not the names that Conky expects, I think. 

One can start applications with the command "export DISPLAY=:0.0 <application>" or something like that I thought. I think tat Conky wants a parameter like that... But when I try to determine the display "number" w/ the command $DISPLAY I get the following error:
```

~$ $DISPLAY

:0: command not found

```
I think the output of the $DISPLAY variable should simply be something like ":0.1". 


[edit] Wait a minute... Fiffled a bit w/ my Conky config file and Conky does noet give me an error if I use the following "lingo" for the "display" option:
```

display :0.0

```
If I put my DHMI1 display (i.e. my TV) on and when I activate it I unfortunately cannot use any other display number than :0.0. Abnyrthing other than :0.0 (i.e. :0.1 or :1.0 or :1.1) won't start conky. If I "ask" what the display number is on the command line w/ $DISPLAY then I keep on getting the error:
```
:0: command not found
```
Guess I'll have to find out how to let Linux (or Xorg) give my displays a number....:???:

---

### Post by Habitual on 2015-01-27
are you starting conky via  a shell script?
"export $DISPLAY ..." should not be necessary.

---

### Post by Meneer Jansen on 2015-01-29
It appears to me that Conky wants an argument like :0.1 for its option "display". Typically this means first X device (i.e. your video card, assigned by :0) and the second display (i.e. your TV, assigned by .1). That means configuring X to have two separate X screens by editing */etc/X11/xorg.conf*. Apart from a lot of other settings in that file, this goes wrong after adding the following line to aforementioned settings file:
```

Section "ServerLayout"

   Screen         1          "Screen1"    LeftOf    "Screen0"

```
Modern desktops like Cinnamon, Unity and Gnome3 do not work w/ two X screens. They crash. 

The only way I can start Conky on my Monitor is by placing the TV screen left of the monitor by using Cinnamon's settings Display dialog screen (from the System Settings application). I.e. start 'cinnamon-settings' from the command line, etc.. However, then Chromium starts on the wrong display.

To make a long story short: controlling on which display Conky starts is not possible anymore w/ the latest Desktop Environments at the time of writing because they do NOT support separate X screens.

---

