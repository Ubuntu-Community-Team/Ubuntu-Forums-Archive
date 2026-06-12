---
title: "No GUI after upgrade...?"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by GabrielWolff on 2005-11-11
Hey!

I just upgraded from 5.04 to Breezy, and what happens when I restart is the following: 
It all seems to run well, but instead of what I saw before, when starting the machine, the graphics look the same like when the machine starts up (black backround white letters, like DOS or so), I am asked for my user and pass, and then I seem to be in a Terminal (it says: name@ubuntu:~$, and that's it). No GUI, nothing

What happened??

Thanx

Gabriel

---

### Post by Lambert on 2005-11-11
First hit ctrl+alt+F7 and make sure you're on that virtual terminal and see if you come to the graphical log on.

if not

After you login and in the terminal type 

```
startx
``` 
and see if that gets you into graphical

If it works someone else will have to post explaing how to make sure it starts up in graphical mode.
if not post back here the results

---

### Post by izmaelis on 2005-11-11
[QUOTE=Lambert]First hit ctrl+alt+F7 and make sure you're on that virtual terminal and see if you come to the graphical log on.

if not

After you login and in the terminal type 

```
startx
``` 
and see if that gets you into graphical

If it works someone else will have to post explaing how to make sure it starts up in graphical mode.
if not post back here the results[/QUOTE]
And if this command won't start GUI, you should do
```

/var/log/Xorg.0.log

```
and see what error causes not loading GUI. You can even post xorg log here to get your problem solved.

---

### Post by GabrielWolff on 2005-11-11
hitting ctrl+alt+F7 did nothing

when typing startx I got the following response:

xauth: creating new authirity file /home/gabriel/.serverauth4111
xauth: error in locking athority file /home/gabriel/.Xauthority
/usr/bin/startx: line 143: dev/null: Permission denied
xauth: error in locking athority file /home/gabriel/.Xauthority
xauth: error in locking athority file /home/gabriel/.Xauthority
/usr/bin/startx: line 143: dev/null: Permission denied
xauth: error in locking athority file /home/gabriel/.Xauthority

Giving up.
xinit: Connection refused (errno 111): unable to connect to X server
Xinit: No such process (errn #): Server error.
xauth: error in locking authority file /home/gabriel/.Xauthority
/usr/bin/startx: line 172: /dev/null: Permission denied

While writing this I noticed: should I be connected to the web while trying this?

---

### Post by GabrielWolff on 2005-11-11
tried that as well.
I typed /var/log/Xorg.0.log

response:

-bash: /var/log/Xorg.0.log: Permission denied

gabriel, the user I'm logged in with, should be root.

Any ideas?

---

### Post by Cannedbread on 2005-11-11
there is no root user on ubuntu ,try putting "sudo" before all of those commands. "sudo <command>".

my machine is doing the same thing. but startx doesnt do anything.

---

### Post by Cannedbread on 2005-11-11
how did you install ubuntu?, was it from a netboot by any chance?

---

### Post by GabrielWolff on 2005-11-11
OK, I am one step further, and one step more confused:

After reading through the diffeent threads I typed in:

sudo dpkg-reconfigure xserver-xorg

and got:

perl: waring: Setting up locale failed.
perl: warning: Please check that your locale settings:
       LANGUAGE = "en_IL:en",
       LC_ALL = (unset),
       LANG = "en_US.UTF-8"
     are supprted and installed on your system
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to the defaulet locale: No suh file or directory
locale: Cannot set LC_MESSAGES to the defaulet locale: No suh file or directory
locale: Cannot set LC_ALL to the defaulet locale: No suh file or directory
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

Is that maybe the answer: should I run installation once again?
How?
Will I loose any information on the machine?

G

---

### Post by GabrielWolff on 2005-11-11
[QUOTE=Cannedbread]how did you install ubuntu?, was it from a netboot by any chance?[/QUOTE]
Yes, I guess.
Through apt-get and that stuff. No CD
Was that the question?

---

### Post by apjone on 2005-11-11
[QUOTE=GabrielWolff]OK, I am one step further, and one step more confused:

After reading through the diffeent threads I typed in:

sudo dpkg-reconfigure xserver-xorg

and got:

perl: waring: Setting up locale failed.
perl: warning: Please check that your locale settings:
       LANGUAGE = "en_IL:en",
       LC_ALL = (unset),
       LANG = "en_US.UTF-8"
     are supprted and installed on your system
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to the defaulet locale: No suh file or directory
locale: Cannot set LC_MESSAGES to the defaulet locale: No suh file or directory
locale: Cannot set LC_ALL to the defaulet locale: No suh file or directory
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

Is that maybe the answer: should I run installation once again?
How?
Will I loose any information on the machine?

G[/QUOTE]


run /etc/X11/xorgcfg

---

### Post by GabrielWolff on 2005-11-11
[QUOTE=apjone]run /etc/X11/xorgcfg[/QUOTE]
 I get:

-bash: /etc/X11/xorgcfg: No such file or directory

---

### Post by apjone on 2005-11-11
just xorgcfg then , may require you to be root

---

### Post by GabrielWolff on 2005-11-11
[QUOTE=apjone]just xorgcfg then , may require you to be root[/QUOTE]
command not found
neither with sudo xorgcfg (if that's got anything to do with it)

---

### Post by apjone on 2005-11-11
try xorgconfig as well

---

### Post by GabrielWolff on 2005-11-11
[QUOTE=apjone]try xorgconfig as well[/QUOTE]
nothin'
command not found

---

### Post by apjone on 2005-11-11
looks like you have no X windows system, either apt-get X-window* to install the x window system and then apt-get install gnome. you may need to update you apt sources

AJ

---

### Post by GabrielWolff on 2005-11-11
[QUOTE=apjone]looks like you have no X windows system, either apt-get X-window* to install the x window system and then apt-get install gnome. you may need to update you apt sources

AJ[/QUOTE]

As I'll have to leave this machine (and flat) to connect to the web, I just wanna get this really clear: 
I login, and then type:

apt-get X-window (with the *? I guess not, but what does it stand for?)
and then
apt-get install gnome

Is that right?
Thanx again

---

### Post by apjone on 2005-11-11
you will have to be root to run apt-get 
yas you need the * at the end of window this will install all the parts of X and gnome will install the gnome desktop.
If you prefer you can reload(back your data off to cd if you need it)  this is just a way to try and get round the reload part.

---

### Post by GabrielWolff on 2005-11-11
Thanx, I'll try that and come back to whine some more ;-)

Gabriel

---

### Post by tseliot on 2005-11-11
Try this:

sudo apt-get install xserver-xorg

---

### Post by GabrielWolff on 2005-11-11
Hez lads, I think I-m OK here,

What I did was:

sudo dpkg --configure -a

Go figure, but it worked.

Good day

---

### Post by Cas07 on 2005-11-21
I had my keyboard fall out of socket when i was about to choose the resolutions and hit the same problem as described at the command line after restart.

after using the command that gabe mentioned in last post everything was sorted :) 

cheers gabe :D

---

### Post by GabrielWolff on 2005-11-22
[QUOTE=Caos]I had my keyboard fall out of socket when i was about to choose the resolutions and hit the same problem as described at the command line after restart.

after using the command that gabe mentioned in last post everything was sorted :) 

cheers gabe :D[/QUOTE]

Oh yeah!

You are the first Ubuntu user who was helped by me, rather than the other way 'round.

You'll always stay important to me ;)

---

