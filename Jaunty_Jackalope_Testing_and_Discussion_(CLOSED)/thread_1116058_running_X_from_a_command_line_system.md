---
title: "running X from a command line system"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by willz06jw on 2009-04-04
Hi,

I am trying to run dillo in X from the command line.

Note:
-I am running 9.04 (fully updated) with a command line only alternative install.
-I installed xorg and dillo using aptitude
-When I run a script to start X and then run dillo I get a black screen.
     -The script is:
         X :3 -ac
         sleep 5
         DISPLAY=:3 dillo

Any ideas guys/gals?

Thanks for any help,
Will

---

### Post by albinootje on 2009-04-04
This is probably easier to get it running :
```

gedit ~/.xinitrc

```

Put this in it :
```

dillo

```

Switch to a console with ctl-alt-F1, and type :
```

startx -- :1

```

---

### Post by albinootje on 2009-04-04
I've just tested my suggestion, and maybe you want to have dillo to 
start in full window mode instead and use a windowmamager so that the close and maximize buttons work :
```

# content of ~/.xinitrc
dillo -f &
metacity

```

---

### Post by willz06jw on 2009-04-04
Thanks for your help,

When I try to open the .xinitrc file with vi or nano (using the sudo prefix) it opens a blank file and won't let me save it.

---

### Post by albinootje on 2009-04-04
> **willz06jw said:**
> Thanks for your help,
When I try to open the .xinitrc file with vi or nano (using the sudo prefix)

No need to use sudo here.
~/.xinitrc is about your own home directory.
> 
it opens a blank file 

That's normal because ~/.xinitrc doesn't exist by default.
> 
and won't let me save it.
Hmm. Weird.

---

### Post by willz06jw on 2009-04-04
I restarted and tried it again without sudo and it worked brilliantly!  

...Of course this leads me to another question (don't shoot me):  Is there a good way to make a launcher for this program (so I don't have to edit the xinitrc file every time I need to open a different program)?

Thanks again,
Will

---

### Post by albinootje on 2009-04-04
> **willz06jw said:**
> Is there a good way to make a launcher for this program (so I don't have to edit the xinitrc file every time I need to open a different program)?


You could do the following :
```

sudo apt-get install rxvt

```
And then put this in your xinitrc :
```

# ~/.xinitrc content
metacity &
rxvt &

```

With that a terminal will be started, and you can start up programs from within that terminal.

---

### Post by willz06jw on 2009-04-05
What about a shell script .. is there anyway to do it with something like that?

Thanks,
Will

---

### Post by willz06jw on 2009-04-05
What I eventually did was use the lwm (lightest window manager) instead of metacity.  It contains a shell that starts up when you press the middle mouse button.  I can launch anything with it and it takes up less resources than any other solution I have seen.

Thanks for the help!
Will

---

