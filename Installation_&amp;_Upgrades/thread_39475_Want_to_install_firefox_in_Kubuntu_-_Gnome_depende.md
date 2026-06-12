---
title: "Want to install firefox in Kubuntu - Gnome dependency ?"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by AndreasMeier on 2005-06-05
Hi all,

I want to install Firefox in my Kubuntu 5,04 Desktop, but then he wants to install some of the Gnome components as well, like libgnome2-0, some bonobo-things and some of other libgnome*-components.
What is wrong here ?
Where can I get a source which provides me a clean KDE-only Firefox ?

thanks a log,
regards
Andreas

---

### Post by mingus on 2005-06-06
For what it's worth . . .

I've got both Ubuntu and Kubuntu installed.  For Kubuntu I did not install the gnome-support package, and Firefox is not skinned as it is in Ubuntu.

As far as prerequisite libraries like bonobo, you may be surprised that this is included in other install packages, e.g., the SuSE rpm on my main box, which is KDE.  Bonobo is a library of CORBA objects built with the Gnome dev language.  There are now quite a few of these kinds of objects that are shared between Gnome and KDE.  Some are there for GUI integration; others look like they are but actually just appear that way because they are written in gtk2 or qt.

Be sure to get Firefox 1.0.4 from Backports so that you can get extensions and themes.

---

