---
title: "MPlayer won't play robot movies"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by Afishionado on 2006-07-11
Hello,

I've been trying to convert a friend to Linux who won't switch unless he can play his robot movies under the new OS. :-) I've been playing with XUbuntu 6 at home trying to find a solution.

I have MPlayer installed alright, and can play the movies at compfused.com inside Firefox. So far, so good.

However, the embedded movies here won't play:

[http://www.robotcombat.com/video_battle.html](http://www.robotcombat.com/video_battle.html)

WARNING: DO NOT CLICK THE LINK IF YOU STILL HAVE THE TOTEM PLUGIN INSTALLED. The Totem plugin crashes Firefox pretty hard if you visit that page. You have been warned. :-P

Back to the question, MPlayer buffers the file, plays the first frame, then stops. I hit play again, the first frame shows, then it stops. Same thing if I download the file and run MPlayer outside the browser. (Some of the movies there are RealPlayer files that play just fine, though.) No error message, nothing.

Even more frustrating: The files play just fine out of the box under Vector Linux. However, Vector is just a bit more hard core than my friend is ready to deal with yet, and I don't want to scare him off.

So, ideas? Could it just be something funny with a codec? Any configuration files under the Vector install that I should look at?

Thanks,
William Tracy

---

### Post by angkor on 2006-07-12
No problem here with those videos in mplayer. My guess it's a codec issue.

---

### Post by lordlollo on 2006-07-12
> **angkor said:**
> My guess it's a codec issue.
I agree. Try easyubuntu or automatix.

Cheers.

P.S.: robots & ubuntu? We might start the Rubuntu project... :cool:

---

### Post by Afishionado on 2006-07-12
OK, this is what I tried before I first posted:

On my laptop, with a fresh install of XUbuntu, I ran Easy Ubuntu with all the media options checked. That activated the Totem plugin, and out of frustration I uninstalled all of Totem. I then ran Automatix, installing MPlayer and all the codecs. When that was done, I got the results I described above.

I'm playing again with Automatix on another machine now, to see if maybe I just screwed something up the last time. 

> **lordlollo said:**
> P.S.: robots & ubuntu? We might start the Rubuntu project... :cool:

Some day I would like to port EmulegOS to work with the Debian and Ubuntu BrickOS packages, and rewrite all the dang Tcl/Tk code in GTK.

[http://emulegos.sourceforge.net/](http://emulegos.sourceforge.net/)
[http://packages.ubuntulinux.org/dapper/devel/brickos](http://packages.ubuntulinux.org/dapper/devel/brickos)

Too many projects going already, though...

---

### Post by Afishionado on 2006-07-13
Still the same result. ](*,) 

Any other ideas?

---

### Post by arnieboy on 2006-07-13
> **Afishionado said:**
> Still the same result. ](*,) 

Any other ideas?

did u install AUD-DVDcodecs from automatix?

---

### Post by Afishionado on 2006-07-13
Just to be sure, I installed *everything* that Automatix offers. Now I have such things as Google Earth and Opera on my desktop, but the movies in question still won't play for me.

Does this movie play for anyone else under Ubuntu?
[http://www.robotcombat.com/video_nmfrenzy_lo.html](http://www.robotcombat.com/video_nmfrenzy_lo.html)

---

### Post by angkor on 2006-07-14
> **Afishionado said:**
> Just to be sure, I installed *everything* that Automatix offers. Now I have such things as Google Earth and Opera on my desktop, but the movies in question still won't play for me.

Does this movie play for anyone else under Ubuntu?
[http://www.robotcombat.com/video_nmfrenzy_lo.html](http://www.robotcombat.com/video_nmfrenzy_lo.html)

Hmm, strange that one doesn't play for me yet the longer high res version (the link on the left bottom of the page does play in mplayer.

---

### Post by arnieboy on 2006-07-14
the movies do not play on my laptop as well. Possibly a newer version of quicktime codecs are required.

---

### Post by Afishionado on 2006-07-15
(Sorry, I was out of town a couple days here.)

I honestly can't get either version to play.

Maybe it's time for me to try bypassing the packaging system and installing the codecs manually?

---

