---
title: "Newer version is older? (automake issue when building a custom package)"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mgol on 2009-10-14
I tried to build amarok-1.4.10 under 64-bit Karmic (using debuild). I installed a lot of dependencies; however, I got the following error:

```
*** YOU'RE USING automake (GNU automake) 1.11.
*** KDE requires automake 1.6.1 or newer
```

Isn't 1.11 supposed to be newer than 1.6.1? I can't understand it...

---

### Post by mc4man on 2009-10-14
It may just not be good with 1.11

Maybe try installing automake 1.10

Then go like this in terminal if need be

> doug@doug-desktop:~$ sudo update-alternatives --config automake
[sudo] password for doug: 
There are 2 choices for the alternative automake (providing /usr/bin/automake).

  Selection    Path                    Priority   Status
------------------------------------------------------------
* 0            /usr/bin/automake-1.11   29        auto mode
  1            /usr/bin/automake-1.10   28        manual mode
  2            /usr/bin/automake-1.11   29        manual mode

Press enter to keep the current choice[*], or type selection number: 





I'm using 1.4 in karmic and while I usually build my own media apps and libs decided in this case to just use the amarok1.4 packages from here

[https://launchpad.net/~bogdanb/+archive/amarok14](https://launchpad.net/~bogdanb/+archive/amarok14)

In my case I have a local repo in $HOME, so just downloaded the 3 packages needed, added them to my repo, updated and then installed amarok from synaptic.  (works fine

I'm sure, if desired, you could add the ppa, install amarok and then dump the ppa.(unless you have a reason to build

---

### Post by mgol on 2009-10-14
Thanks, automake 1.10 seems to work. I cannot build amarok 1.4 for different reasons, but it's not relevant to this problem.

I must admit that this message was highly misleading, though. :)

Thanks for the repo, I'll try it. I assume I have to add a jaunty entry as karmic one doesn't exist there?

---

### Post by mc4man on 2009-10-14
> assume I have to add a jaunty entry as karmic one doesn't exist there?

I've got a testing install so went ahead and did.
Just added the first line for jaunty (don't need the deb-src line

Then went into synaptic and installed ( it removed the current installed 2.2, I removed the amarok-utils,

Installed fine this way

---

### Post by mgol on 2009-10-19
mc4man, do You know how to conveniently change KDE3 settings for Amarok? I don't like this large font but I know kcontrol is gone... Any way I could change it, any conf files to edit? Help would be greatly appreciated...

---

### Post by mc4man on 2009-10-20
> ... conveniently change KDE3 settings for Amarok? 

Well I'm using gnome and amarok is my only kde app, so probably not.

Any changes i want to make to amarok can be done in settings -> configure amarok

( I have changed the font, font size and info displayed for the osd, otherwise I tend to use amarok using r. click actions and the keyboard so don't usually see the player window too much.

---

