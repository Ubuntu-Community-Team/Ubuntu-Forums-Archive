---
title: "Strange command line - what do I do?"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by SoftWhip on 2007-12-23
I have installed Ubuntu Studio on my laptop, which went okay (used the whole hard drive for it) until the reboot - but after entering my login details I now have the command line;

david@ubuntuhome:"$

What do I do now? I'm confused, as I thought the main user interface would load up.
If you could help at all it would be much appreciated!

Dave.

---

### Post by mikewhatever on 2007-12-23
For some reason, the GUI is not working. The line you see is a command prompt, meaning you should be able to type things. I am not familiar with Ubuntu Studio, yet, you could try:
sudo startx
sudo /etc/init.d/gdm start

You'll probably get a bunch of errors, but they may provide a clue to what's wrong.

---

### Post by SoftWhip on 2007-12-23
Thank you for that advice. I will certainly try it, however I am currently in the middle of installing the regular version of Ubuntu, which seems to be working okay. I think I'll leave the Studio version for a few days, see how I get on with the mainstream Ubuntu version.

Thanks once again!
Dave.

---

