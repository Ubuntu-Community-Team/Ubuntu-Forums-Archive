---
title: "Microsoft Fonts"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2005-06-21
Id there a way to get them on Ubuntu? How do I install them? Without them some websites look very weird to me.

---

### Post by GTvulse on 2005-06-21
Hi, you can install the msttcorefonts, which you'll find in synaptic after enabling the multiverse repository. This package willl automatically install the older versions once given away freely by Microsoft (and still free if you follow the licensing conditions)by grabbing copies from the net.

If you have licensed copies of newer versions of the fonts in question from your Windows partition, you could download the source package from [http://packages.ubuntu.com](http://packages.ubuntu.com) (*not* the Debian package but the tar.gz and the diff file!), recover the hints file, and use defoma to install the fonts by hand.

---

### Post by kona0197 on 2005-06-21
I'm really a big noobie - so how do I go about doing all that?

---

### Post by az on 2005-06-21
I think you will be happy just installing the msttcorefonts package form multiverse.

As for the websites, well, Internet Explorer is not standards compliant.  Some websites comply to it, and not to the official standard.  Changing fonts may help, but it won't fix the problem,

---

### Post by kona0197 on 2005-06-21
What do I need to add to my repositories list? Anything? Is there any examples? Thanks.

---

### Post by polo_step on 2005-06-21
[QUOTE=kona0197]What do I need to add to my repositories list? [/QUOTE]
Honestly, there should be a GUI button for this in future releases:

A disclaimer that "this repository's programs are not Ubuntu supported," and "I accept conditions" user button and then the list gets those entries auto-uncommented, biff-pow and move on with life.

That every new user has to edit this manually during his (dis)orientation period is preposterous, geeky, Linuxy and offputting.

There, I've said it. Someone had to. :)

---

### Post by polo_step on 2005-06-21
[QUOTE=azz]I think you will be happy just installing the msttcorefonts package form multiverse.[/QUOTE]
"Happy"? I think I'll be doggone *thrilled!*

The wretched Ubuntu fonts gave me blinding eyestrain and a headache for the first few days.  I'm somewhat more used to them now.  The Ubuntu package's comprehensive aesthetic misjudgment (starting with that shocking diarrhea-episode desktop wallpaper and working outwards) was the single biggest turn-off to the distro for me (OK, call me shallow, but I'm a BFA and that degree is dead worthless in the real world except for pulling rank in artistic merit arguments).

*"But seriously folks..."* One of the things that really stands in the way of new user acceptance -- especially on a dual-boot system -- is a *familiar look* compared to the prior/coexisting OS.  When everything just looks cockeyed it just adds to the shock of coping.  This is not a trivial point to those who want to see broader and more popular acceptance of the distro.

If I'm dual-booting, I don't want to have to re-calibrate myself every time I switch back and forth.  That's terrible visual ergonomics.  It should be as visually seamless a process as possible.

---

### Post by Dogmudgeon on 2005-06-22
[QUOTE=polo_step]The Ubuntu package's comprehensive aesthetic misjudgment ... was the single biggest turn-off to the distro for me ...[/QUOTE] I have to agree, but with some reservations -- I didn't find the new esthetics all that bad, but I would like something closer to the Classic Redmond look from Win95. FWIW, I despise the WinXT wet-candy look and its Gnome and KDE successors. 
 
I guess ideally the two systems would have minor esthetic variations so the user can change "user state" in the "biocomputer" more easily, but some of the stuff was jarring. The caret (selection highlighting) was initially pumpkin-orange. That's got to be someone's idea of a practical joke. 
 
Unlike polo_step, I'm not a complete newbie. I've been programming with MS products since the late 1980s. I'm looking around for tutorials and possibly apps that will allow me to roll my own theme(s). But I've only been at this for about two days, so it will take a little time!
 
--woof!

---

### Post by az on 2005-06-22
[QUOTE=polo_step]Honestly, there should be a GUI button for this in future releases:

A disclaimer that "this repository's programs are not Ubuntu supported," and "I accept conditions" user button and then the list gets those entries auto-uncommented, biff-pow and move on with life.

That every new user has to edit this manually during his (dis)orientation period is preposterous, geeky, Linuxy and offputting.

There, I've said it. Someone had to. :)[/QUOTE]

There is a button.  Have you never run synaptic?  You never have to change your sources.list by hand unless you want to.

---

### Post by polo_step on 2005-06-23
[QUOTE=azz]There is a button.  Have you never run synaptic?  You never have to change your sources.list by hand unless you want to.[/QUOTE]
Yeah, I discovered that in another thread.  When new people ask about stuff that requires adding repositories, this option really should be at least mentioned to them before having them get into the hand-editing of the sources.list, which seems to be the default advice here.

That's pretty scary for a lot of folks...and in retrospect it seems kind of inefficient for anyone, especially if your eyesight's not tops and you screw up a line, as I did. :-?

---

### Post by polo_step on 2005-06-23
[QUOTE=Dogmudgeon]I have to agree, but with some reservations -- I didn't find the new esthetics all that bad, but I would like something closer to the Classic Redmond look from Win95. [/quote]
That's what I've always used, which is interesting, as I never even used Win95.  I went from CP/M to MSDOS and from there directly to Win98.

> FWIW, I despise the WinXT wet-candy look and its Gnome and KDE successors. 
Agreed on that.  I never want to see another rounded window corner ever again, either.  It's bad visual ergonomics.
 
> I guess ideally the two systems would have minor esthetic variations so the user can change "user state" in the "biocomputer" more easily, but some of the stuff was jarring. The caret (selection highlighting) was initially pumpkin-orange. That's got to be someone's idea of a practical joke. 
It may also have something to do with exciting a younger user, who *wants* rather than avoids useless variety and visual disorientation, rather than an adult user with real work to do, deadlines to meet, bad eyes, exhausted patience and the stress of inumerable hostile daily changes in his life without having to deal with pointless ones on his computer.

The solution I have is to have the different boxes, duplicate applications, etc. just slightly different in theme color, enough to be a clear distinguishing marker, but not enough to be the slightest bit unsettling.

Still, at incredible cost, marketing research has established and repeatedly confirmed that certain product colors simply turn people off.  Brown is right there at the top of the list; there are less objectionable earthtones, if you *must* go that route.

While I'm at it, a distro is just ones and zeroes and someone has to decide how to conceive a distro's *geist* and pitch it.  I really don't like the whole chinless-whiteguy-in-a-dashiki, welcome-to-our-hate-free-drumcircle, orientation-day-at-UC-Santa-Cruz vibe this thing gives off.  Everyone I've given this to has spontaneously had the same take and I catch them sort of looking at me funny. "What, you get this from the Youth League of the Belgian Green Party?"  "Whoa, I thought this was a Moby CD!"

Ubuntu Live has avoided the predictable geeky tastelessness of, say, Knoppix and as far as I can see is penguinless, so maybe that's progress!  ;-) 

But progress must...well...progress, right?

---

