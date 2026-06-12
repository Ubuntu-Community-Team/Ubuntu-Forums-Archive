---
title: "Ubuntu Won't boot after 9.10 upgrade"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by goldfish2 on 2010-03-27
I just upgraded from 8.10 -> 9.04 -> 9.10 today.  Now my system seems to only boot every 3rd time or so.  When it doesn't boot, none of the tty1-6 load at all, and I get an error message 

"init: ureadahead-other main process (2930) terminated with status 4"

(But I've been told there is a good chance it is unrelated).

When it DOES boot, I can only get to the tty session and have to start gdm manually with "sudo gdm".

I'm guessing this isn't enough information... what log files do I need to add to be able to give more information?


Unrelated rant:

[SIZE="1"]What is going on with Ubuntu? I switched to it a few years back because it just always worked and spent much less time maintaining... but now its getting terrible.  When I first switched to 9.04 (several months after its release) I had a issue shared by tons of others with HALD not working properly and thus the keyboard and mouse would freeze on boot making the system useless.  I ended up having to install a copy of 8.10 over it.  Even 2 months after this experience no one had fixed it... tons of confirmed bug reports with no resolution, dozen of open threads without even a single person suggestion some hope of resolution.

I finally decided to cross my fingers and dive in today (its been almost a year since the 9.04 release, should be safe?) because I'm sick of my software not being able to upgrade to the latest and not being comparable because I'm stuck in 8.10.  The 9.04 upgrade work, but only long enough apparently to lead me into another completely different system crashing bug in 9.10.  This really sucks guys.[/SIZE]

---

### Post by goldfish2 on 2010-03-27
This morning it failed to boot again, and then I rebooted.  Now the sound doesn't work (when I go into preferences sound it just says "waiting for sound system to respond").  My tty1-6 all have huge font that mostly looks like jibberish.  And my computer beeps at me randomly and produces a redish box in the top left 100x500 pixels or so of my screen that tints everything up there red until an application is moved over it (but the mouse doesn't clear it).

I am not having a good day.

---

### Post by goldfish2 on 2010-03-27
I upgraded to grub2.  This also moved me to the latest kernel, which I apparently wasn't loading.  This may have been the source of ALL these problems.

---

