---
title: "Mac Pro Dual Boot w/rEFit Help"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by shaninho on 2006-11-03
Hello, I am trying to dual boot my Mac Pro into Mac OS X and Ubuntu but am currently experiencing some small problems. 

Aside from using Ubuntu's most recent release 6.10, I followed instructions from several sites including: 

[http://bin-false.org/?p=17](http://bin-false.org/?p=17)

with a few minor tweaks that may not be so minor? 

a few of the things this guide asks to install are not available in the current source lists, so I used whatever recommendations apt-get had for me.

THese included linux-restricted-modules-2.6.15-23-686, which I replaced with linux-restricted-modules-generic because apt-get couldn't install that or a more current specific version number.

Also I suppose it's worth noting that linux-kernel-headers actually just installed linux-libc-dev.

Now when I run rEFit as my bootstrap loader, it sees both the Mac OS X and the Linux "drives" separately, but when I choose Linux it goes to a black screen and then has a blinking cursor (that I think is taunting me). 

I am stuck, and I feel like I'm bricked out of my system. Any suggestions are greatly appreciated, and certainly I can provide more details if necessary.

Just to clarify, I have read every resource online that I can find on this topic, including the discussions on this site and others, all of which have been very helpful. 

Thanks in advance.

---

