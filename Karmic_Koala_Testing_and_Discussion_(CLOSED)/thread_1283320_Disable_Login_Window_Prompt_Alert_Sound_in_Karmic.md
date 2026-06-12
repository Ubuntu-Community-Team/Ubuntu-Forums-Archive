---
title: "Disable Login Window Prompt Alert Sound in Karmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by undoIT on 2009-10-05
Okay, where is the option to disable the accessibility drum sound for the login window hiding this time around?

I thought I had mastered turning this off, but the location for the option has changed in Karmic and now I can't find it.

---

### Post by mtbsoft on 2009-10-11
Both the Sound configuration dialog and the Login dialog seem the have become very spartan.  Could someone PLEASE advise how to turn off this damned sound.

---

### Post by emarkay on 2009-10-11
There's a bug filed on this - sorry, I don't have the number handy, but it's interesting the turmoil this seems to cause - there's also a post on this somewhere around here, too.
I know that I don't want that "rata-tat!" at 3 am waking up the bats in the belfry.

---

### Post by undoIT on 2009-10-12
The only thing worse than the Ubuntu bongos is the majestic gong sound that Mac OS X makes when you press the power button, that can only be silenced with a third-party hack that a kind soul put together :P

Seriously though, I understand the need for the bongos to alert people who can't see that the login window is loaded. There should just always be an easy way to turn this off.

---

### Post by lithorus on 2009-10-12
One way of disabling it is to uninstall the ubuntu-sounds package :)

---

### Post by aysiu on 2009-10-12
Until this gets fixed, my workaround was to record 1 second of silence as an .ogg file and sub it in for the appropriate noise in the /usr/share/sounds/ubuntu/stereo folder.

---

### Post by VMC on 2009-10-12
Strangely I don't get any sound anymore. I use the [hack]("http://ubuntuforums.org/showpost.php?p=8023240&postcount=10") found here, but even then there was a tiny click of a sound. Not anymore.

---

### Post by taavikko on 2009-10-12
[http://ubuntuforums.org/showpost.php?p=8070893&postcount=32](http://ubuntuforums.org/showpost.php?p=8070893&postcount=32)

---

### Post by emarkay on 2009-10-12
OP, this is a duplicate thread.
See:[http://ubuntuforums.org/showthread.php?p=8070893#post8070893](http://ubuntuforums.org/showthread.php?p=8070893#post8070893)
Please mark thread "Solved".  :)

---

### Post by mtbsoft on 2009-10-13
Followed some of the links from this thread and found a very simple solution along the way:

*System* | *Preferences* | *Startup Applications*

Locate the *Gnome Login Sound* entry and either uncheck it or Remove it.

Simple but it works.

---

### Post by aysiu on 2009-10-13
> **mtbsoft said:**
> Followed some of the links from this thread and found a very simple solution along the way:

*System* | *Preferences* | *Startup Applications*

Locate the *Gnome Login Sound* entry and either uncheck it or Remove it.

Simple but it works.
Didn't work for me.

I'm talking about the weird bongo drum noise when you go to the login screen.

I'm not talking about the weird echo space sounds that happen *after* you log in.

---

### Post by mtbsoft on 2009-10-13
I know the ones you mean - three reboots and it was all fine for me, then I had a crash and the damned bongos are back for me too (though I never had the other ones you mentioned?!?!).  Going to try renaming the .ogg file next.

---

### Post by taavikko on 2009-10-13
So this doesn't work?

```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

How about opening the 
```
sudo -u gdm dbus-launch gnome-control-center
```
And setting the sound off from there.

---

