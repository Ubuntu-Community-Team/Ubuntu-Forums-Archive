---
title: "How to install stuff"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by bigseb on 2010-03-20
Quick question: how does one normally install software in Ubuntu? Is it best to go through the terminal each time or would double-clicking the icon do the job.

In another thread where I wanted to install a driver for my graphics card it was suggested I type 'sudo sh /(cut and paste filename here)'. Can I use the same approach the other software?

---

### Post by Fiahhh on 2010-03-20
The most common method of installing software would be using 'sudo apt-get install [package]'. Just google to find out what the [package] is named.

Another method includes downloading a .deb file through an HTTP Server/Web browser, which are basically double-click installs.

There's also the choice of downloading the source code and compiling it yourself. Some software is only available through source, so you may have to get used to compiling source code yourself.

Oh, and there's also the handy Ubuntu Software Center, which can be found in the Applications menu thingy at the top. Additionally, in System > Administration, you can find the Synaptic Package Manager, though you shouldn't need to use that much.

---

### Post by ad_267 on 2010-03-20
Applications -> Ubuntu Software Centre is the recommended way to install most things.

Otherwise find a .deb package on the internet if you can.

---

### Post by Sef on 2010-03-20
Easiest way to hardest ways to install for software that Ubuntu has in its repositories:

1) Applications > Ubuntu Software Center

2) System > Administration > Synaptic Package Manager

3) Applications > Accessories > Terminal > type in command and package name

Note: Some software may need universe and multiverse enabled.


Easiest way to hardest ways to install for software that Ubuntu has not in  its repositories:

1) Deb package

2) source code > compile

---

### Post by bigseb on 2010-03-20
It was a deb package. I installed it now I can't find it, I assume there should be a link in Applications?!?!

---

### Post by ad_267 on 2010-03-20
> **bigseb said:**
> It was a deb package. I installed it now I can't find it, I assume there should be a link in Applications?!?!

That depends on what it was. Not all software is a graphical application you run from a menu. What exactly was it?

---

### Post by bigseb on 2010-03-20
> **ad_267 said:**
> That depends on what it was. Not all software is a graphical application you run from a menu. What exactly was it?
It was Virtualbox 3.1

---

### Post by ad_267 on 2010-03-20
In that case there should be a menu item. I just installed it and got a "Sun Virtualbox" entry in Applications -> System Tools. I'm not sure why it isn't showing up for you.

---

### Post by bigseb on 2010-03-20
> **ad_267 said:**
> In that case there should be a menu item. I just installed it and got a "Sun Virtualbox" entry in Applications -> System Tools. I'm not sure why it isn't showing up for you.
My mistake, it was there all along. Mea culpa.

However I tried to install XP and it gave me an error. Gonna try a few thing to rectify this.

---

