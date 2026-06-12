---
title: "Some questions about Ubuntu"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by dominik_l on 2005-06-15
Hi,

I gave (K)ubuntu a try and installed it on my notebook, and I was really surprised. I suppose it's the best linux for notebooks/desktop. But before I install it on my desktop pc (currently Suse 9.2), I have a few questions.
The main points why I want to change from Suse is that there's no apt, the package management sometimes drives my crazy, especially if I want to install video codecs, and tools like transcode. What's about these things in (K)ubuntu? Is it a problem, getting this tools/codecs?
Another question: When installing (K)ubuntu, is it possible to create a linux software raid? I can't remember such an option when I installed it on my notebook.
And a very special question, but perhaps somebody here has an A8V mainboard and uses the integrated promise s-ata raid controller: Does the current kernel support this controller? I heard something about that it was supported by 2.4.x kernels, but it was kicked out since 2.6 kernel.

Best regards,
Dominik

---

### Post by SGC on 2005-06-15
For the codecs and transcode do the following:

Add this to */etc/apt/sources.list*
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Then type this in the terminal:
 
apt-get update
apt-get install w32codecs transcode

---

