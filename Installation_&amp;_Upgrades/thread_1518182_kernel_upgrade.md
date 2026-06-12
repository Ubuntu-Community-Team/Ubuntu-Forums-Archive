---
title: "kernel upgrade"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by agentchange on 2010-06-26
I just did a kernel upgrade and since I have limited hd space, I am wondering why the source directory (usr/src) created was so much bigger than it was previously, 4 GB compared to maybe 500 MB?   I think it has something to do with the fact that i got it from kernel.org when i should have maybe gotten it from ubuntu or just somehow gotten a patch.  

What I was missing was support for 3d on my intel glx on-board video card 915gl.  The 3d works just fine now although I'm getting a few unimportant messages at startup, mostly from trying to enable a few things that I didn't actually have. 

If I had done it through ubuntu with git, is it likely that I would have been able to access this feature?  I found this one package in git that looks like it would probably have it, sconklin/drm-intel.git , short for Direct Rendering Manager.  Would it have taken up the same amount of space as the one at kernel.org?  

Lastly, how would one go about addressing this with a patch, if that is even possible?

---

### Post by ajgreeny on 2010-06-26
That's an enormous /usr/src.  There are just 4 folders in mine, two for each of the two  linux-header versions on my system.  What is in your system that has added 4GB?

Perhaps you could have got your kernel update from the ubuntu ppa
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by agentchange on 2010-06-26
It just seems like maybe somehow included every possible feature and item that could possibly be included.  I don't remember being prompted for that many specifics about my hardware and system.  First time for everything.    Each one of the directories has hundreds or thousands of items in it.

2 folders, one for kernel and one for headers.  kernel has 73,000 items, 3.8GB, and headers has 12,000 items, 34MB.  The majority of it is in drivers, 22,000 items for 2GB.  I am guessing that if I had an ubuntu kernel, all of these items would already be somewhere else on my system.  What purpose do all of these subdirectories in /usr/src supposed to have?  

Ah-hah.  I have downloaded a lot of games, mainly just to try them out.  I hardly even play.  So what is in /usr/src is a copy of all of the drivers I have, etc.?

The thing is that I know 3d did not work for my intel card using the default kernel from the lucid install, and this video card has been around for over 5 years so if it was going to be included in the default kernel, it would already be there, so i probably still have to create my own.  if i use git, will i be presented with lots of options to choose from in configuration?

---

### Post by ajgreeny on 2010-06-26
Sorry, I've no idea about that.

---

