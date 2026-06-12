---
title: "Argh! Can't instal retircted extras"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by Phadros on 2008-04-14
Hi,
I'm a noob but, loving Ubuntu.
I have installed Ubuntu on my desktop and when I did I used the following line to instal restricted drivers and it worked great:

*sudo apt-get install ubuntu-restricted-extras*

Now I am installing it on my lap top and and I get the following message:

[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras[/I]

Is there another way I can install it like from the internet.

Thanks!

---

### Post by kostkon on 2008-04-14
Go to *System -> Administration -> Software Sources* and check at the first tab if all of the repositories are checked (i.e. enabled). In this case, you need the *Multiverse* repository to be enabled to install the *ubuntu-restricted-extras* package.

---

### Post by Phadros on 2008-04-14
Thanks kostkon!!!!! :) Worked GREAT!
Cheers!

---

