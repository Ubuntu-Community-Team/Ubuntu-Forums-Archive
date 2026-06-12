---
title: "Should I upgrade to Xubuntu 16.04.1 or just install 14.04.5?"
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by the4thwall on 2016-12-15
Hello,

So I want to start working with NodeJs. I have 15.04 but it is not supported by it. I've mostly been using 14.04.5. So I have to make a decision: Should I install 14.04.5 or 16.04.1?

I am a javascript web developer. I want to work with mean stack and lamp mostly. Thoughts? I'm trying to weigh the stability of an older distribution vs security updates and whatnot.

---

### Post by Keith_Helms on 2016-12-15
Xubuntu LTS releases are only supported for 3 years, not 5 like Ubuntu, so the clock is running out on 14.04. It will only be supported for another 4 months.

I've run into 1 new bug in 16.04 related to my wifi adapter and multiple other things that were fixed between 14.04 and 16.04.   Overall it seems to be a stable release to me.

---

### Post by RobGoss on 2016-12-15
I have been running **Ubuntu Gnome 16.04 Xenial Xerus** since it launched and it runs flawless. I have not had any issues so far and everything seems to work great

---

### Post by DuckHook on 2016-12-15
As I see it, you have at least 3 choices:

[LIST=1]
[*]Upgrade to Xenial,
[*]Switch to Ubuntu (5 yrs LTS), but stick with Trusty,
[*]Stick with what you've got for now but transition to Xenial on a separate box.
[/LIST]
I too have switched to Xenial and note that many of the initial bugs have been ironed out. However, there's more to it than just bugs and stability&#8213;Xenial has a whole bunch of underground changes that are very different than Trusty&#8213;like systemd, snaps, changed apps, etc. If this box is your livelihood and you don't want to wrestle with such changes concurrently, then you may be better off using plan 3.

Even if you stick with Xubuntu Trusty for now, I would highly recommend that you either install Xenial on another box, dual boot, or install in a VM to slowly transition without having to risk your production environment.

---

