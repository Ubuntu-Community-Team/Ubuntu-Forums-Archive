---
title: "no display after install ubuntu minimal 10.10 with gnome-core"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by DataSpy on 2011-02-12
Hello,
I recently installed the newest ubuntu 10.10 minimal and only installed the base package.  Afterwards I booted to command prompt and installed xorg, gnome-core, firefox, and wine.  I've done this many times before (never with ubuntu 10.10) and have never had a problem.  This time though after installing the packages mentioned about and typing startx it goes to a blank screen and it looks as though my monitor is in standby mode.

Any help would be greatly appreciated, thanks in advance!!!

Jim

---

### Post by mörgæs on 2011-02-13
My first guess is that you need boot options:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by DataSpy on 2011-02-13
It actually boots fine, I boot into single user mode since I don't have a login manger installed then I type: startx, right after that, as it's starting the xserver the monitor goes dead :( .  Thanks for the help though!!  I'm thinking about reinstalling 10.04 and seeing if upgrading will work, I'll post later if it does :)

---

### Post by mörgæs on 2011-02-15
> **DataSpy said:**
> as it's starting the xserver the monitor goes dead

Yes, this indicates that it is worthwhile to try boot options - but staying with 10.04 is not a bad choice, if it does not work.

---

### Post by Advice Pro on 2012-08-21
Just install gdm.

---

### Post by overdrank on 2012-08-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

