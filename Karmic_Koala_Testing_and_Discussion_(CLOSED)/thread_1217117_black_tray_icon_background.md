---
title: "black tray icon background"
date: 2009-07-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hairy_Palms on 2009-07-19
there seems to be a problem with banshee in karmic its notification icon always has a black background, see the attached screenie, i install the latest daily build under a VM and the problem exists there too, can anyone else confirm this, ill post a bug later today.

---

### Post by Hairy_Palms on 2009-07-19
should mention, tried with banshee 1.4 from repos, 1.5 from the PPA and compiling the latest from git

---

### Post by Craigy90 on 2009-07-19
I'm seeing that here too, could you link to the bug report?

---

### Post by atomizer on 2009-07-19
The System tray specifications are bad and ugly, as some people say.

Different icons from different programs will have different backgrounds, as long as the specs don't tighten.

That why Enlightenment doesn't have a system tray.

It is not a bug in your program.

>  Originally Posted by [http://www4.get-e.org/Main/FAQs/#57](http://www4.get-e.org/Main/FAQs/#57)
Does E17 have systray support ?
No, there will be no tray icon support in E17 until the systray icon standard is changed.

Carsten 'Rasterman' Haitzler wrote:

"The Systray specification that somehow users seem to ask for and applications seem to use that is specified here primarily, is not as nice as you may think. It is in fact rather ugly and limited. It leads to awful interfaces and inconsistent behavior and display."

For the full text of this article, along with a screenshot, please see [Rasterman.com]("http://www.rasterman.com/").

Most people end up using trayer or engage.

---

### Post by MacUntu on 2009-07-19
Checkgmail's tray icon shows the same problem and it worked fine before so it's definitely not a problem with the applications.

---

### Post by MacUntu on 2009-07-19
-- crap --

---

### Post by MacUntu on 2009-07-19
Already filed upstream:

[http://bugzilla.gnome.org/show_bug.cgi?id=588255](http://bugzilla.gnome.org/show_bug.cgi?id=588255)

---

### Post by perfectska04 on 2009-07-19
Is it too much to ask for a panel implementation that supports true transparency, smooth gradients and a single, common matching for **all** applets?

Currently, if you want dark panels in a light theme or viceversa - you have to add resource class matching in GTK for pretty much everything, and some apps will still misbehave or theme some menus/widgets inappropriately.

---

### Post by inportb on 2009-07-20
> **perfectska04 said:**
> Is it too much to ask for a panel implementation that supports true transparency, smooth gradients and a single, common matching for **all** applets?

Currently, yes. The applets themselves must support the new protocol as well.

---

### Post by fluteflute on 2009-07-29
Just wanted to link the LP bug: [https://bugs.edge.launchpad.net/ubuntu/+source/checkgmail/+bug/403135](https://bugs.edge.launchpad.net/ubuntu/+source/checkgmail/+bug/403135)

---

### Post by JohnJackson on 2009-08-13
This is fixed now, think it might've been a gtk update.

---

### Post by MacUntu on 2009-08-13
Icon still fails to reappear if gnome-panel is restarted or notification area is removed and re-added ([http://bugzilla.gnome.org/show_bug.cgi?id=529023](http://bugzilla.gnome.org/show_bug.cgi?id=529023)). This works fine when using GtkStatusIcon instead of the (deprecated?) GtkTrayIcon (which all of those black background apps use).

---

