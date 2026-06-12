---
title: "Theme problem..."
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BwackNinja on 2008-07-16
Am I the only one who is having problems with the theme loading? I had it in my last install and now I'm seeing it again. I load the computer up, and I see a blocky old-default-looking theme show up instead of my theme (which is simply the intrepid theme with some colors changed). It is fixed automagically when I open up preferences > appearance, but its kinda odd...

anyone out there?

Also, and though I normally wouldn't expect it to be related (though it happened at the same time both times) my network manager applet thingy in my tray disappeared too.

---

### Post by psyke83 on 2008-07-16
> **BwackNinja said:**
> Am I the only one who is having problems with the theme loading? I had it in my last install and now I'm seeing it again. I load the computer up, and I see a blocky old-default-looking theme show up instead of my theme (which is simply the intrepid theme with some colors changed). It is fixed automagically when I open up preferences > appearance, but its kinda odd...

anyone out there?

You need to be specific. If you mean the Human theme, it won't be installed or included on the CD by default, although it's still in the repository. The Ubuntu themes you can choose from are NewHuman (current default), Human-Murrine and Human-Clearlooks.

---

### Post by BwackNinja on 2008-07-17
Attached is a screenshot of what it looks like, the window  borders are actually the right ones (though the colors are all mixed up). It seems to start up fine at first, but then changes right before everything is finished loading. I use the same theme in hardy (NewHuman) but don't have these problems there.

---

### Post by mitchellcipriano on 2008-07-17
This is the new theme I am seeing now as well. I switched for me with yesterday's updates.

---

### Post by psyke83 on 2008-07-17
> **BwackNinja said:**
> Attached is a screenshot of what it looks like, the window  borders are actually the right ones (though the colors are all mixed up). It seems to start up fine at first, but then changes right before everything is finished loading. I use the same theme in hardy (NewHuman) but don't have these problems there.

That's the fallback theme, which is an indication that there's something wrong with your system. It could be that you let a dist-upgrade/partial upgrade remove vital packages, or there's a bug causing gnome-session not to load properly.

Also, how do you have NewHuman in Hardy, are you using Ken Wimer's PPA?

---

### Post by BwackNinja on 2008-07-17
I'm using some PPA for the NewHuman theme, most likely Ken Wimer's in my Hardy install. I did my upgrading mostly in synaptic, and I've done it twice (after a while, the first one just died...). The second time I installed, I did it from an intrepid alternate install cd and upgraded from there, and the only packages that were removed were xserver-video-imstt and one other one like it (I don't quite remember). My display works fine, and it doesn't happen all the time (which only makes it weirder).

---

### Post by wlake on 2008-07-17
Yes, I get the theme problem. What I have to do is Ctrl-Backspace and log back in and my theme then shows up. I am using the Mythbuntu theme.

---

### Post by mitchellcipriano on 2008-07-17
> **psyke83 said:**
> That's the fallback theme, which is an indication that there's something wrong with your system. It could be that you let a dist-upgrade/partial upgrade remove vital packages, or there's a bug causing gnome-session not to load properly.

Also, how do you have NewHuman in Hardy, are you using Ken Wimer's PPA?

When I ran the update manager it said I had to do a partial update. Should I do a reinstall of Alpha 2? I was able to restore the dark theme by going to the appearance preference.

---

### Post by eeclark on 2008-07-18
Same here...and my compiz settings "Desktop Effects" get turned off everytime I shutdown.
I have to reselect it everytime I reboot.

---

### Post by mitchellcipriano on 2008-07-18
When I do an update the ubuntu-desktop update is grayed out and not selected. It will not allow me to select it. Is this a bug? Or should I just reinstall and forget it?

---

### Post by BwackNinja on 2008-07-18
do it in synaptic, its just that it is replacing scrollkeeper with something else, update manager seem to allow installation of extra packages.

---

### Post by psyke83 on 2008-07-18
> **BwackNinja said:**
> do it in synaptic, its just that it is replacing scrollkeeper with something else, update manager seem to allow installation of extra packages.

DO NOT do that. Forcing a held-back package is almost always a dangerous idea. Unless the new package "rarian-compat" is going to be a 100% replacement of scrollkeeper, your system will break by forcing this action.

Even *if* rarian-compat is going to replace scrollkeeper, it may be held back because it's not *ready* to replace it yet. I suggest both of you do some more research on the development release. Here is a good start: [http://ubuntuforums.org/showthread.php?t=852857](http://ubuntuforums.org/showthread.php?t=852857)

---

### Post by BwackNinja on 2008-07-18
I remember reading a guide about how to replace scrollkeeper with rarian a long time back. It is hard to argue with possibilities, because technically there's the possibility of rarian-compat not being ready to replace scrollkeeper. Just like the updated xserver-xorg-core, it didn't want me upgrading it from update-manager, but I was easily able to update it from synaptic with no breakages (unless of course any of my problems are somehow related to it. Possible, no real way for me to be sure.) Scrollkeeper deals with documentation and as such, the worst that could possibly happen (likely at least) is that you have problems with your man-pages.

I may not be the best guide with this, but as far as I see, nothings broken for me.

---

### Post by psyke83 on 2008-07-18
> **BwackNinja said:**
> I remember reading a guide about how to replace scrollkeeper with rarian a long time back. It is hard to argue with possibilities, because technically there's the possibility of rarian-compat not being ready to replace scrollkeeper. Just like the updated xserver-xorg-core, it didn't want me upgrading it from update-manager, but I was easily able to update it from synaptic with no breakages (unless of course any of my problems are somehow related to it. Possible, no real way for me to be sure.) Scrollkeeper deals with documentation and as such, the worst that could possibly happen (likely at least) is that you have problems with your man-pages.

I may not be the best guide with this, but as far as I see, nothings broken for me.

Yep, you're right. It does appear to be a replacement, and all the previous scrollkeeper-* commands are symlinked to the new rarian-* commands. The problem is that none of these commands (-update, -rebuilddb, etc) seem to do anything at all... So it may not be ready, as I said. 

Generally speaking, forcing a held back package to install can often cause users to lose a lot of vital packages, and when I saw it being mentioned in this thread, I thought it would be best to give some warning ;).

---

