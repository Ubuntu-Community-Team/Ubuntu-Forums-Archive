---
title: "Gedit takes more than 30 seconds to start"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 3togo on 2008-09-17
I take me more than 30 seconds to start gedit. Am I alone?

---

### Post by forger on 2008-09-17
It's fine here..

Go in terminal and type:
```
time gedit
```

As soon as you see the window, close it. How many seconds does it mention?

---

### Post by gmclachl on 2008-09-17
I did have the same issue, but an update somewhere along the way fixed it. 

George

---

### Post by Gina on 2008-09-17
Takes less than a second on my P4 - just checked.

---

### Post by bpl07 on 2008-09-17
Check the file ~/.gnome2/gedit-metadata.xml

After first installing intrepid, this file was something like 3000 entries long.  It took forever to load gedit because of this.  With recent updates this file has shrunk considerably, and now gedit opens almost instantly for me.  I can't find the bug report at the moment, but it's there somewhere.

---

### Post by 3togo on 2008-09-17
rm .gnome2 -Rf could not fix my problem.
However, I manage to solve the problem by disabling all the plugins and then restart the gedit. 

Now gedit starts almost instantly even though I enable all the plugin again... Really strange. 

Anyway, Many thanks....



> **bpl07 said:**
> Check the file ~/.gnome2/gedit-metadata.xml

After first installing intrepid, this file was something like 3000 entries long.  It took forever to load gedit because of this.  With recent updates this file has shrunk considerably, and now gedit opens almost instantly for me.  I can't find the bug report at the moment, but it's there somewhere.

---

### Post by mattduckman on 2008-09-18
this isn't solved for me yet

i get 1 second startup when the "File Browser Pane" plug-in is disabled, and a 13 second startup when it's enabled. gedit even hangs for about 5 seconds when i'm enabling the plug-in.

are you seeing this behavior 3togo? either way, i'll file a bug tomorrow.

---

### Post by Nullack on 2008-09-18
Maybe your using a repo mirror that is ancient?

try hitting main?

---

### Post by adult swim on 2008-09-18
im on main server and when i start gedit it never loads.  it starts and pops up but i always have to kill the process because it fails.

---

### Post by Nullack on 2008-09-18
Do you get this?

nullack@PPP:~$ sudo apt-cache policy gedit
gedit:
  Installed: 2.23.93-0ubuntu1
  Candidate: 2.23.93-0ubuntu1
  Version table:
 *** 2.23.93-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status

---

### Post by adult swim on 2008-09-18
edit:  woops!  i had geditXXXX.92, not XXX.93
edit2:  i installed the new version via synaptic, but i still get this from (and still crashing)
edit3: what is weird is that synaptic reports that i have the newest version but not so from apt-cache policy
sudo apt-cache policy gedit 
  Installed: 2.23.92-0ubuntu1
  Candidate: 2.23.93-0ubuntu1
  Version table:
     2.23.93-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
 *** 2.23.92-0ubuntu1 0
        100 /var/lib/dpkg/status

---

### Post by Nullack on 2008-09-18
Well you claim your synched to main so if it was me, I'd format and install clean it sounds dodgy. :)

---

### Post by adult swim on 2008-09-18
i guess i should have thought out my original statement more clearly, i am on the main server, but thinkng back, i havent updated in a while, due to partial upgrade being offered.  does gedit have some dependencies i am missing here, or should it work (as i would think) with only updating it?
edit: im bored, time to upgrade, see you on this install... or maybe not!
EDIT:  im back so soon!  you know, ive always read how bad partial upgrades holding me back, so ive never done them.  i just tried to do it, and saw that only a few libraries were holding me back.  here i go, hopefully my lack of understanding will see me through!

---

### Post by adult swim on 2008-09-18
after all of that :), gedit still crashes!  sudo apt-cache policy gedit shows the newest version installed, im stuck!  its a good thing i learned vi!
gksudo gedit shows:
The application 'gedit' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

---

### Post by Gourgi on 2008-09-18
> **3togo said:**
> However, I manage to solve the problem by disabling all the plugins and then restart the gedit. 

Now gedit starts almost instantly even though I enable all the plugin again... Really strange. 

Anyway, Many thanks....
i had the same issue here and seems to be solved with the solution above
```

sudo apt-cache policy gedit
gedit:
  Installed: 2.23.93-0ubuntu1
  Candidate: 2.23.93-0ubuntu1
  Version table:
 *** 2.23.93-0ubuntu1 0
        500 http://archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status

```

before diabling plugins:

```

time gedit

real	1m5.504s
user	0m57.904s
sys	0m2.624s
gourgi@gourgi:~$ time gedit

real	1m4.609s
user	0m57.720s
sys	0m2.880s
gourgi@gourgi:~$ time gedit

real	1m17.884s
user	0m58.320s
sys	0m2.992s
gourgi@gourgi:~$ time gedit

real	0m49.040s
user	0m15.073s
sys	0m0.780s

```

after disabling and re-enabling plugins
```

time gedit

real	0m7.884s
user	0m3.012s
sys	0m0.260s

```

after re-enabling side browser plugin , gedit froze for seconds and came back alive. i think this plugin has something to do with this.
i'll try to reproduce this using live-cd from daily and report a bug if this bug exists.

---

### Post by Nullack on 2008-09-18
> **adult swim said:**
> after all of that :), gedit still crashes!  sudo apt-cache policy gedit shows the newest version installed, im stuck!  its a good thing i learned vi!
gksudo gedit shows:
The application 'gedit' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

What version did you install with? Have you synched to main again since?

---

### Post by forger on 2008-09-18
Is there any output when you run gedit from terminal?

---

### Post by forger on 2008-09-18
I think I know why it takes so long to load: How many files/folders does the directory you are trying to load have? gedit remembers the last directory, and it could be the fact that your last used directory has a lot of files/folders to be read.
It could also be possible that the files in that directory are HUGE (movies backed up?)

---

### Post by Sophont on 2008-09-18
Alternative: Scintilla

Package: scite


enjoy :-)

---

### Post by Gourgi on 2008-09-18
@forger :
nothing of the above that you mentioned

PS 
i didn't test it yet in live cd with daily build

---

### Post by macaholic on 2008-10-18
Anyone know if this issue has a reolution yet? I still get abnormally long loads with the File Browser Pane plugin.

---

### Post by t.alex on 2008-10-24
same issue here.

---

