---
title: "A few &quot;minor&quot; post-install quirks."
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by sk545 on 2005-08-02
Installed Ubuntu, and things seem to be working fine.  Thx to Ubuntuguide, it didn't take long to get most things working.

However, two things are bothering me right now:

1)  I cannot change the brightness/hue/contrast in mplayer or kaffeine.  Mplayer just gives this:

Video attribute 'contrast' is not supported by selected vo & vd. 0 55%
Video attribute 'brightness' is not supported by selected vo & vd. 48%
Video attribute 'hue' is not supported by selected vo & vd..2% 0 0 48%
Video attribute 'saturation' is not supported by selected vo & vd. 48%

I do have mplayer -vo set to xv.  Could it have something to do with Nvidia drivers (7667 from nvidia's website) or X.org extension not being enabled?

2) When i run 'gedit' and start typing, it never automatically goes to the next line.  I have 'word-wrap' enabled in gedit, but even after that, if i type, i get one single long line unless i press enter to go to the next line.

Thats it for now...i am sure other things will come up.

Thanks.

---

### Post by kassetra on 2005-08-03
[QUOTE=sk545]Installed Ubuntu, and things seem to be working fine. Thx to Ubuntuguide, it didn't take long to get most things working.

However, two things are bothering me right now:

1)  I cannot change the brightness/hue/contrast in mplayer or kaffeine. 

2) When i run 'gedit' and start typing, it never automatically goes to the next line.[/QUOTE]

1. What does your /etc/mplayer/input.conf look like?  
Here is mine:
[font=verdana, arial, helvetica][size=2]1 contrast -1
2 contrast 1
3 brightness -1
4 brightness 1
5 hue -1
6 hue 1
7 saturation -1
8 saturation 1

You might also want to try running mplayer from a command line with this command:
 ```
[/size][/font][font=verdana, arial, helvetica][size=2] mplayer -vf eq=20:50 your_movie.mpg[/size][/font][font=verdana, arial, helvetica][size=2]
``` (20:50 is brightness : contrast ration - it starts at 100:100 which is full saturation.)  You can also add the vf options to your ~/mplayer/.conf file.

2. That is very odd.  Are you running gedit from the command line or from the menu?
[/size][/font]

---

### Post by sk545 on 2005-08-03
> 1. What does your /etc/mplayer/mplayer.conf look like? 
Looks exactly the same as yours.  I put in vf = eq=20:50 in  /etc/mplayer/mplayer.conf.  The brightness/contrast work now, however no saturation/hue yet.  Any way to pass some paramater to xine to achieve this?  I use kaffeine plugin to see all the movie trailers and really miss the brightness setting.
> 2. That is very odd. Are you running gedit from the command line or from the menu? 
Same behaviour no matter where gedit is run from.

Thx.

---

### Post by sk545 on 2005-08-06
so, anyone know how to set the brightness in xine manually?  I mean it really kinda sucks not being able to do it...:(

---

