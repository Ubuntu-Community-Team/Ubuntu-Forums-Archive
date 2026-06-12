---
title: "GRUB2 commandline problems?"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-07-07
Whenever I use GRUB2 at boot (sudo grub-emu has no problem), and go to the commandline, it works, however, when the output gets to the bottom of the screen, it updates each line one by one, and extremely slowly.
Basically, the top line gets updated, then the next one down, and so on until the end. the problem is it takes about half a second after the previous one. If multiple lines are being outputted, it updates all the way down the screen, then it updates again, one line at a time.

---

### Post by budluva04 on 2009-07-07
what version of grub?

can you pastebin your /etc/default/grub

---

### Post by camper365 on 2009-07-08
```
# This file is sourced by update-grub, and its variables are propagated
# to its children in /etc/grub.d/
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

```

---

### Post by budluva04 on 2009-07-08
have you tried uncommenting this line?

GRUB_GFXMODE=640x480

then run update-grub2

---

### Post by tad1073 on 2009-07-08
change your resolution also

---

### Post by camper365 on 2009-07-09
it didn't work.

EDIT (again): I tried changing the resolution and that didn't work either. Sorry about the delay. I got distracted

---

### Post by budluva04 on 2009-07-09
can you reply back with your fix so others will know

---

### Post by camper365 on 2009-07-10
I found that changing the resolution just made the blue box on startup and the font size smaller. It didn't help with the problem.

---

### Post by budluva04 on 2009-07-10
ok, then drop to the grub commandline and try vbeinfo

and then see what modes are supported and try changing them to whatever is supported by your hardware

---

### Post by camper365 on 2009-07-13
How do I figure out what's supported by my hardware? I tried that and then changing the vbe_mode but the problem persisted.

---

### Post by MacUntu on 2009-07-13
I see the same thing when dropping to the command line ('c' at GRUB2 menu). Scrolling is very slow (eg. vbeinfo printing the supported resolutions). Don't know if that's a bug?

---

### Post by camper365 on 2009-08-04
A few days ago I ran a
```
sudo aptitude install grub
```
for a project of mine, and then just now I ran a
```
sudo aptitude install grub2
```
and the problem went away. I also noticed that the old font is gone.

---

### Post by budluva04 on 2009-08-04
well grub2 just got an update the other day....this might have fixed your problems, the old grub2 was a few months old

grub2 (1.96+20090725-1ubuntu1) karmic; urgency=low

---

### Post by camper365 on 2009-08-04
I went through the karmic-changes archives right after I posted that and I found that there had been a change a few days ago so I think that solved my problems.

---

