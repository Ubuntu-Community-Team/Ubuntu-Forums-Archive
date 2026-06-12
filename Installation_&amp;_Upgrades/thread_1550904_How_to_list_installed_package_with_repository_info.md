---
title: "How to list installed package with repository information?"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by eshneto on 2010-08-11
Hello, I have recently received a new machine and asked to my company's "computing technical service" to install Kubuntu, which they did. They have, however, enabled a backports PPA repository that I did not notice.

Because of that, when updating, the new KDE4.5 was installed, causing all sorts of bug to show up.

Now I have disabled the alien repositories, but I am still not able to correctly install kubuntu-desktop because there are lots of packages from the PPA that conflict with those I am trying to install.

I know that "dpkg --get-selections" lists every package in my system, but it does not show from what repository it came from.

My idea is to do something like

cmd | grep -i ppa

to get a listing of which packages I must remove in order to fix the system, but I do not know how would "cmd" look like.

Any hints?

Thank you in advance,
Elias.

P.S.: I know I should make the technicians do this dirt job, but they say I must wait for a week without my machine and, further, I just do not trust them anymore.

---

### Post by ajgreeny on 2010-08-11
If you have synaptic available you can simply use the buttons in the left hand pane to look at the origin of all packages.  Using that, with the backports still enabled, you can highlight the backports repo and see all the packages with the installed mark, choose each of those and mark them for removal, then use **File ->Save markings as** and save a text file, then either cancel out, or go ahead and remove them, though it may be difficult to remove them if you are running the desktop environment that needs them, unless you have another desktop environment as well.

---

### Post by eshneto on 2010-08-19
Well, there are two problems:

KDE is not working and I did not have another desktop installed. Installing Gnome only for this task would not be the way to go, even though it could maybe work.

A second problem is that I have disabled the ppa, so it does not show up in synaptic anymore.

I actually got the job done by hand, but I really think there should be a way to do this from the command line, don't you agree?

There is a script that can be helpfull, look at the following thread:
[http://ubuntuforums.org/showthread.php?p=9739351#post9739351](http://ubuntuforums.org/showthread.php?p=9739351#post9739351)

Furthermore, a question comes to my mind: why Fedora guys are always able to update KDE without any problem while Ubuntu dev team cannot do it without breaking everything?

Elias

---

