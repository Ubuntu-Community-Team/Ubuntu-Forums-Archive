---
title: "electric sheep 4 xscreensaver"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-10-27
xscreensaver users get ready for a sheep shearing contest!!!  i dont like gnomescreensaver as it lacks all the options x has

alt + f2

gksu apt-get install xscreensaver electricsheep

run

alt + f2

gnome-terminal

run

gedit $HOME/.xscreensaver

at the bottoms of the programs section add

```

electricsheep --root 1			    \n\

```

make sure it is over this block of codes

```

pointerPollTime:    0:00:05
pointerHysteresis:  10
windowCreationTimeout:0:00:30
initialDelay:	0:00:00
GetViewPortIsFullOfLies:False
procInterrupts:	True
xinputExtensionDev: False
overlayStderr:	True

```

save.....

then alt + f2
xscreensaver-demo
select in the list electric sheep, and let the shearing begin.

---

