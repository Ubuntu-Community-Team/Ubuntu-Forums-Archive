---
title: "Leaving USB mouse for 2 seconds acts like mouse click"
date: 2015-02-13
forum: Installation &amp; Upgrades
---

### Post by resander on 2015-02-13
On Ubuntu 12.04LTS on Dell 64-bit desktop.

Moving the mouse in any program and letting it rest for about 2 seconds makes the mouse emit a click by itself. For example, moving it to the shutdown button (removing the finger first) activates shutdown. In an editor/word processor leaving the mouse beyond the right hand edge of text causes the mouse to move back to the last character on the line which is the action of a click.
I tried: 

 - two other mice, removed other USB devices and checked all USB ports with same result.
 - dual-booted Windows 7 and found the same mouse worked
 - Ubuntu 14.04 in demo mode and the same mouse worked
 - on going back to 12.04 the mouse was still not working

It seems 12.04 is causing the problem, but everything has worked fine for nearly three years.

I have a very large number of files on the Ubuntu 12.04 desktop, so replacing Ubuntu 12.04 with 14.04 is going be a big and lengthy job.

Is there something else I could try first?

Ken
P.S. I noticed problem first time this morning (Friday 13 Feb).

---

### Post by resander on 2015-02-13
I logged in as admin user and created a new user for myself. That cleared the mouse problem. So, the problem is caused by something going on in my 'old' user name. 

A virus? It seems to be engineered to cause maximum disruption. The autoclick after a second makes operating the mouse almost impossible. Then a second malfunction that I did not notice before is that a submenu shoots out and is visible only for about a second and then retracts back. You have to be quick to be able to jump across onto the submenu!

Also, when still being admin user just after having created the new user I noticed a message popping up '/usr/bin/twistd failed'. Name twistd is strange and strange it failed like that.

---

### Post by resander on 2015-02-14
Googled and found that twistd in /usr/bin is a Python Linux addon/plugin, so it is not the cause of my problem.

---

### Post by coldraven on 2015-02-14
Did you look in "Startup Applications"?
BTW I recently bit the bullet, backed-up all my stuff and did a fresh install of 14.04. It's much better than 12.04 on my elderly dual-core laptop.

---

