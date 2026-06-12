---
title: "save installed package list ... for disaster recovery"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2007-06-19
This may be somewhere on the forum, in some slightly different context, so sorry in advance if so.

I just upgraded to Feisty, I had to do a fresh install of everything because I was one release back
(end of the academic year is a busy time).  So I did my usual backup -- all of my personal files, on
DVD -- formatted the partition and did a fresh install.  Then I spent about a day getting back all of
the little bits of software I have downloaded (mostly just by clicking on things in synaptic, but not
entirely), so my new system was usable in the usual way.

So, my question is: can I save off a file which shows all of the packages I have added?  I could put
this on the same DVD as my personal files (or another), then I would use it as follows:
1) In case of hardware disaster, I would fix the hardware problem, do a fresh Feisty install, copy my
/home off the DVD, and then automagically have all of the packages I've chosen as important download
and install.  Note I do fairly frequent personal backups, so this would allow me to recover -- completely
and relatively painlessly -- from problems.
2) Next upgrade, particularly if I miss a step and have to do it by a complete fresh install, I would follow
the same process.

Basically, I am suggesting a fresh install, plus an automagic installation of my personal favorite
packages, would be a great aid to shorter backups.  So -- any way to dump this list of my packages?
In a form from which I can then re-install them, *without simply typing the list*?

Another wrinkle: what about software which you get some other way, not as a .deb?  For example,
I download/install a lot of things from CPAN, how can I list and then automatically recover them?


Thanks in advance!

---

### Post by merlinus on 2007-06-20
dpkg --get-selections > some_file

in your new installation:

dpkg --set-selections < some_file
apt-get dselect-upgrade

-merlin

---

### Post by PaulFr on 2007-06-20
For CPAN, the 'autobundle' command.

---

