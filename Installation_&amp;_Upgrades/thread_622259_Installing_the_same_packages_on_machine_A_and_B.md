---
title: "Installing the same packages on machine A and B?"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by kooldino on 2007-11-24
I've spent a lot of time installing the packages I want and customizing the settings I like on my main machine.  I'd like to not go through all of this again on other kubuntu 7.10 boxes that I set up.

I was wondering two things.

1-Is there a way I could make a list of all the packages installed in this machine, copy the list to a new machine, and auto install the same packages there?  

I could hypothetically write a script to parse the output of dpkg -l and then another script to apt-get install all of those, but I was hoping there'd be a simpler way to do this.

2-I'd like to copy my KDE preferences and such all over to the new machine as well.  How would I go about this?

---

### Post by Pumalite on 2007-11-24
AptOnCD makes copies of programs installed through apt-get or aptitude only:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by kooldino on 2007-11-25
So will it install on the new machine cleanly then?

---

### Post by Pumalite on 2007-11-25
Yes. And get the updates. Then add the packages in the CD's or DVD's.

---

