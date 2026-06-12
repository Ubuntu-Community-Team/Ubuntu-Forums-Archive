---
title: "Screensaver - who's to blame?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-10-21
Me - the user? The screensaver or some other app which is supposed to figure out when the screensaver is not welcome?
Folks, when I'm watching fullscreen movie the screensaver still kicks in.
Also, during Ubuntu installation - it also kicks in, makes the user scared cause the screen goes completely black.
What's your thoughts? Is it supposed to be a "papercut"?

---

### Post by Rubino on 2009-10-21
The app that wants to disable the screensaver.
In the case of a movie player the app should also be savvy enough to work out when to disable the screensaver when needed - but to reactivate it when the movie is over (for when the wench falls asleep and the movie finishes).

---

### Post by 23meg on 2009-10-21
> **froggyswamp said:**
> Me - the user? The screensaver or some other app which is supposed to figure out when the screensaver is not welcome?

The application which doesn't inhibit the screensaver is to blame. File bug reports in all applications which have to, but don't.

> **froggyswamp said:**
> Folks, when I'm watching fullscreen movie the screensaver still kicks in.

Which application?

[QUOTE=froggyswamp]Also, during Ubuntu installation - it also kicks in, makes the user scared cause the screen goes completely black.[/QUOTE]

That's [bug #209410]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/209410") (does not happen in all cases).

---

### Post by ranch hand on 2009-10-21
This is interesting.  I have had this "problem" with 8.04 to 9.10.  Never realized it was a bug.

I just turn off the screensaver until I am done.

I will have to look into this some more when I get a chance.

---

### Post by inportb on 2009-10-21
Some apps simulate mouse/keyboard activity from time to time to discourage the screensaver; it's an ugly hack but it works. VLC used to do that, but it's not working.

---

### Post by jblackhall on 2009-10-21
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/381116](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/381116) if you're talking about totem.

---

### Post by philinux on 2009-10-21
I've bugged firefox.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/457254](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/457254)

If anybody would care to confirm it cheers.

---

### Post by jblackhall on 2009-10-21
marked as dupe since that appears to be a known flash bug.  feel free to unmark if you feel it's different.  This is a bug that really should be fixed in 10.04.  I thought perhaps it could be a papercut if that project comes back.

---

### Post by Seventh Reign on 2009-10-21
Example:  Watching Video on Hulu.com.  I dont mind having to tap my mouse every few minutes when the screen goes black.  What annoys me is that it causes the screen to come out of Fullscreen mode and I end up missing part of the show while I re enable Fullscreen.

---

### Post by Longinus00 on 2009-10-22
> **philinux said:**
> I've bugged firefox.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/457254](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/457254)

If anybody would care to confirm it cheers.

Isn't this a problem with adobe flashplayer? Shouldn't you be filing bugs to them? Outside of some ugly hacks (just disable screensaver if there is any flash on the page), I'm not sure what exactly we can do about it.

---

### Post by Cope57 on 2009-10-22
What is a screensaver? 

Try using the monitor power button.

---

### Post by kestal on 2009-10-22
Indeed... I experience this problem on Windows as well, so I do not think this is Ubuntu specific ^_^ It would probably be adobe flash, or firefox to bug about. Had this happen to me while full-screened on Megavideo.

> **Cope57 said:**
> What is a screensaver? 

Try using the monitor power button.

Thats typical of someone to say. People DO still use screensavers, for various reasons. Did you even read this thread -at all-? What does the power button have to do with a screensaver interrupting full-screened video. Common sense. really. -_-.

Edit: I know about what they used to be used for. Regardless, what if he is using a crt monitor? Also, if they are so pointless, why does osx bother to market their os with fairly decent/eye-pleasing ones to add to the user experience? Do not underestimate something as small as a screensaver because you do not use it. Others do. Its trivial for you to even bring up that argument, but thats a different topic all together, not in here.

---

### Post by Cope57 on 2009-10-22
Screensavers were used to save the screen of a CRT monitor from images being burned into them.  Now that most use LCD screens, they are useless now, except to entertain us.

If the screensaver is disabled, then the screensaver issue would not be an issue. Powering down the monitor after use, is the solution when finished with it.

---

### Post by 23meg on 2009-10-22
Please keep on topic.

---

### Post by ranch hand on 2009-10-22
No, I think he has a point.  If you are not running a screen saver you won't have this problem.  If you are away from your machine, shut down your monitor or (radical) rip yor power company off and shut the box down.

I am going to fool with this to see what it is about, but when it is solved or makes sense to me, I will disable the screen saver again.  They just irritate me when they come on, anytime they come on.

Yes folks use them.  that is fine.  Not using one is a cure for this problem, maybe not a popular one.  

I am sure that there is another one and that we will find it.

---

### Post by bedhead75 on 2009-10-22
I find that Caffeine works very well.

[http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html](http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html)

---

### Post by kestal on 2009-10-22
> **bedhead75 said:**
> I find that Caffeine works very well.

[http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html](http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html)

That actually looks really handy and easy to use (especially to somewhat workaround the problem until the actual bug is fixed), are there any hiccups while using this in Karmic thus far?

---

### Post by bedhead75 on 2009-10-22
Somewhere, I forgot where, I heard it was supposed to be in Karmic by default.  I guess in the repos.  It's a cute application that hasn't failed me yet in Jaunty.

---

### Post by ene_dene on 2009-10-23
Since upgraded to Karmic Koala I have this problem with VLC.

---

### Post by Master One on 2009-10-28
Same issue here. Just installed Ubuntu 9.10-RC + UNR on my Asus Eee PC 901GO yesterday, and added a manually compiled MPlayer + SMPlayer from SVN afterwards. The option "Disable screensaver on playback" is set, but the screensaver nevertheless kicks in. I have disabled the screensaver now, but this is surely not the intended behavior, and can not just be blamed on the different apps trying to disable it temporarily.

---

### Post by Squonk07 on 2009-10-28
Oddly (and frustratingly) enough, when I try to disable the screen saver via GUI, it doesn't work (I'm using Gnome). It blanks the screen (default black screen) after ten minutes no matter what I do. I've attacked Power Management, too, and I can't figure out what's going on. I imagine there's a CLI approach to this and if so I intend to find it. Anybody got any ideas?

EDIT: gconf-editor is no help, either. It simply ignores every single setting I put into it. The GUI isn't cutting it here.

---

### Post by rvm4000 on 2009-10-28
> **Master One said:**
> Same issue here. Just installed Ubuntu 9.10-RC + UNR on my Asus Eee PC 901GO yesterday, and added a manually compiled MPlayer + SMPlayer from SVN afterwards. The option "Disable screensaver on playback" is set, but the screensaver nevertheless kicks in. I have disabled the screensaver now, but this is surely not the intended behavior, and can not just be blamed on the different apps trying to disable it temporarily.

smplayer just passes the option -stop-xscreensaver to mplayer. But it seems this option doesn't work with all screensavers. This is what the mplayer manpage says:

> 
&#8722;stop&#8722;xscreensaver (X11 only)
	
Turns off xscreensaver at startup and turns it on again on exit. If your screensaver supports neither the XSS nor XResetScreenSaver API please use &#8722;heartbeat&#8722;cmd instead.

And about -heartbeat-cmd:

> 
&#8722;heartbeat&#8722;cmd
	
Command that is executed every 30 seconds during playback via system() - i.e. using the shell.

NOTE: MPlayer uses this command without any checking, it is your responsibility to ensure it does not cause security problems (e.g. make sure to use full paths if "." is in your path like on Windows). It also only works when playing video (i.e. not with &#8722;novideo but works with &#8722;vo null).

This can be "misused" to disable screensavers that do not support the proper X API (also see &#8722;stop&#8722;xscreensaver). If you think this is too complicated, ask the author of the screensaver program to support the proper X APIs.

EXAMPLE for xscreensaver: mplayer &#8722;heartbeat&#8722;cmd "xscreensaver&#8722;command &#8722;deactivate" file

EXAMPLE for GNOME screensaver: mplayer &#8722;heartbeat&#8722;cmd "gnome&#8722;screensaver&#8722;command &#8722;p" file

---

### Post by Master One on 2009-10-29
Thanks for the explanation, rvm4000.

So all that is to do, is to add```
&#8722;heartbeat&#8722;cmd "gnome&#8722;screensaver&#8722;command &#8722;p"
```to Options >> Setup >> Extended >> Options for Mplayer >> Options: in SMplayer then. :)

---

