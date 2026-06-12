---
title: "Is PAE enabled by default for 32-bit version?"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by irrdev on 2010-06-23
I personally always use 64-bit, but I need to install linux on my family's desktop (8GB of RAM) and have excellent flash performance. As a result, I have opted to use 32-bit. Is PAE enabled by default in the 32-bit Ubuntu linux kernel, or do I need to rebuild it? If it is not enabled, it there an easy way (i.e. launchpad repository) to install a PAE-enabled kernel without building it from source? 
Thanks for your help in advance.

---

### Post by Don Barzini on 2010-06-23
The answer is NO. It is NOT a default.

You need to compile a custom kernel and jump through some other hoops.

PAE is not worth the trouble.

---

### Post by Stereotypical Rage on 2010-06-23
> **Don Barzini said:**
> The answer is NO. It is NOT a default.

You need to compile a custom kernel and jump through some other hoops.

PAE is not worth the trouble.

LOL! Do you even know what PAE is? It's not that hard to use or even enable, especially out of Synaptic/apt-get'ing. I would hardly consider it NOT worth it and "jumping through other hoops" as I personally use it as I have 8GB of RAM myself on a Quad Core. (Used Synaptic, rebooted, selected kernel, all done) I can't think of ANYTHING that I had trouble with as a result of PAE.

@irrdev: This URL might be of some help to you: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Flash 10.1 is 64-bit on Linux(well most platforms) now, if you want to use that. I personally haven't used it on a 64-bit system yet though.

---

### Post by irrdev on 2010-06-23
@Stereotypical Rage
Thank you very much for your help. Adobe removed the experimental Flash 10.1 64-bit from its labs two weeks ago. It is infected by a critical bug which poses a huge security issue. Therefore, I'm definitely going to stick with a 32-bit kernel for now.

---

### Post by Rizlaw on 2010-06-24
> **irrdev said:**
> I personally always use 64-bit, but I need to install linux on my family's desktop (8GB of RAM) and have excellent flash performance. As a result, I have opted to use 32-bit. Is PAE enabled by default in the 32-bit Ubuntu linux kernel, or do I need to rebuild it? If it is not enabled, it there an easy way (i.e. launchpad repository) to install a PAE-enabled kernel without building it from source? 
Thanks for your help in advance.

I have downloaded two copies of Ubuntu 10.04 from two different mirrors and in both cases it appears to install the 2.6.32-xx-generic-**pae** kernel by default. After installing this can be checked with:

> uname -a

I also checked the md5 sums on each downloaded ISO file to make sure the downloads were bit perfect; they were.

So, to answer your question, it seems that the latest Ubuntu 10.04 installs the "pae" kernel version by default. This would be O.K. if you  have 4+GBs of RAM, but on one machine I have only 2GB of RAM and it still installed the PAE kernel. No idea what's going on.

Otherwise, the pae kernel works fine, although I have read you get a small negative performance hit using the pae kernel.

---

