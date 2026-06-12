---
title: "644 Updates!!??"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by namelessone on 2007-01-13
I turned on my computer this morning to discover that there are 644 updates for my computer. That is demented! Was there a major update to the Ubuntu repositories, or am I going crazy (or both)?

I guess I should mention that I recently added a line to my sources.list file:

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

I added this for easycam2 (followed the some ubuntu.help instruction...can't find the link again) is this my problem?

EDIT: I guess this extra line in my sources.list file is the answer. I still want to know if it's alright to install other things from this non-ubuntu repository (in particular, the newest version of  libqt4-core and stopmotion). If so, I could just add the debian unstable repo, install the stuff I want, and then remove it from sources.list.

---

### Post by mojoman on 2007-01-13
> **namelessone said:**
> I turned on my computer this morning to discover that there are 644 updates for my computer. That is demented! Was there a major update to the Ubuntu repositories, or am I going crazy (or both)?

I guess I should mention that I recently added a line to my sources.list file:

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

I added this for easycam2 (followed the some ubuntu.help instruction...can't find the link again) is this my problem?

Should be easy to find out. Comment out blognox in your /etc/apt/sources.list (using #) and then do ```
sudo apt-get update
``` If you have a slighty more sane number of updates available after that the rest of the updates (i.e. the one that you can't see after this) should come from the blognux repository.
/Mojoman

---

### Post by confused57 on 2007-01-13
> **namelessone said:**
> I turned on my computer this morning to discover that there are 644 updates for my computer. That is demented! Was there a major update to the Ubuntu repositories, or am I going crazy (or both)?

I guess I should mention that I recently added a line to my sources.list file:

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

I added this for easycam2 (followed the some ubuntu.help instruction...can't find the link again) is this my problem?

EDIT: I guess this extra line in my sources.list file is the answer. I still want to know if it's alright to install other things from this non-ubuntu repository (in particular, the newest version of  libqt4-core and stopmotion). If so, I could just add the debian unstable repo, install the stuff I want, and then remove it from sources.list.

There's a very good chance you'll break your Ubuntu installation, especially since you're using the unstable repo...if you don't have anything you mind losing, it would be a learning experience...let us know of the packages you were able to install successfully, I'm sure many people would be interested.

---

