---
title: "kernel patching advice"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-06-18
Hey everybody!

I am having overheating issues with an old thinkpad and having done some research have drawn up three potential partial solutions:

1) Wait for the next Ubuntu release, apparently 2.6.35 has super duper Radeon GPU (my hot graphics card) power saving features.

2) Patch existing kernel with linux-phc ([http://www.linux-phc.org/forum/index.php](http://www.linux-phc.org/forum/index.php)) to undervolt system (requires recompiling the whole kernel)

3) Hardware mod. Glue in a thermal sink. This is reported to work fairly well.


Anyway, my idea is to combine solutions 1 and 2 and wait till the stable release of 2.6.35, patch it with linux-phc ([http://www.linux-phc.org/forum/index.php](http://www.linux-phc.org/forum/index.php)) and install that on Lucid.

Since I am recompiling and reinstalling the kernel anyway, I may as well grab the latest and greatest and enjoy the benefit of the extra power saving features.

My questions are:

- IS THIS MADNESS?? If I am compiling my own kernel either way, is it a good idea to go ahead and grab the latest kernel instead of 2.6.32?

- If I am compiling my own kernel anyway, would the cautious use of a couple of architecture specific CFLAGS be a safe thing to do? Getting that bit of extra performance on an ageing laptop would be super.

---

### Post by dino99 on 2010-06-18
about thinkpad:

with synaptic, install: tp-smapi-dkms, thinkfan, acpitool

into synaptic repo, add these ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

then update

---

### Post by goseph on 2010-06-18
ah!

Thanks for the reply - how will more up to date beta software help me out with the thinkpad? Are there important Radeon enhancements in the 2.6.32 and X.org pipeline that I was unaware of?

---

### Post by goseph on 2010-06-27
I have done what you suggested but it does not appear to have made any difference :(

---

