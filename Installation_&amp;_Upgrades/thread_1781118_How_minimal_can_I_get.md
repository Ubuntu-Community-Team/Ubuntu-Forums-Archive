---
title: "How minimal can I get???"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2011-06-13
Hi all,

I have recently done a minimal install of Ubuntu and it is great; fast and very few apps installed, I'm adding them as I go and figuring out what I need.

Although it doesn't install a lot of apps, it does install a lot of other things, like drivers, which I will never use (don't have the hardware). My questions are:

**1/** Is there anyway I can install specifically for my hardware setup and leave all other drivers off the machine (not plopped on the hard drive and unused but never there in the first place)? 

**2/** Is there anyway I can just install what I want, no packages that I 'might' want to use one day sitting there taking up space and doing nothing?

Apart from weeding out Synaptic Manager for hours and completely removing things I don't know of any way of achieving what I'm after. Does anyone else?

I do remember seeing, when I first got into Ubuntu, an install where you could select the hardware drivers specifically for your machine as you were installing but don't remember what that was or what it was called. 

I also remember that some of the questions it asked I couldn't answer and perhaps only a computer engineer could (re hardware questions). I'm not talking about drivers for CD, hard drives, etc, but for specific components on the motherboard also. I have no idea about that but guess I could spend some time researching it.

My aim: An install with a handful of drivers specific to my hardware, a desktop environment and a handful of essential apps. 

All ideas welcome ... ;)

---

### Post by sanderd17 on 2011-06-13
I think Arch is better in this kind of work than Ubuntu. Ubuntu is build to have almost everything out of the box.

---

### Post by Bucky Ball on 2011-06-13
Brainstorm. Custom kernel, that is what I'd tried back in 2008 but didn't know what was safe to disable in the kernel. Think I'll give it a go as described here:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

... and start by removing the obvious that I really don't need and never will. The custom kernel also gives the option to choose which hardware drivers are used. That is the bit I got lost on. Sounds obvious, but to me, wasn't.

Wonder if there is a log of the packages I am using? I'll keep digging ...

---

### Post by Bucky Ball on 2011-06-13
> **sanderd17 said:**
> Ubuntu is build to have almost everything out of the box.

Yes, a regular Ubuntu Desktop Edition install is, but the minimal install certainly isn't. Neither are the vanilla or server kernels . . ;)

Arch looks interesting, cheers. I might fiddle around with that some, too.

---

### Post by Bucky Ball on 2011-06-13
This file looks interesting:

/boot/config-2.6.38-020638rc2-generic

(Replace the kernel number with yours.) Sure I could do a lot of damage tweaking that! Under 'Modify the source for your needs' on this page:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

* UPDATE: From later on in the above link:

> Since the 2.6.32 kernel, a new feature allows you to  update the configuration to only compile modules that are actually used  in your system: 
```
make localmodconfig
```

Exactly what I was looking for. It is possible to install just the modules my system is using. ;)

---

### Post by StrayEddy on 2011-06-13
+1 Arch

---

### Post by snowpine on 2011-06-13
There is **no advantage** to removing hardware support from Ubuntu (unless you have an *extremely* tiny hard drive).

If you're doing this as an aesthetic challenge or thought exercise, I think you'll have best results if you use a distro like Gentoo or Linux From Scratch and learn to compile a custom kernel.

---

### Post by Bucky Ball on 2011-06-13
I'm halfway through the localmodconfig now but stuck just before installing the kernel using the guide on [this]("https://help.ubuntu.com/community/Kernel/Compile") page. Can anyone work out what the part in bold is supposed to be? I have tried all combinations:

```
fakeroot make-kpkg --initrd --**append-to-version=-some-string-here** kernel-image kernel-headers
```And anyone got any ideas how I might do this?

> ... Ubuntu kernels build with debugging information on, which makes the  resulting kernel modules (*.ko files) much larger than they would  otherwise be. To turn this off, go into the config's "Kernel  hacking"<!-- ; then, under "Kernel debugging", --> and turn OFF  "Compile the kernel with debug info". 
 I will post another thread regarding these issues. I think this one is pretty much solved. My question is answered. Thanks all for your clues and ideas and I will definitely take a closer look at Arch. ;)

---

