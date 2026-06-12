---
title: "Locking up"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by init6 on 2006-06-04
Ok so I download the liveCD and booted up.  About 30 seconds to 1 minute after it gets to the desktop it freezes the system.  Did this on my laptop and my desktop.  So I download the alternate install and run it on my laptop.  Install went off without a hitch but after rebooting I get the same deal.  About 1 minute after getting to the desktop locked the system.  

Any ideas?

---

### Post by John.Michael.Kane on 2006-06-04
We are going to need spec's on both systems. if any help is going to be given.

---

### Post by init6 on 2006-06-04
That would help wouldn't it.

Laptop is a Dell XPS. 3.2 GHz Intel processor, 1gb ddr400 ram, ati 9800 agp video.

Desktop is 3.2 GHz Intell Prescott processor, 2gb Corsair dual channel DDR400 ram, ati 9700 pro.

I've had these issues with previous versions of Ubuntu as well so I've been using Gentoo.  

I've been messing with the new install on the laptop and as long as I don't do anything after it boots it sits fine with no trouble.  As soon as I open a web browser, start software updates, or anything other than a shell it seems, it'll hang in about 30 seconds.

---

### Post by John.Michael.Kane on 2006-06-04
init6 are you using the standard kernel when using ubuntu? also are these cpu's HT based?

---

### Post by init6 on 2006-06-04
Yes, they are HT processors.  Yes, I'm using the default install.  

Are you in IRC atm?

---

### Post by John.Michael.Kane on 2006-06-04
init6 #ubuntuforums all members of the forums are welcome to join.

Also if you can try installing the smp-kernel for your cpu i think this could be the cause of the lockup's

---

### Post by init6 on 2006-06-04
I'll give it a shot.  Is there an option during the install to choose this kernel?  I'm not sure I can keep the machine working long enough to install it after the fact.

---

### Post by init6 on 2006-06-04
I managed to get the machine stable enough to run a terminal.  I then could install a new kernel from the command line.  I tried 686 and 686-smp.  Both still lock up if I try to do anything else.  It's almost like the ati graphics gets confused.  

Regardless, Ubuntu stock is dropping really fast with me.  I quit using version 5 after about 3 days because of the same problems.  Gentoo hasn't argued with me once.  I figured I'd give Ubunut 6 a shot because I really like what y'all have done.  However, it's useless to me if I can't do anything with it.  

I'm going to investigate new ati drivers and see if that helps.  If that doesn't work I'm probably going back to gentoo.  If y'all come up with any other ideas to try I'll give them a whirl first.  I'd really like to get this runnning.

---

