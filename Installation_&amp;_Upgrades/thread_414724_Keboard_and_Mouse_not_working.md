---
title: "Keboard and Mouse not working"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by catalytic on 2007-04-20
I thought I'd give Feisty Fawn a go, but straight away I'm having issues.

It boots up ok, I can select items from the menu with the mouse. But it wont allow me to select anything on the desktop. Only the arrow keys on the keyboard work. So I use arrow keys and enter to start the installation. I managed to get up to the partitioning bit, then both keyboard and mouse stopped working all together.

Is this a bug?? Is there a fix? How I fix if I haven't even installed it yet?

---

### Post by catalytic on 2007-04-20
It is the desktop version that I am trying to install, and I don't have a USB keyboard or mouse.

---

### Post by catalytic on 2007-04-21
Well I think I may have fixed it, for anyone who is interested....

First off I used my DVD drive instead of my older CD drive, it seemed to work faster and I managed to get Feisty installed.

I found when I went to update, I got an error message saying "could not grab your mouse, a malicious client may be eavesdropping on your session, or a program may be trying to focus."

I did a google search and all I could come up with was that this package may be causing the problem libgksu2-o.

I went into synaptic package manager, and marked this one for reinstallation. Now the mouse seems to be working fine. 

That's enough Ubuntu tweaking for me tonight!

---

