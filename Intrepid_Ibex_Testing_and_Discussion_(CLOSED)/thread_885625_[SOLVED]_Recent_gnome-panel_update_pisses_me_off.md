---
title: "[SOLVED] Recent gnome-panel update pisses me off"
date: 2008-08-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-08-10
Recently, there was an upstream commit to gnome-panel that "fixed" strut behavior on auto-hide panels. And by "fixed", I mean "changed an accepted behavior that has existed for years and which resembles other desktop environments simply to destroy a bug that doesn't happen for the top 99% of usage scenarios".
If you don't know what struts are in reference to dock windows, they're the little packet of data that says how the dock affects your desktop environment. You probably notice with a static dock that your fullscreen windows don't cover it. Well, basically, what this change did was that. For auto-hide windows. The effect is that full-screen windows resize every time you open the panel. And if your panel is animated? Your window goes through 24 frames of redrawing.


In other words, a GNOME dev, stuck on fixing a silly bug, decided to completely destroy an established standard and expected behavior of a crucial and immediately visible application.

I myself despise this change so much, I added back in the *2 lines* that are needed to retain the original behavior.

[Bug report on Launchpad](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/256618).

---

### Post by Nullack on 2008-08-10
IMHO youd be better off taking this issue upstream to gnome and discussing it there.

---

### Post by MaX on 2008-08-10
What bugnumber is it?

---

### Post by klange on 2008-08-10
> **MaX said:**
> What bugnumber is it?
[256618 on Launchpad](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/256618), [546835 upstream](http://bugzilla.gnome.org/show_bug.cgi?id=546835).

---

### Post by ronacc on 2008-08-10
well are you going to share the 2 lines needed to "unfix" this ?

---

### Post by Ripfox on 2008-08-10
Yes what are the two lines...

---

### Post by klange on 2008-08-10
> **ronacc said:**
> well are you going to share the 2 lines needed to "unfix" this ?

[Readd the lines removed by this commit](http://svn.gnome.org/viewvc/gnome-panel/trunk/gnome-panel/panel-toplevel.c?r1=11188&r2=11187&pathrev=11188). Read the commit message and have a look at the bug they were "fixing" with this.

(Simply `apt-get source gnome-panel`, `sudo apt-get build-dep gnome-panel`, gedit "gnome-panel/panel-toplevel.c" and add those two lines back in, you should also compile with --disable-scrollkeeper, because it yelled at me (and we don't actually use scrollkeeper any more), note that as not all of the Ubuntu patches are applied, you'll lose the "About Ubuntu" menu item)

---

### Post by southsnow on 2008-08-10
AHA! This is what broke my firefox display!

---

### Post by ronacc on 2008-08-10
thanks the "dancing desktop" and fullscreen windows were rapidly ceasing to be amusing .

---

### Post by ronacc on 2008-08-12
just a note ! the build-deps for gnome-pannel drug in 113 files , the next update with aptitude wanted to remove all of them , switching to apt-get for the upgrade did not want to remove any so I used that .

---

### Post by klange on 2008-09-09
And now it is gone. The quirk has been removed up stream and from the Intrepid releases.

In retrospect, it may have been a nice *option*, but the results of the change were too obvious and dramatic for it to be a default behavior, let alone *the* behavior.

---

### Post by dagrump on 2008-09-09
Didn't RTA but I see the return of behavior I was used to. Thank you for voicing your displeasure, I would of never guessed it would payoff, I had quit maximizing windows, just left room for my panels. Hadn't noticed this thread earlier.

---

