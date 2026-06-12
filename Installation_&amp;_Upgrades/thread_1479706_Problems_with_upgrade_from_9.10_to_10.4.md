---
title: "Problems with upgrade from 9.10 to 10.4"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by spinlock99 on 2010-05-10
I've just upgraded my Dell Inspiron 600m from ubuntu 9.10 to 10.4 and ... I'm a bit disappointed with this new release. I have 3 main issues to resolve (so far):
[LIST=1]
[*]Performance - my machine is thrashing fiercely right now even though I'm only running Firefox.
[*]Suspend is now broken (was working before) :(
[*]Networking - "works" but is rough around the edges. I need to enable networking whenever I boot up and 10.4 doesn't recognise the ethernet cable when it's plugged in.
[/LIST]
So, I'll be cataloguing my attempts to tune 10.4 to a more usable state in this thread. If you have any suggestions please feel free to leave a comment :) Thanks.

---

### Post by Tiberion on 2010-05-11
Spinlock I am having similar issues.  Performance down by 15% and my networking is disabled by defualt.  There used to be a place you can set those preferences.  I can't seem to find it now.

---

### Post by varanasi on 2010-05-11
Upgrading was a disaster for me.  The upgrade stalled and restarting resulted in an unbootable installation.  After running in safe mode, I managed to get a clunky, difficult to use computer.

I would say, don't screw around, do a clean install.

But even doing a clean install wasn't painless.  Although the installer doesn't mention this, it goes much more smoothly if you establish a network connection (using the live cd) and then do the install from that point.

I should note, this is the first time I have had trouble with an install.  I'm not a linux guru but I've been using it for over a decade.

---

### Post by spinlock99 on 2010-05-11
I wrote a post about what I'd tried to do to get power management running again. Unfortunately, I had to reboot before I could get it on the forum. Maybe later :mad:

I've been running htop to try to get a feel for why the performance on my machine is so horrible and I'm beginning to notice that I'm leaking memory when I run a web browser (I've tried firefox and opera so far). I don't think this is just web browsers but I can't use my system for much of anything else at this point so that's where I am. I did notice that my system will reclaim it's memory from opera and function normally when I restart the application. Firefox is a different story. I have to reboot the machine to get my memory back when I've been using firefox for a while.

The really strange thing is that both firefox and opera spawn multiple threads for libraries! Right now there are 12 instances of /usr/lib/firefox-3.6.3/firefox-bin. Each is consuming 18.7% of my memory. Now, I'm no expert here but shouldn't you only have 1 copy of a library in memory that multiple processes share? 12 instances to run 2 open tabs is a bit ridiculous.

Anyway, at least I've started to figure out why my performance is so bad. I'll start using opera (kind of a bonus because I haven't had a chance to check it out yet) and restarting every couple of hours to reclaim my memory. That should keep my system usable until I can find a solution.

---

### Post by spinlock99 on 2010-05-11
I think the issues with networking may have something to do with a hard reset as a result of power management not working. I noticed that when I booted up this morning my wifi connection worked fine and it even recognized the wired connection when I plugged in an ethernet cable. After trying to hibernate and having to do a hard shutdown of the system, networking was disabled when I booted back up.

---

### Post by Tiberion on 2010-05-11
That is interesting, though I have got away from using Hibernate/Suspend due to obvious issues, my networking is enable on my last hard restart but not the time before.  I have had a similar problem with Cups on my tower.  Every now and again I have to restart the service from terminal to load my networked printer.

---

### Post by lactosefighter on 2010-05-11
I upgraded from 9.10 to 10.04 and got the dreaded blank screen after rebooting. I pressed esc on boot to enter recovery mode and the selected safe graphics mode. I found xorg.conf missing. I tried every fix I could find but the best I could get was 800x600 resolution without any desktop effects. Firefox also didnt work. I had to reformat and go back to ubuntu 9.10 :(

---

### Post by lactosefighter on 2010-05-11
I tried a fresh install of ubuntu 10.04 on all my machines. Firefox doesnt work on any of them even though I could download and install and update software using synaptic. My older machine just displays a blank screen after installation.  Does this mean I cant ever upgrade from the older versions of ubuntu? Will these issues be fixed?

---

### Post by wcdsugpy on 2010-05-11
> **spinlock99 said:**
> I've just upgraded my Dell Inspiron 600m from ubuntu 9.10 to 10.4 and ... I'm a bit disappointed with this new release. I have 3 main issues to resolve (so far):
[LIST=1]
[*]Performance - my machine is thrashing fiercely right now even though I'm only running Firefox.
[*]Suspend is now broken (was working before) :(
[*]Networking - "works" but is rough around the edges. I need to enable networking whenever I boot up and 10.4 doesn't recognise the ethernet cable when it's plugged in.
[/LIST]
So, I'll be cataloguing my attempts to tune 10.4 to a more usable state in this thread. If you have any suggestions please feel free to leave a comment :) Thanks.
In my case 9.10 was working fine on my HP Pavilion laptop until I upgraded to 10.04. Now Ubuntu won't boot up and I'm left with a black screen. Not sure what to do here.
wcdsugpy

---

