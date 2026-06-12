---
title: "installing fvwm"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by u534_n4m3 on 2006-09-11
i'm a linux noob and i need some help with some stuff.


how do you install fvwm?  what modules/packages are required to install this that isn't included in the defualt installationg of ubuntu?

basically what i'm asking is, after installing ubuntu, how do i install fvwm?

thanks

---

### Post by skymt on 2006-09-11
You're a Linux noob, and you want to install FVWM? :-s 

Well, you're in luck. All you need to do is open a terminal and type "sudo aptitude install fvwm". It'll install everything FVWM needs.

But... Why FVWM?

---

### Post by u534_n4m3 on 2006-09-11
> **skymt said:**
> You're a Linux noob, and you want to install FVWM? :-s 

Well, you're in luck. All you need to do is open a terminal and type "sudo aptitude install fvwm". It'll install everything FVWM needs.

But... Why FVWM?

i've seen some screenshots and they look kinda cool. fvwm looks different than the normal boring windows desktop.

---

### Post by skymt on 2006-09-12
The setups in those screenshots took hours to create. Out-of-the-box FVWM is almost as ugly and plain as you can get. It is very flexible, though (as you've seen).

Many users who like alternative desktops use one of the boxen: [Fluxbox](http://fluxbox.sourceforge.net/), [Openbox](http://www.icculus.org/openbox/), or the original [Blackbox](http://blackboxwm.sourceforge.net/). There's also the stepalikes: [Afterstep](http://www.afterstep.org/) and [Window Maker](http://www.windowmaker.info/). [IceWM](http://www.icewm.org/) is one of the lightest ways to get a normal-looking (read: Windows style) desktop.

Anyway, once you've run aptitude to install it (if you still want to), just log out and choose the FVWM session at the login screen.

Good luck. (Can you tell I don't like FVWM?)

---

### Post by whittycat on 2006-10-01
> **skymt said:**
> You're a Linux noob, and you want to install FVWM? :-s 

Well, you're in luck. All you need to do is open a terminal and type "sudo aptitude install fvwm". It'll install everything FVWM needs.

But... Why FVWM?

I too would like fvwm but this command (in Kubuntu 6.06) throws up a lot of dependency errors, eg libread4. What do I need in /etc/apt/sources.list to make this work? 

whittycat

---

### Post by whittycat on 2006-10-03
I found the answer. After installing Kubuntu 6.06 from the alternate install  ISO disc you have to do apt-get update and apt-get upgrade. Then you can install fvwm in the usual way. I think this is really bad. You think you are  getting a stable release and it is full of creepy-crawlies. Surely it is a serious bug that prevents apt from installing an application when it is in the archive (universe) and the sources.list is correct.

Disgusted of Wellington

---

### Post by theBlackDragon on 2006-10-09
I just install FVWM from source in my homedir, I find the Debian/Ubuntu packages to be horrible, they pull in half of GNOME for no reason at all and are pretty badly out of date (FVWM 2.5.14 is about a year old?)

And as stated by a previous poster: FVWM is not for the faint of heart, but that is to be expected: such extreme flexibility comes at a price.

---

### Post by [Yatta] on 2006-10-14
I use to use FVWM while i was in SuSE.. I think I'm goign to go back to it. Gnome just isn't doing what i want it to do.

theBlackDragon??? U left the Gentoo arena? or just giving ubuntu a whirl?

---

### Post by theBlackDragon on 2006-10-15
> **'[Yatta] said:**
> I use to use FVWM while i was in SuSE.. I think I'm goign to go back to it. Gnome just isn't doing what i want it to do.

Heheh, sounds familiar, once you have experienced the power of the dark...of FVWM there's now way back ;) But really, once you start using Gnome (or anythinge else for that matter) again you'll soon start wondering why you can't do this or that:) 

> **'[Yatta] said:**
> theBlackDragon??? U left the Gentoo arena? or just giving ubuntu a whirl?

Neither really, I'm still using Gentoo on my desktop and home server, but after my laptop's harddisk failed for the 3rd time I didn't really feel like going through the entire Gentoo installation process again, so I grabbed the next best thing ;) I like Ubuntu though, no messing to get suspend, networks and a lot of other stuff up.

Otoh there are some things that annoy me, like how outdated some packages are (gmpc and FVWM for instance) and the lack of packages for some development tools (hint: "Ruby"), there are also some stability issues, but those might be hardware related, dunno.

Simply put, I use them both, but for different purposes :)

---

