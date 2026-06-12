---
title: "Boot Error after Fresh Install and Updates - Ubuntu"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by whitlecj on 2011-01-14
I installed ubuntu 10.10 last night on my laptop.  Installation went well and I had updates to install after the install from the disk.  After installing the updates, every time I boot up the machine, I see an error message while ubuntu is starting up before it gets to the splash screen.  Ubuntu boots up fine and seems to work fine but I was just concerned about the error and didn't know if there is anything I can do to correct it.  The error is only on the screen for a split second but it says something like "Fatal: could not load lib modules 2.6.35 ..." It has this message displayed twice (on 2 lines) but again it is only up for a split second.  Any ideas on what this could be?

---

### Post by Rubi1200 on 2011-01-14
Hi and welcome to the forums :)

How did you install Ubuntu and what other operating systems are on the computer?

---

### Post by whitlecj on 2011-01-14
I installed from the live cd.  This is the only operating system on this computer.

---

### Post by whitlecj on 2011-01-14
I installed it from the live cd and this is the only operating system on this computer.  thanks.

---

### Post by whitlecj on 2011-01-14
I installed it from the live cd and this is the only operating system on this computer.  thanks.

---

### Post by whitlecj on 2011-01-14
I installed it from the live cd and this is the only operating system on this computer.  thanks.

---

### Post by whitlecj on 2011-01-14
Sorry for the duplicate posts.  Not sure if the site was having a problem when posting or if it was on my end.  Sorry

---

### Post by Rubi1200 on 2011-01-15
Sorry for the delayed response; it seems the forum is experiencing some kind of overload.

What I suggest is the following; if Ubuntu is booting normally except for the messages, try looking in the logs for references and post it here.

For example, in the terminal:

```
egrep -e fatal /var/log/dmesg

egrep -e modules /var/log/syslog
```

You can also play around with other search parameters.

---

