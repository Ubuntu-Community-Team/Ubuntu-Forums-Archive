---
title: "Title bars missing"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by peyre on 2018-11-06
When I upgraded from Xubuntu 18.04 to 18.10, all the title bars in all my windows (also the Xubuntu panel, what Windows calls the Taskbar) disappear.  I've had this happen before, but in the past, I would drop out with Ctrl-Alt-F2, log in and run rm -rf ~/.cache and the problem would go away.  Now it works after the reboot, but the *next* time I start up, everything's missing again.  I backed up my data, wiped the drive, and installed 18.10 from scratch, but I'm having the same problem.  

I've googled the issue and tried lots of things suggested to fix this, but they're all years old and none of them have helped.  Wth do I do to fix this, anyone know?

---

### Post by peyre on 2018-11-13
Bump

---

### Post by peyre on 2018-11-14
Well, never mind.  I started over and did a fresh install on a different hard drive and it seems to have come out ok.

---

### Post by peyre on 2018-11-18
What ?  On reboot it's done the same thing again.  Title bars and the Taskbar are missing on bootup, and it doesn't respond to my volume up/down buttons, and windows don't respond to Alt-F4.  What do I do about this?  It's not usable in that condition.  I can make it work right with the rm -rf ~/.cache trick, but it's simply not practical to do that every time I start the computer.

---

### Post by peyre on 2018-11-18
What the effin' eff?  On reboot it's done the same thing again.  Title bars and the Taskbar are missing, it doesn't respond to my volume up/down buttons, and windows don't respond to Alt-F4.  What do I do about this?  It's not usable in that condition.  I can make it work right with the **rm -rf ~/.cache** trick, but it's simply not practical to do that every time I start the computer.

---

### Post by Adam_GUI on 2018-11-18
When you did the fresh install of 18.10, where did you grab the installer image from?  Was it the 32 or 64 bit image?

---

### Post by peyre on 2018-11-18
Oh good question.  It's 64-bit.

Now I shut down and restarted, and it came up good.  So maybe this is intermittent instead of happening every time.  I'm puzzled!  Xubuntu is a wonderful OS and I hate having to struggle with it.

---

### Post by Adam_GUI on 2018-11-18
When title bars disappear, can you issue an "ALT + F2" input or open xfce4-terminal and issue "xfwm4 --replace"?

You haven't installed anything like Compiz, have you?

---

### Post by peyre on 2018-11-18
And another reboot just now, and it's still working right.  Well wth?  (Ha, only an IT guy like me would say "Oh no, it's working right!")

---

### Post by peyre on 2018-11-20
I'll try that next time it happens, thanks!

No, I haven't installed any other window managers or anything like that, just Web browsers, Wine, and other utilities like gpicview and gnome-system-monitor.

---

### Post by peyre on 2018-11-24
Well bugger, it did it again today.  Very strange!  It seems like it only does it when I'm not expecting it to, so then when I go to troubleshoot it, it behaves.

---

### Post by peyre on 2018-11-24
Well bugger, it did it again today.  Very strange!  It seems like it only does it when I'm not expecting it to, so then when I go to troubleshoot it, it behaves.

---

### Post by peyre on 2018-11-25
> **Adam_GUI said:**
> When title bars disappear, can you issue an "ALT + F2" input or open xfce4-terminal and issue "xfwm4 --replace"?

You haven't installed anything like Compiz, have you?

When I fired up tonight it did the same thing again, so I Alt-F2ed and ran xfwm4 --replace.  It returned:

Gtk-WARNING **: 16:49:xx:xxx: cannot open display:

with nothing following it. Those xx numbers were 31:880 the first time I tried it and 23:903 the second time.

---

### Post by Adam_GUI on 2018-11-25
Do you have xauth installed?

I'm out of ideas.  But, at least you have an error you can use to look-up.

---

### Post by peyre on 2018-11-27
Why yes, xauth *is* installed.  I didn't install it manually though; it must have come piggypacked on something else.  I wonder what.  Would it be a good idea to remove it, or is that likely to break something important?

---

