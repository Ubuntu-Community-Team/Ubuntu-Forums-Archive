---
title: "ATI driver in gutsy makes computer unusable."
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by JackLhasa on 2007-10-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/133192](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/133192) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Okay, I just upgraded to Gutsy, and then it asked me to install the restricted ati driver, which I did.  Upon rebooting after this install, the screen displays garbage horizontal lines at login.  nothing can be read and the cursor cannot be found.

After reading some things on launchpad and these forums, I've already tried several "fixes."

First off, I cannot change my xorg.conf file as many of these fixes ask me to do.  When I try to change to /etx/X11/, in the command line, it tells me that this directory does not exist.  doing an ls in /etc/ does not show a /X11/ directory.

Second, I found a suggestion that said to downgrade the driver to the previous Fiesty version.  Upon trying this, the web address that I'm supposed to use for the wget is dead.

Is there anyway at all that I can just downgrade back to Feisty?  I do not want to have to do a clean install.

Thanks,
Jack.

---

### Post by Nakkel on 2007-10-07
You could try to run "dpkg-reconfigure xserver-xorg" on the commandline. That would try to reconfigure your X with fresh settings. If the restricted driver is at fault you should try the free ATI-driver when prompted.

- N

---

### Post by JackLhasa on 2007-10-07
Nakkel, you are a saviour!  I've been reading bug reports and forum posts for a solid day and no one mentioned doing this.  It worked like a charm.

-Jack

---

### Post by JackLhasa on 2007-10-07
Okay, this worked great for getting a working system again.  It even let me set the correct resolution and synch rates for my new monitor.  I've still run into a problem, although it is much less drastic.  I set my video card driver to fglrx, mostly from memory of doing that when I first installed Feisty. 

The only problem left is that when I play movies, the are really choppy now.  Am I using the wrong driver?  I have an ATI Radeon 9550.  Monitor is an HP w1907.

Much Thanks,
Jack.

---

### Post by rockin_goliath on 2007-10-07
No dice for me. I have two solid vertical lines on my screen. I think this is due to the latest ATI driver update. Guess we'll just have to wait for an update that will fix it. Oh well, this is, after all, a beta, and this is where we resolve show stoppers such as this. I have nothing but respect for the Ubuntu Dev's. Keep it up the good work!

---

