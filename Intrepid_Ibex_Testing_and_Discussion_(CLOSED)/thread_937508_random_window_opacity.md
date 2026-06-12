---
title: "random window opacity?"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stewacide on 2008-10-03
I've noticed since upgrading to Intrepid that window contents will sometime appear semi-transparent and sometime not. I can't discern any pattern to it. Unless I'm imagining thing the same window from the same application will sometimes show up one way and sometime the other, and windows will even 'mix' styles (see attached pics).

What's going on?

---

### Post by Luffield on 2008-10-04
I noticed it too - the system monitor window is always slightly transparent. Did you check if there's a bug on Launchpad about this?

---

### Post by danf_1979 on 2008-10-04
Right, confirmed here too.

---

### Post by Kow on 2008-10-04
I noticed this last night and just thought I was tired. Guess I was right. Interesting easy-to-miss bug.

---

### Post by wgrant on 2008-10-04
It's not a bug - Human-Murrine makes windows translucent if it can (ie. if they say they are RGBA). It looks much better with Compiz blurring the windows behind.

---

### Post by stewacide on 2008-10-04
> **wgrant said:**
> It's not a bug - Human-Murrine makes windows translucent if it can (ie. if they say they are RGBA). It looks much better with Compiz blurring the windows behind.

In that case it really need some sort of Vista-glass-esq diffused lighting going on so that window contents underneath don't show through clearly. How would one enable that in compiz?

Hopefully this prompts developers to program in the alpha values for their apps (Ubuntu being so popular and this being the new default). Unfortunate that even most standard Gnome windows lack it (System Monitor being an exception)

---

### Post by taavikko on 2008-10-04
> **stewacide said:**
> In that case it really need some sort of Vista-glass-esq diffused lighting going on so that window contents underneath don't show through clearly. How would one enable that in compiz?

Hopefully this prompts developers to program in the alpha values for their apps (Ubuntu being so popular and this being the new default). Unfortunate that even most standard Gnome windows lack it (System Minitor being an exception)

simple-ccsm or compizconfig-settings-manager
Both of them should do the trick.

---

### Post by stewacide on 2008-10-04
Compiz settings manager has an absolutely mind-boggling number of options (not complaining, it's an incredible piece of work). Any idea what one in particular?

edit -- NVM, I found the blur window menu, although I'm having trouble getting the settings to take effect... I think it could be a hardware compatibility issue...

---

### Post by wgrant on 2008-10-04
> **stewacide said:**
> Compiz settings manager has an absolutely mind-boggling number of options (not complaining, it's an incredible piece of work). Any idea what one in particular?

A combination of Reflection and Blur might work well.

---

### Post by plun on 2008-10-04
No this is not a bug...:D

RGBA themes are just great with RGBA enabled apps.

Much better then messing around with Blur  


About Cimis RGBA (direct to apps)  

[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)


For the first time in history I like Rhythmbox with RGBA enabled. :D

MacSlow about this  **IMPORTANT to read  !!**
[https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish](https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish)


How it looks with RGBA enabled apps and Compiz running
[[img]http://ubuntu-pics.de/thumb/4029/rgba_46O7a0.jpg[/img]](http://ubuntu-pics.de/bild/4029/rgba_46O7a0.jpg)

Also latest Murrine SVN....


I just love RGBA...:D

---

### Post by stewacide on 2008-10-04
Without that diffused blur effect (see pics attached; the same effect is present everywhere in Leopard and Vista) it seems like a UI disaster, having text and other elements from one window showing through clearly to another. Unfortunately it seems support for that blur effect in Compiz is extremely spotty (seems to be the least supported of all effects in terms of hardware)

---

### Post by plun on 2008-10-04
> **stewacide said:**
> Without that diffused blur effect (see pics attached; the same effect is present everywhere in Leopard and Vista) it seems like a UI disaster, having text and other elements from one window showing through clearly to another. Unfortunately it seems support for that blur effect in Compiz is extremely spotty (seems to be the least supported of all effects in terms of hardware)

OK

Well, its probably a larger disaster not running RGBA compared with Vista and Leopard. Also look at **Windows 7** ! 

I personally don't find this as a problem but I know that Cimi tried to find out a way for global RGBA settings.

Default Intrepid is just a touch with this technology.

---

### Post by Luffield on 2008-10-04
Thanks for the information everyone. I still think this is a bug - since not all windows are able to do this trick, none of them should. With the way it is now, when some windows have this opacity and some don't, things just look weird.

---

### Post by plun on 2008-10-04
> **Luffield said:**
> Thanks for the information everyone. I still think this is a bug - since not all windows are able to do this trick, none of them should. With the way it is now, when some windows have this opacity and some don't, things just look weird.

This is a Windows 7 mockup... 

[[img]http://ubuntu-pics.de/thumb/4030/194521518_J2ZTw0.jpg[/img]](http://ubuntu-pics.de/bild/4030/194521518_J2ZTw0.jpg)

So maybe we must start somewhere...:)

---

### Post by taavikko on 2008-10-04
> **Luffield said:**
> Thanks for the information everyone. I still think this is a bug - since not all windows are able to do this trick, none of them should. With the way it is now, when some windows have this opacity and some don't, things just look weird.

Then take this issue to software developers upstream.
tell them to use unified toolkits to have consistent look on desktop usage...

Depending on toolkits used, is ARBG supported by default.

---

### Post by taavikko on 2008-10-04
> **plun said:**
> This is a Windows 7 mockup... 

[[img]http://ubuntu-pics.de/thumb/4030/194521518_J2ZTw0.jpg[/img]](http://ubuntu-pics.de/bild/4030/194521518_J2ZTw0.jpg)

So maybe we must start somewhere...:)

Transparency in all elements is something I would call, awful :(
It might affect usage, when you have hard time to see eg. menus. IMHO.

Little less time on eyecandy, little more on stabilizing the software :)
In all Desktop-enviroments and OS.

---

### Post by plun on 2008-10-04
> **taavikko said:**
> Transparency in all elements is something I would call, awful :(
It might affect usage, when you have hard time to see eg. menus. IMHO.

Little less time on eyecandy, little more on stabilizing the software :)
In all Desktop-enviroments and OS.

No I would say more eyecandy and stop figting against what **"main stream"** wants.  :D

This fighting just kills Linux....

The picture is maybe a problem and the guy which posted it and other pics got into trouble...:cool:

[http://www.thinknext.net/archives/2281](http://www.thinknext.net/archives/2281)

Please also read MacSlows wiki earlier posted....

---

### Post by psyke83 on 2008-10-04
Just remember that we're still in the testing phase. You can quote me on this: RGBA may not be enabled for the final release. 

There, it's been said. Nobody has the right to moan if this feature disappears :p.

It really depends on Kenneth Wimer's decision, and he's been advised that RGBA may not be fully stable or polished enough to be enabled by default for the final install.

---

### Post by vishzilla on 2008-10-04
> **psyke83 said:**
> Just remember that we're still in the testing phase. You can quote me on this: RGBA may not be enabled for the final release. 

There, it's been said. Nobody has the right to moan if this feature disappears :p.

It really depends on Kenneth Wimer's decision, and he's been advised that RGBA may not be fully stable or polished enough to be enabled by default for the final install.

can I moan before it disappears for the sake of it? :D

---

### Post by stewacide on 2008-10-04
Hopefully by the time Jaunty rolls around RGBA will be widely implemented (or at least a comprehensive collection of hacks compiled) and hardware support for the alpha blur will be widespread (with software fallback).

---

