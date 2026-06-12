---
title: "problem with X41 tablet stylus functionality"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by FrankTheTankC on 2011-01-08
Under the ubuntu 10.10 live CD, the stylus works perfectly.
However, when I actually install and start to use 10.10 on this laptop, touching the stylus to the screen would make the cursor jump and click all over the edges of the screen.
Any ideas?

---

### Post by Favux on 2011-01-08
Hi FrankTheTankC,

Sounds like the stylus isn't actually on the Wacom driver for whatever reason.  Let's see what the output of the following in a terminal is.:
```
xinput --list
```

---

### Post by Oldbones on 2011-01-23
:popcorn:  I'm paying attention to this thread and would love to see the touchscreen start working.  ```
roue@ThinkPad:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-01-23
Hi Oldbones,

Now let's check what driver the stylus is on:
```
xinput list-props "Serial Wacom Tablet stylus"
```
and post the output.

---

### Post by cBusBrewGuy on 2011-03-05
I had similar problems and for kicks I installed the latest version of the linux wacom driver.
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

Problem solved! No more random clicking, jitter, jumping, etc.

---

