---
title: "laptop strange hanging"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2010-11-25
I am experiencing a strange behaviour just after having installed Maverick on my HP 6730b laptop: any application in Gnome gets stuck until I move the mouse! Even the cursor movement, e.g.: when writing in a terminal window (or in a file editor, or OOo writer etc.) if I keep the space bar depressed, I get a space and one only, but if at the same time I move the mouse, the cursor start running and it runs just until I keep the mouse in movement. And in Thunderbird: I get a message open only after a mouse movement... 
That sounds VERY strange to me... Maybe it's just a trivial problem.
Any idea around???

---

### Post by dino99 on 2010-11-25
seems to be a memory issue: check the driver activation (system admin additional driver)

sudo dpkg-reconfigure -phigh -a

and watch the logs (xsession-errors into /home, ctrl+h to unhide it)

you can set system-monitor icons on top panel to see how memory is used, and wath the overran processes

---

### Post by Gingalone on 2010-11-26
> **dino99 said:**
> seems to be a memory issue: check the driver activation (system admin additional driver)

I got:
No proprietary drivers present on this system

> **dino99 said:**
> sudo dpkg-reconfigure -phigh -a

and watch the logs (xsession-errors into /home, ctrl+h to unhide it)

I got a lot of critical warnings and many "errors" but I can't read the long cryptic list...

> **dino99 said:**
> you can set system-monitor icons on top panel to see how memory is used, and watch the overran processes

Even a rsync backup hangs and the system-monitor as well, it runs only if I move the mouse... (Argh...)

???

---

