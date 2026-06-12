---
title: "Distribution upgrade 'stuck'"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by escalated on 2007-03-19
I decided to try and play with feisty fawn, I realize that it's not officially supported, still beta, etc..so feel free to yell/berate me below(although i'd prefer a solution :P)

I started the upgrade manager the official way 'update-manager' etc..

However, now, it is stuck on the 'fetching and installing upgrades' step, specifically, configuring libgstreamer.

The last thing in the little >terminal box on the distribution upgrade window says:

Setting up libgstreamer-plugins0.8-0 (0.8.12-6ubuntu3) ...

It's currently just sitting there, apparently, doing nothing.

Any help is appreciated, thanks.

---

### Post by escalated on 2007-03-20
Well, in case something similar happens to someone else, ill just let everyone know what has happened so far.

I had run update-manager from a console, so, i just closed it and it closed.  Then i tried to run it again -- no luck(spat out some python error..something about pygtk iirc)

Then, between apt-get install -f and dpkg --configure -a (dont know what order, or how many times i ran them, but i ran them!) i got done what i could, and attempted to reboot.

It wouldnt boot. no worries <grabs knoppix cd>

I end up chrooting into my normal ubuntu root dir and running the apt-get and dpkg stuff from before --this time i get alot of errors about not being able to create /dev/null (wtf? i made the drive writeable..)

So, after screwing around with knoppix/chrooting/dpkg/apt-get i reboot, yay! it boots..now i can run these commands from within ubuntu! (that's where im at so far.)

</self reply> :D

---

### Post by Kateikyoushi on 2007-03-20
After it hang there wasn't much we could recommend to do, other than what you did but thanks for sharing your solution.

---

