---
title: "Synaptic Package Manager problem"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Bill168 on 2010-01-28
[LIST]
[*]I have tried to install a few programs with Synaptic. I installed a game and that went just fine, I found it in Applications > Games. Where does software that really doesn't fall into any of the application categories go to? An example would be Kismet, if I go to Places > Search for Files, I can see that it is on the hard drive, but it is no where to be found in any of the Applications sub menus. My search finds 82 files on a search for "Kismet". Five of them are executable files, I've tried clicking on all five, none of them do anything. I assume that clicking on an executable file should run the file. Is this correct, or am I stuck in the Windoze way of thinking. Another example would be Callgit. I installed it through Synaptic, got no errors, and again I can't seem to find a link to launch the program. What am I doing wrong? I am using Ubuntu 9.10 Karmic Koala.
[/LIST]

---

### Post by MelDJ on 2010-01-28
some programs don't have a GUI. like kismet
to run it, type kismet in terminal

---

### Post by MaindotC on 2010-01-28
> **Bill168 said:**
> I've tried clicking on all five, none of them do anything.

This is happening because kismet needs administrative privileges and additional options passed to it upon startup - just running it by itself returns nothing.  There's nothing wrong with launching applications from the command line - in fact this provides debugging output in case there's a problem - but if you must here is a [guide to adding menu entries in Gnome](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html).

---

### Post by Bill168 on 2010-01-28
> **strAlan said:**
> This is happening because kismet needs administrative privileges and additional options passed to it upon startup - just running it by itself returns nothing.  There's nothing wrong with launching applications from the command line - in fact this provides debugging output in case there's a problem - but if you must here is a [guide to adding menu entries in Gnome]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html").

How exactly do I get " administrative privileges" through the command line? I have run CP/M and DOS years ago, but I don't understand the Linux command line. From what I have read (so far), I need to use the sudo command? I've looked that command up and quite honestly, I don't understand it. Somewhere I have to put in a super user password, but where? I am finding many links on the command line, all tell me the command options but none seem to explain how to use them.

---

### Post by MelDJ on 2010-01-28
sudo is the run as root . type the same password you use for your user.
you can also use su

---

### Post by MaindotC on 2010-01-28
> **Bill168 said:**
> How exactly do I get " administrative privileges" through the command line? I have run CP/M and DOS years ago, but I don't understand the Linux command line. 
Then you're using the wrong operating system.
> ...I need to use the sudo command? I've looked that command up and quite honestly, I don't understand it.

Yeah you're in a different world.  Best to stick w/ your CP/M and DOS.

---

### Post by Bill168 on 2010-01-28
> **strAlan said:**
> Then you're using the wrong operating system.


Yeah you're in a different world.  Best to stick w/ your CP/M and DOS.

Will do! Thanks for your help. At least I have a nice Linux CD coffee cup coaster :D.

---

