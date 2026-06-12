---
title: "Clean .iso install of Karmic leaves me without wallpaper ?"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Geweten on 2010-01-06
Hi guys,

I had Ubuntu 9.04 and first let the system do the upgrade to 9.10.
This left me with the "black hole" as in my screen-shot.:)
I figured to do a clean install from a fresh downloaded .iso.
Same...

At first sight everything seems to work, and the update manager says I'm up to date so...

But I always liked the desktop wallpapers Ubuntu added, I wonder where it left ?:confused:

Just letting you know !

---

### Post by Geweten on 2010-01-08
There was an update from generic 16 to 17...
Problem maintains...

---

### Post by mutex023 on 2010-01-08
During the clean install did you format the partitions, or just
selected the existing ones from the previous install ?

---

### Post by Geweten on 2010-01-08
Hi Mutex023, thanks for your interest !

Well I let gparted autoinstall and I believe it formatted the partition again...

But I'm not sure of course ! I cannot remember if there was a question posed ?

Damn good thinking Mutex !

---

### Post by mk1w86 on 2010-01-08
Can you change the wallpaper at all in

System>>Preferences>>Apperance

and select the Background tab? :-s

---

### Post by mikewhatever on 2010-01-08
Well, on the positive side, you get to enjoy a very famous piece of art for free.
[http://lmgtfy.com/?q=black+square](http://lmgtfy.com/?q=black+square)

---

### Post by Geweten on 2010-01-08
Well **mk1w86** ubuntu surely teases me with some nice fotographs, but I don't seem to be in the possibillity to install one... :D

Thanks **Mikewhatever** ! LOL ! Yeaaah I'm an artist ! Gotta tell mom !;)

But the more I nose around the system I might want to try another reinstall because :

1) permissions of user are a pane in the xxx
2) totem and rythmbox cannot slide trough music 
(hmmm which distro had that before ? 6 ?)
3) record in audacity isn't working any more (and I fiddled around believe me !)
4) wanted to reinstall backup mail in evolution and it doesn't work 
(again you should untar and all... crap... , now I'll have to make one file out of two... the recent and former...?!)
5)the wallpaper

I already looked back with sadness at a 9.04 jaunty again. But for some reason this choice is not available on the "official Ubuntu / Canonball-site" any more... :D

worst case scenario : use my 8 iso.
 
Thx guys appreciate your input !

---

### Post by Geweten on 2010-01-08
By the way neat trick Mikewhatever !
In which thread can I learn that ?

Cheers !

---

### Post by mikewhatever on 2010-01-08
> **Geweten said:**
> By the way neat trick Mikewhatever !
In which thread can I learn that ?

Cheers !

If you mean [http://lmgtfy.com/](http://lmgtfy.com/), there isn't much to learn there, just check it out.

As for the wallpapers included with Karmic, you don't need to install them, but select the one you like and it should become your desktop background a second later. Apparently, something is wrong there, not quite sure what.

---

### Post by mk1w86 on 2010-01-09
> I already looked back with sadness at a 9.04 jaunty again. But for some reason this choice is not available on the "official Ubuntu / Canonball-site" any more...

If you do have to go back to Jaunty :( you can download it from here:

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by mk1w86 on 2010-01-09
Someone else is having the same problem: 

[http://ubuntuforums.org/showthread.php?t=1376517](http://ubuntuforums.org/showthread.php?t=1376517)

and after a google search I found this:

[http://www.ode2.com/?p=44](http://www.ode2.com/?p=44)

---

### Post by Geweten on 2010-01-10
Hi guys,

Meanwhile:
For some reason the wallpaper that I picked wasn't installed directly.
Just befor shutdown it flickred up !
At reboot tah dah... There it was !

Thx mk1w86 for showing the way to a trustful 9.04 .iso.
I was already aware too, but I actually wondered why this successful distro is put in the background ?

Thx for your patience ! Gonna study your links now ! ;)

Cheers !

---

### Post by Geweten on 2010-01-10
Yep **mk1w86** good search !  Definitely a bug !
[http://www.ode2.com/?p=44](http://www.ode2.com/?p=44)

MESA...

Think I'm going for a reinstall of 9.04 easier and cleaner than the fix they propose...

The fix may speed up the system, stop the upgrades, graphics (wallpaper)... but will the rest function properly again ? (cohesion ?)
Because as I understand : all packages remain 9.10 except for this Mesa thing...

Maybe Karmic wasn't tested enough to meet a deadline ?
Gonna download the 9.04 iso, but will wait your thoughts befor reinstall !

By the way thanks mikewhatever, can make people think, their browser was hacked for a sec too ! "Wow... what's happening ? I didn't do that !?" ;)

---

### Post by Geweten on 2010-01-11
Pfff... Was working with audacity, when the system crashed.
And : my installed wallpaper has gone and the black hole is there again.

Loggfile:

Jan 10 23:22:30-desktop pulseaudio[1623]: alsa-source.c: Resume failed, couldn't restore original fragment settings. (Old: 65536/65536, New 1073676288/65532)
Jan 10 23:23:38-desktop pulseaudio[1623]: last message repeated 3904 times
Jan 10 23:24:41-desktop pulseaudio[1623]: ratelimit.c: 2 events suppressed
Jan 10 23:24:41-desktop pulseaudio[1623]: alsa-source.c: Resume failed, couldn't restore original fragment settings. (Old: 65536/65536, New 1073676288/65532)
Jan 10 23:26:09-desktop pulseaudio[1623]: last message repeated 3838 times
Jan 10 23:28:11-desktop pulseaudio[1623]: alsa-source.c: Resume failed, couldn't restore original fragment settings. (Old: 65536/65536, New 1073676288/65532)
Jan 10 23:29:12-desktop pulseaudio[1623]: last message repeated 30799 times
Jan 10 23:30:13-desktop pulseaudio[1623]: last message repeated 31183 times
Jan 10 23:30:28-desktop pulseaudio[1623]: last message repeated 7548 times
Jan 10 23:30:28-desktop kernel: [20172.430419] Marking TSC unstable due to cpufreq changes
Jan 10 23:30:28-desktop pulseaudio[1623]: alsa-source.c: Resume failed, couldn't restore original fragment settings. (Old: 65536/65536, New 1073676288/65532)
Jan 10 23:30:28-desktop pulseaudio[1623]: last message repeated 62 times
Jan 10 23:30:28-desktop kernel: Kernel logging (proc) stopped.

---

