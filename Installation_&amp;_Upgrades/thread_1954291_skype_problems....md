---
title: "skype problems..."
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by Geist in the shell on 2012-04-07
just upgraded to 11.10, i had a few problems with skype on 11.04, audio requiring app. restart, the 'my video' thumbnail in main video window causing an odd glitch (blocking out video on whole x-axis section of the thumbnail while repeating it from an upper section of the main vid window. EXTREMELY annoying, never found a fix) but with a fresh upgrade, the skype notification icon hasnt shown up in my top bar(by the upgrade, battery, volume, etc.), sys-tray equivalent 

TL;DR skype notification icon not present, how do make it appear?

---

### Post by Geist in the shell on 2012-04-07
bumping

---

### Post by Bucky Ball on 2012-04-07
Please wait 24 hours before bumping. ;)

Have your tried dropping the Skype icon in there or right clicking and adding it?

---

### Post by Geist in the shell on 2012-04-08
"please wait 24 hours.." noted, still new to the forums =p

right clicking was the first thing i did, nothing.
just tried drag and drop, icon wouldnt even come out of the dock probably cause ive switched to ubuntu 2d because ubuntu is messing up, i believe it has something to do with this error message:


[INDENT][/INDENT]E: Type '    sudo' is not known on line 59 in source list /etc/apt/sources.list
 
[INDENT][/INDENT]E: The list of sources could not be read.


happens every time i try to update through terminal via ' sudo apt-get update', or in update manager.
I need to get that fixed before anything else

---

### Post by Bucky Ball on 2012-04-08
> **Geist in the shell said:**
> 

E: Type '    sudo' is not known on line 59 in source list /etc/apt/sources.list
 E: The list of sources could not be read.


happens every time i try to update through terminal via ' sudo apt-get update', or in update manager.
I need to get that fixed before anything else

Yes, you do. Should be the subject of a new thread but seeing as we're here:

Could you paste your /etc/apt/sources.list here, please? (Specifically line 59.)

---

### Post by Geist in the shell on 2012-04-08
yeah i found the error message like ten minutes after i started the thread, bebash: /etc/apt/sources.list: Permission denied
en too lazy to make another

here's result:


bash: /etc/apt/sources.list: Permission denied

should i sudo it? i have no f***ing clue whats going on

---

### Post by Geist in the shell on 2012-04-08
oh my bad that was a location not a command,
 
lines 55 - 60
do you need the rest?

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
****sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
****sudo apt-get update

last thing i installed was an icon packages and cairodock with sudos from noobslab(.)com

---

### Post by Bucky Ball on 2012-04-08
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
[B]****sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
****sudo apt-get update[/B]
```Get rid of the two lines in bold. Then:

```
sudo apt-get update
```

---

### Post by Geist in the shell on 2012-04-08
how do i take ownership? it says i dont have the permissions necessary to save a file here, or save because its a read only
ty for all your help thus far btw

---

### Post by Bucky Ball on 2012-04-08
```
sudo nano /etc/apt/sources.list
```

Remove the two lines I put in bold. Press 'x' then 'y'. Then run:

```
sudo apt-get update
```

The non-terminal way to do this is go to Update Manager, click 'Settings' at bottom left, click the 'Other Software' tab.

You should find those 'sudo' lines you need to delete there. Simply untick them.

---

### Post by Geist in the shell on 2012-04-08
awesome, it worked :D 
now back to thread topic lol
did a restart, im on the regular ubuntu/unity desktop now, skype is open and no notification thing in the top bar(what is the name of that anyway?)
ive seen that 11.10 has pretty limited system setting control pre installed, ive gotten advanced settings or, 'system tweak' but its not much help.

---

