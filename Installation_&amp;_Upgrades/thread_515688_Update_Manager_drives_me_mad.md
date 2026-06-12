---
title: "Update Manager drives me mad"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by dkaddict on 2007-08-02
I have had a look through this forum and done a few Googles on the following yet have become none the wiser as a result of my searches. If I have missed anything glaringly obvious or any relevant posts, please forgive me and try to point me in the right direction if you can. I will be grateful.

Ok. I am running Feisty/Gnome. It is a red hot OS in almost all departments and I love using Ubuntu: so much so that I very rarely boot into anything else. I have, however, got a problem with 'Update Manager'. Basically, it pesters me every time I log in to Ubuntu. The cause of its persistent nagging is because it wants to upgrade a package called 'libfaad2-0' but is not allowed to. I have tried to tick the box which it corresponds to in Update Manager, remove/upgrade it in Synaptic, and remove/upgrade it on the command line with 'apt' and 'aptitude'. Nothing works, alas, and the pestering continues. I am hazarding a guess at it being some sort of dependency problem yet am nowhere near 'ghuru' enough to sort it out. 

Also, when I use 'apt' or 'aptitude' I am always being told to remove hundreds of apps, which  include a large of amount of the applications I use almost daily, by way of using the 'autoremove' option for 'apt' or 'aptitude' in BASH. The behaviour with regards to 'autoremove' resembles that described here>>

[http://ubuntuforums.org/showthread.php?t=506789&highlight=libfaad2-0](http://ubuntuforums.org/showthread.php?t=506789&highlight=libfaad2-0)

... yet I am too much of an ex-WIN (20yrs-aaaaaaaagggggggghhhhhhhhhhh) point and click merchant to see where the content of this thread applies to my 'libfaad2-0', 'autoremove' dilemma.

Again, please and big thanx for any help. I will check back here a few times each day. Let me know of any output I can obtain with BASH and I will post it ASAP.

peace

dk

---

### Post by 505 on 2007-08-02
Well, you could lock the package, so it will never try to upgrade it again. Open Synaptic, search for the package, and from the Package menu choose Lock version.

(Although it would be a better solution to resolve the actual conflict...)

---

### Post by Seisen on 2007-08-02
libfaad2-0 is in the multiverse repository did you happen to install it then remove the multiverse repository?

---

### Post by dkaddict on 2007-08-03
Thanx for replies. I am not sure about the repositories but will go and check. I will bar the package as explained in the first reply if needs be.

Cheers again. I will post results in a bit!

dk

---

