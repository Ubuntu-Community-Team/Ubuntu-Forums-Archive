---
title: "help installing the vodafone connect driver for linux"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by msv240586 on 2008-04-01
Good day everyone

I'm a slight newbie to linux and seem to be having slight trouble, i'm running ubuntu 7.10 on a dell latitide d630 laptop
I want to install the vodafone connect card driver for linux, which has 4 dependencies which are, python-twisted, python-serial, python-central and python-crypto. I have managed to successfully install python-serial and python-central

my trouble starts with the other two

python-crypto requires python-twisted-conch which requires python-twisted-core which requires pythone-zopeinterface which requires python which is already installed on my pc and is the later version than what is avaliable on the net, so i'm stuck there

the other trouble is with python-notify which requires libc6 which conflicts with the installed package tzdata. i'm also clueless on how to solve this one

not entirely sure if this is the right section to post this question

any help would be gratefully appreciated in helping me install the vodafone driver.

thanks

---

### Post by HoTseChu on 2008-04-01
I've installed it with the .deb from

[https://forge.vodafonebetavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb](https://forge.vodafonebetavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb)

and is working fine. The package installer resolved the dependencies without any problem (in Ubuntu 7.10).

---

### Post by atasaRossios on 2008-04-26
Hi I installed the same package "vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb" but had no luck at all.
I also upgrade to Hardy and installed the same package and it is not working again.
There is some difference.
In Gutsy the device was recognized as a cd-rom this is not happening with Hardy.
What did you do different?
Did you install any extra package?

---

