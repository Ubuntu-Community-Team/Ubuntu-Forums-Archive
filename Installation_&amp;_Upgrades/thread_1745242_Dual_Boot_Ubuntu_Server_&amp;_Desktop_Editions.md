---
title: "Dual Boot Ubuntu Server &amp; Desktop Editions"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Schickles on 2011-04-30
Hello, I had a few questions regarding setting up a Dual-boot of Ubuntu Server Edition and Desktop Editions. First, I was curious if I can download The Server edition directly onto the empty drive I plan on using, or if I have to use a CD or Jump Drive. Secondly I was curious which edition you recommend for a server I plan on using for practice on Web Development, I don't plan on having the practice site live for any extended period of time, only long enough to test functionality. If you have any other suggestions as to how I could do that feel free to comment. Another Note is that I'm a fairly new Linux convert I previously used windows, and I have never run a server, so this is a pretty big first time.

---

### Post by MAFoElffen on 2011-04-30
> **Schickles said:**
> Hello, I had a few questions regarding setting up a Dual-boot of Ubuntu Server Edition and Desktop Editions. First, I was curious if I can download The Server edition directly onto the empty drive I plan on using, or if I have to use a CD or Jump Drive. Secondly I was curious which edition you recommend for a server I plan on using for practice on Web Development, I don't plan on having the practice site live for any extended period of time, only long enough to test functionality. If you have any other suggestions as to how I could do that feel free to comment. Another Note is that I'm a fairly new Linux convert I previously used windows, and I have never run a server, so this is a pretty big first time.
Well- Here goes with my experience on this--
I originally thought (many moons ago) that I would do this same thing = Run a multi-boot server and separate desktop... for development.  It just didn't work that way.  Only one was booted at a time.

So I did some homework.  I found for the best performance of my dev work and with testing in my desktop, that what I "really" needed was to install the server services to my desktop edition.  Then I could test my work from a browser (and other routes) through my local host... Similar in practice to Window's Open IIS Manager (IIS 7)  

Today, even though I've grown to multiple PC's and dedicated servers, I still run server services on my dev box, so I can develop and test without affecting what it outside that.

I've tested and installed linux desktops on top of "servers" and the priority goes to the server services and the desktop services are slower and lag.  Just how the kernels are configured and how it does scheduling differently.

You can do the same by doing everything in virtual, with a virtual desktop talking with a virtual server, but I didn't like the performance issues with that also.  

What I settled on for dev work, ended up as the easiest to setup and maintain, with the best performance overall.

---

### Post by Schickles on 2011-04-30
Well That isn't what I wanted to hear! lol. Thank you for the information, and with that advice I think I might just seek out another solution entirely, seeing as I plan on using this computer personally and for gaming and don't want to take away its performance. Thank you again.

---

