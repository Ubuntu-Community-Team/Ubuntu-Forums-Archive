---
title: "Mouse problem at login screen Ubuntu 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by fernandoch on 2010-05-04
I have just installed a clean Ubuntu 10.04 and I am having problems with my mouse at login. The pointer just goes up and down and I cannot move it to any side. I cannot even login. If I reset the PC, sometimes it works, and sometimes it doesn't.

It used to work properly with 9.10.

Any clues about what could be wrong?

---

### Post by Raptorista on 2010-05-05
I have similar problem: my pointer goes to the left and keeps going even if i take it to the center. I am considering downgrading :)

---

### Post by fernandoch on 2010-05-05
I think this is due to my logitech quickcam :(

When I unplug it, everything works fine.

---

### Post by P4man on 2010-05-05
> **fernandoch said:**
> I think this is due to my logitech quickcam :(

When I unplug it, everything works fine.

thats rather.. bizarre!

BtW, you can log in with keyboard only. Just hit enter on your name, type in your password and hit enter again. of course that is not a solution, but just saying.

Maybe if this happens, you can switch to a full screen terminal with conrol+alt+f1 and have a look in the output of dmesg?

Or check the logs in system > adminstation > log file viewer after a normal log in, and look in the history if there is any clue what happened at the time you did have this problem.

Frankly, I would suspect a problem with the mouse, rather than a software problem, but what do I know, I have never seen or heard of a one directional mouse. its not a mechanical ball mouse is it?

---

### Post by P4man on 2010-05-05
> **Raptorista said:**
> I have similar problem: my pointer goes to the left and keeps going even if i take it to the center. I am considering downgrading :)

You mean on a laptop with an IBM-style track pointer in the keyboard? I have that too now and then, just touching the touchpad seems to make it recalibrate.

---

### Post by Magellan on 2010-10-14
I had a similar problem.
I found a solution and posted it here:
[http://ubuntuforums.org/showthread.php?p=9974626#post9974626]("http://ubuntuforums.org/showthread.php?p=9974626#post9974626")

---

