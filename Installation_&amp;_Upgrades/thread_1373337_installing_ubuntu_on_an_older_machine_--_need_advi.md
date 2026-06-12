---
title: "installing ubuntu on an older machine -- need advice"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by ensleepent on 2010-01-05
I have some friends (a family) who really need a better computer but are tight on money.  I was hoping to switch their Pentium 4 w/ 128 MB RAM machine from the hideous, glitchy Windows ME to the awesome Ubuntu.

We all know that would be so much better for them.  :)

I've never used Ubuntu on a machine with only 128 MB RAM before, so I was wondering what to expect.  Will there be problems with installation?  What kind of desktop, window manager, etc. do you think would be best?  Should I consider Xubuntu, or some other Linux distro?  I've been reading a lot of articles around here but I'm not sure what my opinion should be.

BTW, the family I'm wanting to help out isn't very computer-savvy (I'll set it up for them), so a decent GUI will be preferred.  They use it mainly for browsing the web, doing office-type work, and for watching videos, listening to music, etc.  Nothing that requires too much high-performance.

---

### Post by SecretCode on 2010-01-05
I think you should expect a complete disaster running in 128MB. Ubuntu, Kubuntu and Xubuntu will not cope. 

Can you/they not manage to install some more RAM? Even if it means throwing out the chips currently installed (e.g. if it's full with 2 banks of 64MB).

Otherwise, why don't you install virtualbox on your machine and try to install various OSes in 128MB of RAM? Puppy and "Damn Small" Linux might be OK.

---

### Post by ensleepent on 2010-01-05
Yeah, I was wanting to get them some more memory; it's on my to-do list.  I was hoping I could get them started in the meantime though.

I guess I'll just wait until I get them some memory, thanks.

---

### Post by ajgreeny on 2010-01-05
I would still get a CD of puppy to try, which will run very well on that machine and may be all that is needed, depending on the uses it will be put to.

Even though it runs as a live CD you can use any hard disk available to save all your files and settings without problem.  Just boot to the live CD, set it up as you want and need and then when you shutdown, there will be an option to save all your settings/files and secondly to copy to the same disk the main puppy run file, which makes the live CD run so much faster than looking on a CD.

For such a small distro, it really is amazing.  I have used it many times in the past, and if I had a slow, old machine, it would definitely be my OS of choice.

[http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

---

### Post by wandalalakers on 2010-01-05
I 2nd puppy linux if you only have 128mb.

---

### Post by adam814 on 2010-01-05
Puppy Linux might be a good bet as I understand it's a bit more updated than DSL (I think it still uses a 2.4 kernel).

It's not like you'll have fancy new hardware you'll need a bleeding-edge kernel to support here.  In fact I'm not sure the newest Ubuntu kernels will support ancient IDE controllers anymore.  If one of those super-light distros won't cut it for what you need you can probably get away with doing a minimal netinstall of either Debian Stable or Ubuntu Hardy Server and selecting only the core system then doing an "apt-get install lxde" after it's up and running.

LXDE is the lightest full desktop environment I've seen (You could use fluxbox, but I consider it a Window Manager rather than a DE).  And it happens to look suspiciously like some XP themes I've seen.

---

### Post by Bartender on 2010-01-05
More RAM is the best answer, especially since you say they're not computer-savvy.  Ubuntu provides a lot more "point-and-click" stuff than Kubuntu or Puppy or DSL.  You could succeed in installing a light-weight distro but end up fighting the decreased "user-friendliness" forever.

---

