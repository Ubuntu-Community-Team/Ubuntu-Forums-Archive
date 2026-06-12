---
title: "Can't start X"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by pixel80r on 2006-04-19
I followed the instructions at 
[https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28low%29%7C%28memory%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28low%29%7C%28memory%29)

to insatll fluxbox on a ubuntu server install using the command:
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic

When I type startx i get an error:
Xsession: unable to start X session---no "/home/username/.xsession" file, now "/home/username/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

Any ideas how or where to find a fix?
tx.

---

### Post by henriquemaia on 2006-04-19
[QUOTE=pixel80r]I followed the instructions at 
[https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28low%29%7C%28memory%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28low%29%7C%28memory%29)

to insatll fluxbox on a ubuntu server install using the command:
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic

When I type startx i get an error:
Xsession: unable to start X session---no "/home/username/.xsession" file, now "/home/username/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

Any ideas how or where to find a fix?
tx.[/QUOTE]

Verify permissions of your home folder. Your username is "username"?

---

### Post by NetMatrix on 2006-04-19
You also have to install X

```
sudo apt-get install xserver-xorg
```

---

### Post by pixel80r on 2006-04-20
[QUOTE=NetMatrix]You also have to install X

```
sudo apt-get install xserver-xorg
```[/QUOTE]
Xserver is already istalled so that cant be it.

apt-get install result is "xserver-xorg is already the newest version"

??

what should the permissions be set to for the home folder?
(no, the user name is not "username". I just used that for an example)

---

### Post by NetMatrix on 2006-04-21
Change the permissions on the startup script to 755 ie

```
chmod 755 startup  or
sudo chmod 755 startup   if you compiled it as root
```

I had that problem with mine.

---

### Post by NetMatrix on 2006-04-21
the startup script should be in /home/*youruser*/.fluxbox and is should be called startup.

---

### Post by NetMatrix on 2006-04-21
This link may provide some help also:

[http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox]("http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox")

---

### Post by pixel80r on 2006-04-21
[QUOTE=NetMatrix]This link may provide some help also:

[http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox]("http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox")[/QUOTE]


Netmatrix, thanks for all the replies. I'll have a go at it and let you know how it works out.

Thanks!!

---

### Post by vigos on 2006-04-22
Pixel, you might also have some problems with xdm as I'm having problems myself. But you should still be able to start up fluxbox ok

See this [thread]("http://ubuntuforums.org/showthread.php?t=131455&highlight=xdm") and this [thread]("http://ubuntuforums.org/showthread.php?t=162755&highlight=xdm") for more information.

---

### Post by pixel80r on 2006-05-03
[QUOTE=vigos]Pixel, you might also have some problems with xdm as I'm having problems myself. But you should still be able to start up fluxbox ok

See this [thread]("http://ubuntuforums.org/showthread.php?t=131455&highlight=xdm") and this [thread]("http://ubuntuforums.org/showthread.php?t=162755&highlight=xdm") for more information.[/QUOTE]

Hey, now that is looking a lot like what i'm experiencing.  I removed the packages with apt-get and then installed again before checking back to this post. When I type "startx" it looks like it wants to start, goes to a grey screen with the "X" cursor and then kicks back out to the command screen.

It's not really an urgent need for me right now. I'm running the server install (base) with no GIU for now. I just figured I'd install something lightweight that I could start manually when I wanted a GUI instead of only command.

Thanks Vigos

---

