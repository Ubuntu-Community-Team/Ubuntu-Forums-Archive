---
title: "Anyone got Electric Sheep working on Lucid?"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mazz0 on 2010-03-09
Anyone got Electric Sheep working on Lucid?

---

### Post by cariboo on 2010-03-09
A bump for the move

---

### Post by |{urse on 2010-03-09
HAaha I freakin love those screensavers! 
I'll be watchin this to find out if anyone figures out how.

---

### Post by Anduu on 2010-03-09
Have you tried the script from [http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51) or the PPA ?

It works for me.

---

### Post by wilee-nilee on 2010-03-10
> **Anduu said:**
> Have you tried the script from [http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51) or the PPA ?

It works for me.

I downloaded the site link and it works in mplayer with a code prompt, how does it link to screensavers?

---

### Post by Anduu on 2010-03-11
> **wilee-nilee said:**
> I downloaded the site link and it works in mplayer with a code prompt, how does it link to screensavers?

Sorry to have left you hanging there but I needed to do some digging to remember which way I got it working :P

Use the PPA
```
deb http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main 
deb-src http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main 

```

Unfortunately the latest Ubuntu version it supports is Intrepid but it should install and function correctly in Lucid :)

---

### Post by wilee-nilee on 2010-03-11
The ppa installed to the screensaver, thanks.

---

### Post by Kevbert on 2010-03-11
It doesn't install for me via Synaptic on 10.04. I get a dependency problem:
> electricsheep:
 Depends: libjpeg-progs but it is not going to be installed
So the PPA is the best bet.

---

### Post by ikt on 2010-03-11
> **Kevbert said:**
> It doesn't install for me via Synaptic on 10.04. I get a dependency problem:

So the PPA is the best bet.

Indeed, that is a recent development, the fix should be incoming soon to make it so installing from synaptic will work.

[https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/535629](https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/535629)
[https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/537370](https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/537370)

---

### Post by ikt on 2010-03-13
Just to let you know the issue is fixed and electricsheep should install now just by doing

```
sudo apt-get install electricsheep
```

cheers

---

### Post by CylnZ on 2010-03-19
> **ikt said:**
> Just to let you know the issue is fixed and electricsheep should install now just by doing

```
sudo apt-get install electricsheep
```cheers

Yep, this worked first try.Run the config "electricsheep-preferences" in a terminal and set your nick and test the connection or set your vid prefs. Works great. :)

---

### Post by mazz0 on 2010-04-24
Ooh, it's in the Software Centre now!

Next, to get it working with [Shantz XWinWrap]("http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap")...

---

### Post by mazz0 on 2010-04-24
OoooOOoooh!!!
```
xwinwrap -ov -fs -- electricsheep -window-id WID
```
AWESOME!!!!!
One issue though, it doesn't start till you click on the background.

---

### Post by ixlam on 2010-04-27
Here's a modified script I use to toggle xwinwrap ON and OFF (#with a few optional presets#) on Lucid.

```


#!/bin/bash

if pidof xwinwrap | grep [0-9] > /dev/null
then
exec killall xwinwrap 
else
exec nice -n 10 xwinwrap -ni -sp -fs -st -b -o 0.5 -- electricsheep -window-id WID
fi

#exec nice -n 10 xwinwrap -ni -sp -ov -fs -st -b -o 0.5 -- electricsheep -window-id WID
#exec nice -n 10 xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/skytentacles -root -window-id WID
#exec nice -n 10 xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glmatrix -root -window-id WID -density 10
#exec nice -n 10 xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/lament -root -window-id WID


```

I put the script in my home folder and named it .xwintoggle to keep it hidden...
then I created a launcher in my dock for easy one click use
.
As it is above, I can still see and use my desktop launchers, shortcuts, screenlets etc.

PS..I did have Xwinwrap/DreamAquarium working with wine. Although I am not sure if the follwing will work since upgrading. *change USERNAME to your user*

```


exec nice -n 10 xwinwrap -ni -fs -s -st -sp -nf -b -- env WINEPREFIX="/home/USERNAME/.wine" wine /home/USERNAME/.wine/drive_c/windows/Dream_Aquarium.scr -window-id WID


```

---

