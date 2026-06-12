---
title: "Opera 10 Completely Dead"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alligoodw on 2009-08-27
It's possible this thread doesn't belong here, but seeing I'm testing it under Karmic Koala I thought I'd give it a try. 

I recently downloaded Opera 10 from [www.opera.com](www.opera.com) site - it was the debian package for i386.  I installed it and work with it a whole day.  I love Firefox but I like to have two browsers to play with on my system.  And too, I tend to like Opera as well.  

After that day, Opera hasn't work at all.  When I select it from the main menu it does nothing.  I can't load it from gnome-do either.  Should I try and load it from the terminal, I get the following message:

/home/alligoodw/lib/opera/10.00/opera: 1: Syntax error: "(" unexpected

Anyone have any suggestions as to how to correct this error?

---

### Post by gradinaruvasile on 2009-08-27
Maybe uninstall it and reinstall?

---

### Post by alligoodw on 2009-08-27
I've tried that - it doesn't work!

---

### Post by taavikko on 2009-08-27
Delete the settings folder from ~/. and try again.

Sorry, don't know the exact name for the folder, maybe in ~/.config/

---

### Post by alligoodw on 2009-08-27
I've just discovered something. If I run opera as root - sudo opera - opera will load as it should.

---

### Post by taavikko on 2009-08-27
> **alligoodw said:**
> I've just discovered something. If I run opera as root - sudo opera - opera will load as it should.

Never run those apps with root privileges.

Like I stated on my previous post, delete the .config file and start again, it should help.

---

### Post by alligoodw on 2009-08-27
It won't run if not run as root.  I would delete that .config file, but I don't know where it is located.  My knowledge of Ubuntu isn't as sharp as your own.  What is the complete name of this config file I should be looking for?  I'll do a search for it and delete it from there.

---

### Post by taavikko on 2009-08-27
> **alligoodw said:**
> It won't run if not run as root.  I would delete that .config file, but I don't know where it is located.  My knowledge of Ubuntu isn't as sharp as your own.  What is the complete name of this config file I should be looking for?  I'll do a search for it and delete it from there.

The following should give a clue where it is.
```
cd; find . -iname "*opera*"
```

I don't use opera so cannot tell exactly.

In nautilus, press Ctrl+H to show hidden files/folders and search around...

---

### Post by Colonel Kilkenny on 2009-08-27
Opera configs are at ~/.opera.
You can try to start opera with temp profile from console with "opera --pd /tmp/opera".

---

### Post by ronacc on 2009-08-27
I have been using opera 10 since the start of karmic on amd64 and have had no problems other than a copy/paste problem with the b3 version of opera 10 that was resolved in the RC . try renaming your ~/.opera dir and then reinstall .

---

### Post by alligoodw on 2009-08-27
What is ~/.opera dir?  I have a folder in my home folder called .opera.  Is this the folder you are referring to?  If so, I changed the name of that folder and attempted to reinstall.  However, I noticed that is attempting to reinstall instead of installing the program.  Is this what you want?

---

### Post by ronacc on 2009-08-27
yes to both questions .

---

### Post by ronacc on 2009-08-27
reinstalling should create a new .opera dir in your home dir with default settings , you can then copy any bookmarks wand PW's etc from the renamed dir . if that don't work try purging opera and then install again .

---

### Post by taavikko on 2009-08-27
> **ronacc said:**
> reinstalling should create a new .opera dir in your home dir with default settings , you can then copy any bookmarks wand PW's etc from the renamed dir . if that don't work try purging opera and then install again .

No need for reinstall, just deleting the folder resets to defaults and restarting the app will do.

---

### Post by alligoodw on 2009-08-27
And how does one purge a program?

---

### Post by ronacc on 2009-08-27
if you installed it with gdebi it should show up in synaptic , mark it for complete removal .  

@ taavikko the reinstall is to make sure it is also reset in /usr just incase . It shouldn't be necessary but in case of problems cover all bases .

---

### Post by alligoodw on 2009-08-27
Problem is resolved.  I went into Synaptic, uninstalled the program and rebooted the system.  I redownloaded the .deb file and reinstalled Opera.  The reinstallation was successful.  I'm sending this reply using Opera.

I would be amiss if I failed to express my appreciation to all you guys for your input and your time.  Thanks, guys!

---

### Post by MavisCruet on 2009-08-31
I have exactly the same problem.  Removed it with synaptic even tried the latest stable version.  Nada.

I will try the purging plan.

It's not limited to Karmic Koala, I am in 9.04

---

### Post by pedrogfrancisco on 2009-08-31
I'm with [http://snapshot.opera.com/unix/rc-4570/intel-linux/opera_10.00.4570.gcc4.qt4_i386.deb]("http://snapshot.opera.com/unix/rc-4570/intel-linux/opera_10.00.4570.gcc4.qt4_i386.deb") and it works.

**WARNING**: Qt4 version [seems they're not pushing it, probably because it seems slow]

**WARNING**: 10 *RELEASE CANDIDATE* version, AKA not final AKA might ignite your settings and you lose them and stuff

**WARNING**: once you convert mail to Opera 10 format you can't revert it back to 9.64.

**WARNING**: end of warnings ;)

---

### Post by ronacc on 2009-08-31
try to start opera from a terminal and post the output .

---

### Post by MavisCruet on 2009-08-31
Having removed it again with synaptic, there is no longer an opera root folder when I reinstalled the .db file.

details below...

[IMG]http://i15.photobucket.com/albums/a396/djmaviscruet/operafail.png[/IMG]

---

### Post by ronacc on 2009-08-31
I meant try running opera in a terminal .

---

