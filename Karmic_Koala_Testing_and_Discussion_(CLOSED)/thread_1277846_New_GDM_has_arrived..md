---
title: "New GDM has arrived."
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-09-28
The new gdm has arrived and it looks nice with the throbber.I have the wallpaper with the moth, butterfly, what ever it is and it looks good with all of the other new artwork. I think this is getting competitive with the MacOS.

I would go as far as to say that this is really art. Ubuntu has managed to maintain it's integrity and make good use of it's color scheme. If the default wallpaper was the one I mentioned or something with a similar effect the default artwork would be perfect. Let me say that I am not a fan of brown but I really like the way color is being used for this release. 

My compliments to the artwork team.

---

### Post by Squonk07 on 2009-09-28
Now *that's* classy. :) They even got the transition to my wallpaper right now, with a smooth fade revealing a fully-loaded and functional desktop. I know that all the loading is really happening behind the screen with the throbber, but it's still an excellent effect and gives the impression of a speedier system.

The login box looks, dare I say it, slightly OS X-ish, but that's a good thing. Ah, elegance...coming to an Ubuntu Karmic install near you.

---

### Post by exploder on 2009-09-28
> The login box looks, dare I say it, slightly OS X-ish, but that's a good thing. Ah, elegance...coming to an Ubuntu Karmic install near you.

I agree, I am reminded of the style of the MacOS on my daughters MacBook Pro. The MacOS is noted for it's stunning looks and Ubuntu is finding a style that provides elegance and maintains it's roots.

---

### Post by Darkshade on 2009-09-28
I don't see any difference at all. (?)
Could you post a screenshot please :)

---

### Post by kzutter on 2009-09-28
deleted...

---

### Post by Squonk07 on 2009-09-28
Removed.

---

### Post by joey-elijah on 2009-09-28
I'm not even sure if i'm seeing the same as anyone else anyway! A week or so back i manually selected the GDM theme/icons etc and i've not noticed many changes since... :S 

Is it the Xsplash background with a sleek light grey dialogue window and taskbar? Or am i really missing!?

---

### Post by swj on 2009-09-28
I received 2 gdm updates today. The background is now dark. The login box looks the same...I'm hoping it will change.

Does anyone know how to turn the drum beat off?

---

### Post by graaant on 2009-09-28
Unticking Gnome Login Sound in Preferences > Startup Applications should stop it.

---

### Post by joey-elijah on 2009-09-28
> **swj said:**
> I received 2 gdm updates today. The background is now dark. The login box looks the same...I'm hoping it will change.

Does anyone know how to turn the drum beat off?

Programme some missiles in it's general direction?! 

Seriously: -

terminal : 
cd /usr/share/sounds/ubuntu/stereo

The sound it plays is system-ready.ogg, which is just a symbolic link to dialog-question.ogg, so find another ogg file you want, & (using button-toggle-off.ogg as an example)...

sudo rm system-ready.ogg

sudo ln -s button-toggle-off.ogg system-ready.ogg

If you have another ogg file & want to use that then just...

sudo ln -s /path/to/your.ogg system-ready.ogg

---

### Post by swj on 2009-09-28
Thanks for both solutions!

---

### Post by joey-elijah on 2009-09-28
> **graaant said:**
> Unticking Gnome Login Sound in Preferences > Startup Applications should stop it.

Soh beaten to it - and with the easy solution, too!

---

### Post by Mr. Picklesworth on 2009-09-28
Yay! The transitions are all pretty slick :)
It isn't exactly what the mockup had, (yet) but I think I prefer it this way since it's closer to what we see after logging in, in a real working desktop. (On a similar note, that's what drives me crazy with kde4. All the screenshots showing how beautiful it is involve Plasma and the login experience. Then, once you actually start using the thing you realize that the meat of it - actual applications like DigiKam and Kontact - it's the same old ugly, albeit with a pretty nice UI toolkit. Uhh... back to your regular programming: ).

For some reason GRUB started appearing at startup (and I get a text console there, either), but it's just about flicker-free and beautiful.

On that topic, anyone know why we drop to a console with a blinking cursor at the top left for the last second or so of shutting down? It seems mighty silly.


Edit: I should clarify, with regards to the side point that I honestly didn't intend to eat this whole post, that I don't think the meat of KDE is ugly in particular. Everything is similarly ugly, but the pictures of Air brought my hopes up.

---

### Post by joey-elijah on 2009-09-28
> **Mr. Picklesworth said:**
> Yay! The transitions are all pretty slick :)
It isn't exactly what the mockup had, (yet) but I think I prefer it this way since it's closer to what we see after logging in, in a real working desktop. (**On a similar note, that's what drives me crazy with kde4. All the screenshots showing how beautiful it is involve Plasma and the login experience. Then, once you actually start using the thing you realize that the meat of it - actual applications like DigiKam and Kontact - it's the same old ugly, albeit with a pretty nice UI toolkit. Uhh... back to your regular programming: **).

For some reason GRUB started appearing at startup (and I get a text console there, either), but it's just about flicker-free and beautiful.

On that topic, anyone know why we drop to a console with a blinking cursor at the top left for the last second or so of shutting down? It seems mighty silly.

Quite possibly the best surmise of KDE i've ever read!

---

### Post by Darkshade on 2009-09-28
Seriously, could someone post a screenshot of it?

---

### Post by joey-elijah on 2009-09-28
> **Darkshade said:**
> Seriously, could someone post a screenshot of it?

*sigh* If only i knew how to! xnest doesn't seem to work anymore and gdmtesterthingy isn't part of the new GDM :(

---

### Post by Merk42 on 2009-09-28
Still can't figure out how this 'attach' thing works...

[ATTACH]130130[/ATTACH]

---

### Post by Darkshade on 2009-09-28
Thanks, Merk42! Can't say I'm impressed but it's a step forward I guess :)

---

### Post by Longinus00 on 2009-09-29
I have a new and fun bug you guys can help me verify! On the gdm facebrowser, click your username but don't enter your password yet. Instead, click the blue accessibility icon on the bottom and then close it (don't enable any options). Watch in wonder as you can no longer enter your password!

---

### Post by Darkshade on 2009-09-29
> **Longinus00 said:**
> I have a new and fun bug you guys can help me verify! On the gdm facebrowser, click your username but don't enter your password yet. Instead, click the blue accessibility icon on the bottom and then close it (don't enable any options). Watch in wonder as you can no longer enter your password!

Awesome! :lolflag:

---

### Post by wfp on 2009-09-29
Oh please looks the same as alpha 4.

---

### Post by Squonk07 on 2009-09-29
> **Longinus00 said:**
> I have a new and fun bug you guys can help me verify! On the gdm facebrowser, click your username but don't enter your password yet. Instead, click the blue accessibility icon on the bottom and then close it (don't enable any options). Watch in wonder as you can no longer enter your password!

I will have to test this out, but right now I'm embroiled in Facebook Chat. I'll add my confirmation to the chorus if I can reproduce this result myself.

EDIT: Yep, it sure does this. It's not a show stopper in that you can just click Cancel and pick your account from the list again, but it's an almost cute bug. ;)

---

### Post by Visceral Monkey on 2009-09-29
...wtf people, it's just a background change. Nothing to see here.

---

### Post by Squonk07 on 2009-09-29
> **Visceral Monkey said:**
> ...wtf people, it's just a background change. Nothing to see here.

As I mentioned in one of the threads about this, the method of selecting which image gets used for the GDM background has changed slightly from before (probably because it's not using the default wallpaper as the GDM background anymore), so there's a little more going on here than a background change. Everything is a lot smoother and polished, too. Hopefully the devs won't alter the system too much now that they've got the seamless transitions going well.

The way I see this it's more of a showcase of what can be done once users swap in their own background images, which is trivially easy to do. I have a seamless transition from xsplash all the way to my desktop, and it's a stunning effect. There are some who dislike the default backgrounds. Customization is now pretty easy, and some excellent effects can be achieved.

---

### Post by neferty on 2009-09-29
hmmm I'm getting an error while updating the new gdm. It says:

```
E: gdm: subprocess installed post-installation script returned error exit status 1
E: indicator-session: dependency problems - leaving unconfigured

```

has anybody got the same issue?

---

### Post by misfitpierce on 2009-09-29
[IMG]http://lh4.ggpht.com/_FJH0hYZmVtc/SrwNOqnVBMI/AAAAAAAADNA/JgToeAcv9Ck/image_thumb%5B3%5D.png?imgmax=800[/IMG]

Is this the mockup that actually made it or the ugly one with gray bar on bottom... Cause this mockup above is the one that should be used... It is beautiful!

---

### Post by skep on 2009-09-29
@neferty

same for me, trying to figure a way out

There is a bugreport: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/438561](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/438561)

---

### Post by amano on 2009-09-29
IIRC, some people showed off a screenshot with a black themed login menu as well. So just wait a bit. There will be something to be done with the menu, even if it cannot match the mockup entirely.

---

### Post by cyberkilla on 2009-09-29
> **misfitpierce said:**
> [IMG]http://lh4.ggpht.com/_FJH0hYZmVtc/SrwNOqnVBMI/AAAAAAAADNA/JgToeAcv9Ck/image_thumb%5B3%5D.png?imgmax=800[/IMG]

Is this the mockup that actually made it or the ugly one with gray bar on bottom... Cause this mockup above is the one that should be used... It is beautiful!

What I'm using looks more like that, so it must be planned.

---

### Post by godhika on 2009-09-29
This is what's planed but unfortunately the gtk 2 toolkit makes this mockup not possible - so they try to get close. Once gtk 3 arrives (Lucid or Lucid +1) they will go for it.

---

### Post by shafin on 2009-09-29
Try this command.
gksudo -u gdm dbus-launch gnome-appearance-properties
Then click customize and set the gtk and metacity theme to HumanLogin. It'll give you something like this:
[http://ubuntuforums.org/showpost.php?p=8005733&postcount=163](http://ubuntuforums.org/showpost.php?p=8005733&postcount=163)

You can try setting the Icon theme to HighContrast. that gives a closer look.

---

### Post by dino99 on 2009-09-29
Hope that something darkless or brownless will rise up.

---

### Post by amano on 2009-09-29
> **shafin said:**
> Try this command.
gksudo -u gdm dbus-launch gnome-appearance-properties
Then click customize and set the gtk and metacity theme to HumanLogin. It'll give you something like this:
[http://ubuntuforums.org/showpost.php?p=8005733&postcount=163](http://ubuntuforums.org/showpost.php?p=8005733&postcount=163)

You can try setting the Icon theme to HighContrast. that gives a closer look.

The dark Login Menu from your screenshots has just to be hooked up properly thus everybody can see it. Give the devs a few hours to sort that out.

---

### Post by bluenova on 2009-09-29
> **shafin said:**
> Try this command.
gksudo -u gdm dbus-launch gnome-appearance-properties
Then click customize and set the gtk and metacity theme to HumanLogin. It'll give you something like this:
[http://ubuntuforums.org/showpost.php?p=8005733&postcount=163](http://ubuntuforums.org/showpost.php?p=8005733&postcount=163)

You can try setting the Icon theme to HighContrast. that gives a closer look.

Pfft, such a let down after seeing the mock-ups. It's just the same flat box that was there before, only chocolate. I guess I'll be sticking with [Avio-GDM ]("http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395")then.

---

### Post by tjeremiah on 2009-09-29
i like the brown but this obviously isnt final.

---

### Post by Slug71 on 2009-09-30
I doesnt has facebrowser and my wallpaper is still yellow. :confused:

---

### Post by ricsi-pontaz on 2009-09-30
One day to Beta and the GDM is the same (with the brown background). I hope it will change today!

---

### Post by exploder on 2009-09-30
I like the gdm, it looks good with the throbber and is neutral enough that it allows for a nice transition to most any wallpaper. I hope they change the default wallpaper though.

---

### Post by tjeremiah on 2009-09-30
> **ricsi-pontaz said:**
> One day to Beta and the GDM is the same (with the brown background). I hope it will change today!

wow, beta is tomorrow ? That was fast,i think, been here since Alpha 1.

---

