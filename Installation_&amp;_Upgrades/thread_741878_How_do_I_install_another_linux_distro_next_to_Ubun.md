---
title: "How do I install another linux distro next to Ubuntu?"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by spinoza666 on 2008-04-01
I'm very happy with Ubuntu, but after changing to Linux I've started to suffer from a compulsive disorder.... I keep finding new and exciting distributions that I want to try out, and end up formatting and reinstalling Ubuntu over and over:)

I'm looking for a quick an easy way to keep Ubuntu, but be able to have a second distro next to it. And be able to change this frequently as I try new ones out.

I guessing I need to make a partition for the other distro, and the install the second distro to it? How do I go about doing this?

My apologies if this has already been answered. I did find some posts that have some relevance, but nothing that gives me a complete how-to. Any help would be much appreciated.

Cheers:)

spinoza

---

### Post by thrice upon a time on 2008-04-01
Welcome to the phenomena known as "distro-hopping" :lol:

You've already answered your own question ;-) You simply make room with a spare partition (no need for another swap), and install away. Make sure to put a pointer to it in GRUB, or you can use the other distro's grub, and put a pointer to Ubuntu in it if it isn't automatically detected.

That's about it, unless you have a seperate /home, in which case it is only slightly more complicated.

---

### Post by spinoza666 on 2008-04-01
My illness has a name? Distro hopping syndrome? Thank heavens I felt so alone:) I was wondering if I was going bonkers when I sat up until 4 in the morning fighting the urge to install Scientific Linux by CERN and Fermi Lab...... Like really, what on earth on earth would I, a biology student, need that for!? But it's like you just gotta have it......

:lolflag:

Anyways, thanks for your reply, since I'm a newbie I have a couple of questions so hopefully you'll indulge me a little bit longer.

I'm unsure if I have a seperate /home, all I did was install by the default method, ie. I did not manually partiton but used the the guided entire disk thing?

And how do I go about making room for another partition? I read something about gparted, but unsure if this is what you mean? Do I just use gparted to partition off a bit of whatever of my existing partitions is the largest? And how much space do you recommend I use?

And finally, what is GRUB, and how do I put a pointer to the other distro in it? Would this allow me to access the other distro from the ubuntu desktop, the login or when booting?

Thanx heaps :)

spinoza

---

### Post by housam on 2008-04-01
Try [[COLOR="Red"]_this guide _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817")by **Bodhi.zazen**

---

### Post by spinoza666 on 2008-04-01
Thank you both very much:)

This does look like quite a difficult task though, but hopefully Ill make it in the end...

---

### Post by stalkier on 2008-04-01
> **spinoza666 said:**
> Thank you both very much:)

This does look like quite a difficult task though, but hopefully Ill make it in the end...

Well is you screw it up you can always just start over. Believe me even people that have been around have messed it up a time or two. :D

---

