---
title: "does Ubuntu support hyperthreading?"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by scorpio2002 on 2005-07-19
Hi there! I noticed that Ubuntu is running with a normal kernel but I do have a P4 Prescott, so it should use a smp kernel supporting multi-processor HAL.

How can I install a smp kernel?

---

### Post by gb25 on 2005-07-19
There's an smp kernel in synaptic.  You could try that.  Just search synaptic for smp.  Or you could compile the kernel and add in hyperthreading support that way.  That's the way i did it, and it worked fine.

---

### Post by scorpio2002 on 2005-07-19
Hi there! Bad news :|
I got the smp kernel from Synaptic but it doesn't work properly. When I boot the smp kernel, after less than one minute, the screen simply freezes and the machine stops working hoplessly. 

I must admit that this used to happen when I had Fedora core 3, so I'd got used to working with no smp. But when I installed Fedora 4 everything worked fine with the smp kernel. The kernel version was 2.6.12-1. 

Now I think those freezes I get are due to the old smp kernel(v 2.6.10-7) which is available on apt. Do you know where I can get a newver version? Thank you ^^

---

### Post by gb25 on 2005-07-19
I just downloaded the one from kernel.org.  At the time it was 2.6.12.2, but now it's 2.6.12.3.  With that kernel, you'd have to compile it yourself though.  I'm not sure where to find a newer prepackaged smp kernel though.  Maybe the linux-image-2.6.11-1-686-smp package in synaptic will work.  I don't know.

Where does the booting hang at?  Is there any error or anything?

---

### Post by scorpio2002 on 2005-07-19
> Where does the booting hang at? Is there any error or anything?

The boot works just fine. Then I get into Ubuntu and i start using it. Randomly, after some seconds I'm using it, the screen just freezes as I said and there's nothing I can do. The machine stops and I can't even access a console by typing CTRL-ATL-F1...

Never understood why. Only with the latest kernel available in Fedora 4 I get HT to work fine. 

I've never compiled a Kernel myself, but I'd like to try. Could you help me? :D

---

### Post by mingus on 2005-07-19
It might pay to look further into setting up the stock kernel.  I can't speak to Ubuntu's 2.6.10 smp, but on another box I have the SuSE 2.6.8 smp kernel, and it works fine.

---

### Post by scorpio2002 on 2005-07-20
mingus, how do I look further into setting up the stock kernel?

Anyway, if with fedora and the latest kernel it worked fine, I think it is worth compiling the latest kernel on Ubuntu. But, as I said, I need some help because I'm not an experct.

My aim is to get a kernel configured the same way as the one provided with ubuntu which is really fast. Which forum I have to post in to get help with kernel compilation?

---

### Post by mingus on 2005-07-20
I would try posting to the "hardware" forum.  I can't help you on this one with the kernel.  My kernel experience is with Gentoo, and that is a *totally* different approach.  And some with SuSE, which I suspect is similar to Fedora.  But like yourself, I am still learning Debian.  Sorry I can't be of more help.

PS.  Re Prescott performance:  I've been dissappointed.  I architected that box carefully, so I've got HT set up but also optimized the FSB and RAM.  I suppose if I were using games built especially for HT it would be different, but I don't.  For regular use - with a smp kernel and reiserfs - no faster than my Athlon box.  Now that I think about it, the only noticeable diff in speed between distros I've seen, other than a custom Gentoo kernel, is with YOPER - it will detect and install the kernel you need, will optimize it, uses reiser4 - a very sweet power-users distro.

---

