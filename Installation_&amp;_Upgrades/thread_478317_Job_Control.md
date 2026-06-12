---
title: "Job Control?"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by Xaimas on 2007-06-19
I put in a Ubuntu 7.04 FF CD in my New Laptop, and run the general boot but then it loaded the shell and came up with this:

```
/bin/sh: can't access tty; job control turned off
```

WTF? I never had this problem before, any suggestions?

---

### Post by Xaimas on 2007-06-19
Anyone?

---

### Post by digitalbenji on 2007-06-19
That's a strange one.  Did you test the CD for defects?

---

### Post by Xaimas on 2007-06-22
> **digitalbenji said:**
> That's a strange one.  Did you test the CD for defects?

Brand new ordered CD ;)

The OS is Vista on my Laptop, does that change anything?

---

### Post by strangedata on 2007-06-27
Hi,

I'm having a similar problem on my Sony Vaio laptop. First I get:
/bin/sh: can't access tty; job control turned off

And the casper.log file says (repeatedly):
cannot mount /dev/sda1 on /cdrom: no such file
cannot mount /dev/sda2 on /cdrom: no such file
...
...
could not find any media with live CD data (or something similar)

What's up?

Thanks!

---

### Post by strangedata on 2007-06-27
FYI: The solution posted [_here_]("http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off") solves the problem for me.

I still have to figure out how to make it recognize my wireless card and support 1024x768 resolution though.

---

