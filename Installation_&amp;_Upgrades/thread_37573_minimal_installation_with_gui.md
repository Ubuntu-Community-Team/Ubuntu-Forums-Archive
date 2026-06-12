---
title: "minimal installation with gui?"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by madmetal on 2005-05-27
i got 1.2gb hdd.
is there a way to install ubuntu 5.04 with gui?
if it is usefull i already got ubuntu install in command line only.

---

### Post by cdhotfire on 2005-05-27
put in ur ubuntu disk, then type in server.  After install is done login command based, and then put universe repos.
```

$ sudo pico /etc/apt/sources.list

```

and the remove the &quot;#&quot; in from of the universe repos(the ones that say universe at the end) then do Ctrl+O, press enter, then Ctrl+X, then
```

$ sudo apt-get update
$ sudo apt-get install xterm x-window-system-core gdm xfce4 abiword mozilla-firefox menu

```

then apt-get install anything else u want.  But that should take care of the basics. :-)

good luck.

---

### Post by madmetal on 2005-05-29
[QUOTE=cdhotfire]put in ur ubuntu disk, then type in server.  After install is done login command based, and then put universe repos.
```

$ sudo pico /etc/apt/sources.list

```

and the remove the &quot;#&quot; in from of the universe repos(the ones that say universe at the end) then do Ctrl+O, press enter, then Ctrl+X, then
```

$ sudo apt-get update
$ sudo apt-get install xterm x-window-system-core gdm xfce4 abiword mozilla-firefox menu

```

then apt-get install anything else u want.  But that should take care of the basics. :-)

good luck.[/QUOTE]
 the modem is not recognized and i cannot make an internet connection to apt-get the packages.
how can i download the packages from another pc copy them to a cd and install them from tha cd?
the ubuntu cd 5.04 got this staff? 
any suggestions are wellcomed.

---

### Post by cdhotfire on 2005-05-30
hmmm, i dont know youd have to check all dependencies of those files, and that will not take an hour or two.:???:

Maybe someone else has a better suggestion.

---

### Post by nicholaspaul on 2005-05-30
I have a clearer suggestion....

1. insert Ubuntu disc (if you need help with getting the ISO on a disc, let me know)
2. At the main screen (the first one) type 'server', hit ENTER 
3. When all is done, and you are at the prompt - something like :> cdhotfire@ubuntu:~$ 
type: > sudo nano /etc/apt/sources.list 
(enter password)
sudo apt-get update
(enter password)
sudo apt-get install xterm x-window-system-core gdm xfce4 abiword mozilla-firefox menu
(enter password)

This will give you the basics for running Ubuntu and the XFCE4 desktop. On my system ( I finished this install about 5 minutes ago!) it took up 575Mb. Perfect for a networked mp3 player with speakers!

** EDIT**
Damn, I just realised that you need this on CD... best way might be to get an ISO of an existing install. Of course, you'd have to ask someone else, but that would be your next clue.

---

### Post by madmetal on 2005-05-30
thanx for the reply.
i find it there is a bit difficult to make it through without a net connection.
i have 2 solutions.
1) i establish an net connection.
2) i'll find a bigger hdd..

if anyone had another solution wellcomed... :)

---

### Post by tread on 2005-05-30
You said you have another pc? If that has ubuntu, you can download and install these packages there and just copy the cached packages onto a cd .. 

By that I mean apt-get caches all packages downloaded .. its somewhere in /var .. so you can get them from there.

---

### Post by cdhotfire on 2005-05-30
[QUOTE=nicholaspaul]I have a clearer suggestion....

1. insert Ubuntu disc (if you need help with getting the ISO on a disc, let me know)
2. At the main screen (the first one) type 'server', hit ENTER 
3. When all is done, and you are at the prompt - something like :
type: 
This will give you the basics for running Ubuntu and the XFCE4 desktop. On my system ( I finished this install about 5 minutes ago!) it took up 575Mb. Perfect for a networked mp3 player with speakers!

** EDIT**
Damn, I just realised that you need this on CD... best way might be to get an ISO of an existing install. Of course, you'd have to ask someone else, but that would be your next clue.[/QUOTE]

Sir?

i just posted this.

---

### Post by cdhotfire on 2005-05-30
[QUOTE=tread]You said you have another pc? If that has ubuntu, you can download and install these packages there and just copy the cached packages onto a cd .. 

By that I mean apt-get caches all packages downloaded .. its somewhere in /var .. so you can get them from there.[/QUOTE]

i was gonna suggest this, but it could get troublesome for him.:???:

---

### Post by nicholaspaul on 2005-05-31
[QUOTE=cdhotfire]Sir?

i just posted this.[/QUOTE]

I was just trying to make it even clearer.

---

### Post by madmetal on 2005-05-31
[http://ubuntuforums.org/showthread.php?t=38113](http://ubuntuforums.org/showthread.php?t=38113)

a solution like this is what you both suggested,.
i'll give a try...
i couldn't find the appropriate packages here
[http://packages.ubuntu.com/warty/](http://packages.ubuntu.com/warty/)

sites with the packages you suggested?

nicholaspaul did you apt-get the packages?

---

### Post by madmetal on 2005-05-31
[QUOTE=madmetal][http://ubuntuforums.org/showthread.php?t=38113](http://ubuntuforums.org/showthread.php?t=38113)

a solution like this is what you both suggested,.
i'll give a try...
i couldn't find the appropriate packages here
[http://packages.ubuntu.com/warty/](http://packages.ubuntu.com/warty/)

sites with the packages you suggested?

nicholaspaul did you apt-get the packages?[/QUOTE]
 too lazy me....

xfwm4 (4.0.5-1) [universe] 
window manager of the XFce project 

i guess this is the gui you suggested..?

---

### Post by madmetal on 2005-05-31
too lazy me....

xfwm4 (4.0.5-1) [universe] 
window manager of the XFce project 

i guess this is the gui you suggested..?

---

### Post by madmetal on 2005-05-31
too lazy me.... 

xfwm4 (4.0.5-1) [universe] 
window manager of the XFce project 

i guess this is the gui you suggested..?

---

### Post by nicholaspaul on 2005-06-01
[QUOTE=madmetal]

nicholaspaul did you apt-get the packages?[/QUOTE]
I certainly did. I just un-commented /etc/apt/sources.list and updated.

---

