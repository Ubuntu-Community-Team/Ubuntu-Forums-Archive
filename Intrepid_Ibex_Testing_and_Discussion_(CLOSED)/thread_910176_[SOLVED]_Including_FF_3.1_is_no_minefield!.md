---
title: "[SOLVED] Including FF 3.1 is no minefield!"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-09-04
Is anyone else using Minefield 3.1b1pre (soon to be Firefox 3.1)? 

I've been testing it out, with Tracemonkey enabled, going to the usual heavy sites (Flash heavy sites, and heavy JS usage like Digg, etc,.)
 _I'm blown away!_
...but not by it's speed - it was always fast - I can't really tell the difference -- I guess it feels a bit snappier.I'm amazed that it's so insanely stable, and works flawlessly with Flash 10. I've not had a single crash (yet), many issues with Flash 10 and weird artifacts are gone (crisp video), the random site crashes aren't happening anymore. 
To be honest, I think this is the first time I've ever felt I'm using a browser that works like it would on windows, it's perfect, and it would be such a shame if it didn't get into Intrepid!

... and it can only get better!

 Forgot to mention, I think I notice slightly better GTK+ integration, but I'm not too sure.
 How could I forget memory footprint, 4 tabs (Flash video, Google, Digg, Ubuntuforums) = ~40 megs
Edit: Couldn't figure out how to add a poll --(THREAD TOOLS!)-- so I made a new thread. 
**Please Post There**

---

### Post by syko21 on 2008-09-04
I can't comment on the gtk integration but the overall feel is a much more responsive web browser.

---

### Post by mc4100 on 2008-09-04
> **syko21 said:**
> I can't comment on the gtk integration but the overall feel is a much more responsive web browser.
By better integration, I mean, the "awesome-bar" suggestions seem to have their URL's colors to match my theme, as does the "awesome-bar" itself when it has focus, like the glow I see in other apps such as nautilus -- I can't remember this being in 3.0, but as I said, I'm not sure.
I'm curious...
[LIST]
[*]Have you had it crash ... do you find it better in that respect than 3.0, or worse?
[*]What's you're experience with flash (whatever version)
[/LIST]

---

### Post by amano on 2008-09-04
Exspecially Firefox got backported to Ubuntu at any time a final version was released.

I cannot think of including a beta (is it even beta?) again after all that bashing that happened with the inlcusion of the firefox 3.0 betas in Hardy Heron.

Just wait for the final Firefox and it will get backported for sure...

And with the current version of firefox in intrepid ibex most flash issues should already be ironed out.

---

### Post by syko21 on 2008-09-04
I made a symlink with the ubuntu installed flash player 10. Even with the pre-beta its noticeably more stable on flash websites. Usually I get a crash when I open a new tab with embedded flash (youtube, addictinggames) but now it just works.

---

### Post by ccw on 2008-09-04
> **mc4100 said:**
> it would be such a shame if it didn't get into Intrepid!

... and it can only get better!


It will be beta come Oct 28 with no firm final release date (late 2008/early 2009). Why the rush? intrepid+1 will be here before you know it.

---

### Post by mc4100 on 2008-09-04
> **amano said:**
> Is it even beta?
No, right now it's at pre-beta

Have you tried it?
I went in with the same mind as you... not-yet-even-beta-expect-catastophes, but that's my point, I don't see any. I'm literally in awe, it feels (with the exception of a bomb as the icon :)) like a final release.


... I probably should say, that there *will* be bugs, waiting till later to show themselves (just like through the Alphas of Intrepid), so I'm not claiming it is perfect. Only that it seems to be a major improvement (fixing important issues, introducing important features), and a far as I can see, doesn't have any major issues ... so if it's going to be fully stable before release (beta or otherwise), why not include it?

---

### Post by plun on 2008-09-04
Well, the TraceMonkey is faster then Chromes V8....:)

[http://arstechnica.com/journals/linux.ars/2008/09/03/new-firefox-javascript-engine-is-faster-than-chromes-v8](http://arstechnica.com/journals/linux.ars/2008/09/03/new-firefox-javascript-engine-is-faster-than-chromes-v8)

FF 3.02 in Ubuntu version is really sleepy.... I saw a strange changelog about "branding"...:confused:

It might be a bad idea to not follow Mozillas stable releases now...

Flash 10 RC is rock solid with [this solution]("http://ubuntuforums.org/showthread.php?t=866965").

---

### Post by mc4100 on 2008-09-04
Wow, anyone using Minefield might want to check out CTRL+TAB, its like a compiz window switcher, but for the browser's *TABS*.

---

### Post by autocrosser on 2008-09-04
How about a link to the download?

---

### Post by plun on 2008-09-04
> **autocrosser said:**
> How about a link to the download?

Its better to use [fta ppa]("https://launchpad.net/~fta/+archive"), IMHO....

You also need symlinks for plugins.....


([Nightly build ]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/"))   just to unpack and run firefox shell script.

---

### Post by mc4100 on 2008-09-04
> **autocrosser said:**
> How about a link to the download?
First, backup your .mozilla folder, then add a new source:
```
deb http://ppa.launchpad.net/fta/ubuntu intrepid main
```
and install firefox-3.1, and firefox-3.1-gnome-support as well.

---

### Post by ubulette on 2008-09-05
> **plun said:**
> Its better to use [fta ppa]("https://launchpad.net/~fta/+archive"), IMHO....

You also need symlinks for plugins.....


hmm, really? my package should already do that for you:

```

$ ls -ld /usr/lib/firefox-3.1*/plugins
lrwxrwxrwx 1 root root 25 2008-09-02 21:53 /usr/lib/firefox-3.1b1pre/plugins -> ../firefox-addons/plugins

```

---

### Post by gjoellee on 2008-09-05
The firefox developers have seen that Flash have had worked badly, and in the next release even if it is 3.0.2 or 3.1 flash should work better, and firefox should not crash as often as it does noe

---

### Post by plun on 2008-09-05
> **ubulette said:**
> hmm, really? my package should already do that for you:

```

$ ls -ld /usr/lib/firefox-3.1*/plugins
lrwxrwxrwx 1 root root 25 2008-09-02 21:53 /usr/lib/firefox-3.1b1pre/plugins -> ../firefox-addons/plugins

```

Yes, symlinks are OK....  (not if you use the nightly build)

---

