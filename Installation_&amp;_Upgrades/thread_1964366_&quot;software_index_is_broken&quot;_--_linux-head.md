---
title: "&quot;software index is broken&quot; -- linux-headers-generic"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by Luke3535 on 2012-04-23
I have 10.04 installed on a Dell Mini 9. I've been using it for about a year, but I'm still just a half step about complete noob.

Opera stopped playing youtube videos and it said it was missing a plug-in. It couldn't install it automatically and the instructions for manual installation of a deb or tar packagae scared me, so I tried Firefox. It said it needed Flash, and it tried to install it automatically, but then gave the error:

"software index is broken"  

I Googled the problem and tried:

>sudo dpkg --configure -a

and

>sudo apt-get update

and 

>sudo apt-get upgrade

but none helped. 

I opened Synaptic Package Manager and it said that linux-headers-generic is broken. I marked it for Upgrade and it did a lot of stuff, but wasn't successful in fixing the broken package. I didn't write down the long error message.

When I exited and reopened Synaptic, a new option was available for linux-headers-generic: "Mark for reinstallation". I tried that, it downloaded stuff and then gave this error:

E:/var/cache/apt/archives/linux-headers-2.6.32-41_2.6.32-41.88_all.deb: unable to create '/usr/src/oinux-headers-2.6.32-41/arch/ia64/Makefile.dpkg-new' (while processing './usr/src/linux-headers-2.6.32-41/arch/ia64/Makefile') and etc.

Help?

Thanks!


Luke

---

### Post by Luke3535 on 2012-04-24
Please?

---

