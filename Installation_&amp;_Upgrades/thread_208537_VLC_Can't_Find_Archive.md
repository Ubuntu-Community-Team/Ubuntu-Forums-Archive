---
title: "VLC Can't Find Archive"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by twistedchick on 2006-07-03
When updating to Dapper my machine shut down!  I've already went through most of the applicable fixits contained in "Having problems with installing or upgrading to Dapper? Here are some fixes".  Fixed more than a few things <yay! patting self on the back :D> however one error persists:

The package vlc needs to be reinstalled, but I can't find an archive for it.

To no avail I've attempted to fix the issue via:

[PHP]sudo apt-get -f remove
sudo dpkg --configure -a
sudo apt-get remove vlc
sudo apt-get install vlc=0.8.5 -f
[/PHP]

Where am I going wrong???  

p.s. I'm a total beginner so super detailed & dummed down explanations are appreciated!  8-[

---

### Post by jISh on 2006-07-03
Why don't you just do it through Synaptic?
Find the package, mark for removal.
Then install again.

---

### Post by Jagot on 2006-07-03
What do you get when you do this:

```
sudo aptitude search vlc
```

---

### Post by twistedchick on 2006-07-03
sudo aptitude search vlc

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

*I've already 'dpkg --configure -a' and it doesn't fix anything.  Furthermore I attempted to fix the dependencies using the guide and the method I mentioned above.  Maybe I'm messing up the code or something it seemed fairly straight forward.  In addition if this helps when I type:

sudo dselect

it returns with the dependency probs listed below that I can't figure out how to rid fr: the system:

dpkg: dependency problems prevent configuration of libhal1
libhal1 depends on libdbus-1-2 (>=0.60):however:Package libdbus-1-2 is not installed

dpkg: dependency problems prevent configuration of wxvlc
wxvlc depends on vlc (=0.8.4 debian -1ubuntu6);however:Package vlc is not installed

---

### Post by Jagot on 2006-07-03
Have you run 'dpkg --configure -a' with a sudo before it?

---

### Post by twistedchick on 2006-07-03
yes the same dependency issues that were listed under

```
deselect
[C]onfig
```

stated in the previous message are the exact same ones that pop after

```
sudo dpkg --configure -a
```

---

