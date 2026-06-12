---
title: "xsession-errors in Lucid"
date: 2009-11-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-05
For me, so far, Lucid seems pretty good, having installed over 110 updates. I seem to be getting a large number of warnings/errors in my .xsessions-errors file which is attached, but don't see any errors/crashes occurring on the desktop.
At least one python file looks suspect.
Comments...

---

### Post by VMC on 2009-11-05
> **Kevbert said:**
> For me, so far, Lucid seems pretty good, having installed over 110 updates. I seem to be getting a large number of warnings/errors in my .xsessions-errors file which is attached, but don't see any errors/crashes occurring on the desktop.
At least one python file looks suspect.
Comments...

110! I've only received 87 updates so far. I have similar error messages in my xsession log.

---

### Post by skep on 2009-11-05
> **VMC said:**
> 110! I've only received 87 updates so far. I have similar error messages in my xsession log.


Just got another big chunk of updates..now alltogether 179 updates...

---

### Post by Kevbert on 2009-11-05
Just try updating again. Received 64 updates earlier today and then another 9 a few minutes ago (I'm on the main UK server).

---

### Post by VMC on 2009-11-05
How are you guys updating or upgrading. Like so

sudo aptitude update && sudo aptitude full-upgrade (aptitude/apt)

Strange thing is. aptitude manual says full-upgrade has replace dist-upgrade, but kept for historical reasons.

If I do:

```
sudo aptitude update && sudo aptitude full-upgrade

```
nothing

If I do

```
sudo aptitude dist-upgrade

```
Then I get updates?!

---

### Post by cariboo on 2009-11-05
At this point in time if I use aptitude, I use the safe-upgrade option. I normally use synaptic for upgrades.

---

### Post by Kevbert on 2009-11-05
But does Synaptic work at the moment ? (not for me). I'm using
```
sudo apt-get update
sudo apt-get upgrade
```
I'm not too worried about breakages (the more the better), hence I'm not using the recommended safe-upgrade option.

---

### Post by VMC on 2009-11-05
> **Kevbert said:**
> But does Synaptic work at the moment ? (not for me). I'm using
```
sudo apt-get update
sudo apt-get upgrade
```
I'm not too worried about breakages (the more the better), hence I'm not using the recommended safe-upgrade option.

Yes doing it that way I get updates. If I try. 'sudo aptitude update && sudo aptitude full-upgrade', it just report there are x amount of updates available.

---

### Post by ranch hand on 2009-11-05
> **cariboo907 said:**
> at this point in time if i use aptitude, i use the safe-upgrade option. I normally use synaptic for upgrades.
+1

---

### Post by seeker5528 on 2009-11-05
> **Kevbert said:**
> But does Synaptic work at the moment ? (not for me). 

Synaptic works fine for me, and is my preferred manager, but aptsh makes a good addition to the repertoire.

[http://aptsh.berlios.de/howto.html](http://aptsh.berlios.de/howto.html)

As for .xsession-errors, I got a lot listed in there, but almost all:

[code]** (gnome-settings-daemon:2530): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:2751): WARNING **: Connection failed, reconnecting...[/quote]

I'm assuming one of these is because I don't have pulseaudio installed and the volume-control is looking for that and that one will go away now that I took the volume control out of my startup applications. 


Later, Seeker

---

### Post by DougieFresh4U on 2009-11-05
> **VMC said:**
> How are you guys updating or upgrading. 

I have always used 
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

