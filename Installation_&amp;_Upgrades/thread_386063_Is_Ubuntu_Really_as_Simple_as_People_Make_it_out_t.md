---
title: "Is Ubuntu Really as Simple as People Make it out to be?"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by spacemanspork on 2007-03-16
I really have to say the answer is no.

It might be the fact that I'm in a special situation, but here's my experience with Ubuntu.  After hearing all this great stuff about Ubuntu and finding out WINE is pretty good now, I decided, heck I'll install Ubuntu.  I have a Compaq with an AMD 64 3400+ chip.  Obviously Windows XP is installed and I figured I'll run a dual boot machine.  So the steps I took.

1) I repartitioned my second hard drive into 3 pieces. One for the Linux root, one for Linux swap, one for just holding data in NTFS format.
2) I booted up the 6.10 CD
3) I ran the installation
4) It installed.  It asked me to reboot.
5) It didn't seem like my machine rebooted, but it gave me a menu of which OS to load.
6) I picked Ubuntu and it loaded great.

All good right?

Next thing, I'm using wireless (Netgear WG111) so I looked up on how to get it to run in Ubuntu.  Ndiswrapper is the answer.  Ok... so I load up a console and type ndiswapper.  It's unrecognized.  Great.  I look up on how to install it.  "Go through the menu and the package manager and add it".  I go there and... Ndiswrapper isn't an option to be added.  I looked up the help file in Ubuntu and it said the same thing.  Wtf?  I might've missed something really simple, but it wasn't in the list.

Sigh, no big deal.  I downloaded it on my laptop, moved it to a thumb drive, copied it over (Ubuntu saw my thumb drive just fine, which was a very pleasant surprise).  I copied it over, ran the make uninstall, then the make.  Which came back with a BUNCH of errors.  UGH.  Installation didn't work needless to say.  I said, screw this and I decided to just try it later, shut down and rebooted my machine.

Noticed it went STRAIGHT to Windows.  No option whatsoever to load up Ubuntu.  So... now I have Ubuntu installed, but I can't access it.  I also have no idea why I can't install Ndiswrapper thru the package manager (which apparently should be the easy way to do it) plus I can't make it either.

I just needed to rant and maybe someone can tell me what's going on wrong.  I have a feeling it's something really stupid though.  I'd be a lot more patient figuring it out if I had internet access when I loaded Ubuntu.  But I guess that doesn't change the fact that I can't seem to load it again.  I guess that would be the biggest issue... why aren't I given an option to load an OS?  It goes straight into Windows XP... It might be because of the way the Compaq computer is set up though.  I didn't think I'd need to tinker with the BIOS... I'll have to look in on that I guess.

---

### Post by eapache on 2007-03-16
You seem to have a really bizarre set of problems. I don't use wireless, so I can't help you there, but I have some suggestions for getting back into Ubuntu.

Try this website: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

and make a boot disk that will hopefully remake the list of os' at boot (follow the site's instructions). Good luck.

---

### Post by jenhsun on 2007-03-16
I did struggle about the wireless problem before. 
Here you might take a look:
[http://www.ubuntuforums.org/showthread.php?t=112526&highlight=WG111](http://www.ubuntuforums.org/showthread.php?t=112526&highlight=WG111)

---

### Post by spacemanspork on 2007-03-19
Thanks for the links.

I'll try it at some point in the future.  Been a little busy recently.

---

