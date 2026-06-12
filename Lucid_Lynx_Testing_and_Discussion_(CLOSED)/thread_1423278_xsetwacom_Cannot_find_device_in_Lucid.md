---
title: "xsetwacom: Cannot find device in Lucid"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ola on 2010-03-06
I just upgraded to Lucid and I'm having problems with my Wacom tablet. In Karmic I used the following lines to configure it the way I want.

```
xsetwacom set "Wacom Graphire4 6x8" Mode Relative
xsetwacom set "Wacom Graphire4 6x8" Button2 "button 3"
xsetwacom set "Wacom Graphire4 6x8" Button3 "button 2"
xsetwacom set "Wacom Graphire4 6x8" SpeedLevel 5
xsetwacom set "Wacom Graphire4 6x8" Accel 7
```

But when I try it in Lucid I'm getting the following error
```
$ xsetwacom set "Wacom Graphire4 6x8" Mode Relative
Cannot find device 'Wacom Graphire4 6x8'.
```

If I do a xinput --lits I get these devices
```
$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom Graphire4 6x8" eraser            	id=8	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom Graphire4 6x8" cursor            	id=9	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom Graphire4 6x8" pad               	id=10	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom Graphire4 6x8"                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"      	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=6	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=7	[slave  keyboard (3)]
    &#8627; "HID 05f3:0007"                         	id=12	[slave  keyboard (3)]
    &#8627; "HID 05f3:0007"                         	id=13	[slave  keyboard (3)]
    &#8627; "UVC Camera (046d:0992)"                	id=14	[slave  keyboard (3)]
```
So I think the names seems fine.

I also tried to use xsetwacom --list which gives
```
$ xsetwacom --list
"Wacom Graphire4 6x8" eraser ERASER
"Wacom Graphire4 6x8" cursor CURSOR
"Wacom Graphire4 6x8" pad PAD
"Wacom Graphire4 6x8" STYLUS
```

Any ideas for what I'm doing wrong?

---

### Post by Pox on 2010-03-11
The only way I've managed to get xsetwacom to work is using the internal numbers it assigns to devices - to find the numbers you want, try
```
xsetwacom --list dev --verbose

# On my machine:
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device '"Power Button"' (6).
... Found device '"Video Bus"' (7).
... Found device '"Video Bus"' (8).
... Found device '"Power Button"' (9).
... Found device '"Sleep Button"' (10).
... Found device '"Wacom ISDv4 E3"' (11).
... Found device '"Wacom ISDv4 E3" eraser' (12).
"Wacom ISDv4 E3" eraser ERASER    
... Found device '"Wacom ISDv4 E3"' (13).
"Wacom ISDv4 E3" STYLUS    
... Found device '"HP Webcam"' (14).
... Found device '"AT Translated Set 2 keyboard"' (15).
... Found device '"PS/2 Synaptics TouchPad"' (16).
... Found device '"Macintosh mouse button emulation"' (17).

```

So I have to use 12 and 13 (just do xsetwacom --set 13 <command>)
Hope that helps.

---

### Post by ola on 2010-03-11
Nice! Worked like a charm. Thanks a lot!

I updated my wacom-config-script to:
```

xsetwacom set 11 Mode Relative
xsetwacom set 11 Button2 "button 3"
xsetwacom set 11 Button3 "button 2"
xsetwacom set 11 SpeedLevel 5
xsetwacom set 11 Accel 7
```

Were **11** is the id for my *Wacom Graphire 6x8* device.

---

### Post by elefantcrossing on 2010-03-17
thanks for the help in solving this! 
using the number worked but since the number changed with every log out or reboot changing my scripts to a number was of no use.

but looking at the output of: xsetwacom --list dev --verbose 
I found the right device name: ... Found device [COLOR="Red"]'"Wacom Intuos4 8x13" pad'[/COLOR] (13)


so for example: xsetwacom set '"Wacom Intuos4 8x13" pad' Rotate "HALF"
works as it should.

---

### Post by ola on 2010-03-21
Just a note.

My device listing gives me: 
```

$ xsetwacom --list dev 
"Wacom Graphire4 6x8" eraser ERASER    
"Wacom Graphire4 6x8" cursor CURSOR    
"Wacom Graphire4 6x8" pad PAD       
"Wacom Graphire4 6x8" STYLUS

```

So if you want to change the STYLUS to relative mode you use:
```

$ xsetwacom set '"Wacom Graphire4 6x8"' Mode Relative

```
and not (as I thought at first)
```

$ xsetwacom set '"Wacom Graphire4 6x8" STYLUS' Mode Relative

```

---

### Post by speedkreature on 2010-03-31
I have a Bamboo (CTH-460)...my **xsetwacom --list dev --verbose** output is as follows:

```
xsetwacom --list dev --verbose
... Display is '(null)'.
... 'list' requested.
```**xinput --list **output is as follows:
```
xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; "Logitech USB Receiver"                     id=10    [slave  pointer  (2)]
&#9116;   &#8627; "Logitech USB Receiver"                     id=11    [slave  pointer  (2)]
&#9116;   &#8627; "SynPS/2 Synaptics TouchPad"                id=13    [slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; "Power Button"                              id=6    [slave  keyboard (3)]
    &#8627; "Video Bus"                                 id=7    [slave  keyboard (3)]
    &#8627; "Sleep Button"                              id=8    [slave  keyboard (3)]
    &#8627; "Power Button"                              id=9    [slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"              id=12    [slave  keyboard (3)]
```Can anyone point me in the right direction?

---

### Post by tempo500 on 2010-04-26
hey, ubuntu 10.04 rc.

i got it halfway working with xsetwacom --list --verbose

how can i switch button 2 with 3?once i copied button 3 to 2, the 2nd button (right click) is lost and i cant copy it over to button 3. and vice versa. this was definitly not the case with 9.10 

xsetwacom set 13  Button3 "Button 2"
xsetwacom set 13  Button2 "Button 3"

thanks, phil

---

### Post by Favux on 2010-04-26
Hi tempo500,

The xsetwacom commands should work.  I gather 13 is the device id in 'xinput --list'?  You can just use "2" instead of "Button 2".

You could try adding the lines to the Wacom "snippets" in 10-wacom.conf (or is it 20 now?) at "/usr/lib/X11/xorg.conf.d/".  It would look something like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
       Option "Button2" "3"
       Option "Button3" "2"
EndSection
```

---

