---
title: "Is there anyway to convert from 32 bit Ubuntu install to 64 bit?"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by kevdog on 2016-10-28
I have a server on 32 bit Ubuntu but would like to upgrade to 64 bit.  Most of the things I've read suggest I do this by just starting over or reinstalling the OS. This might be the easiest way.  I remember however I once had a 32 bit Arch install and was able to convert to a 64 bit install via these instructions [https://wiki.archlinux.org/index.php/Migrating_between_architectures](https://wiki.archlinux.org/index.php/Migrating_between_architectures).  I was wondering if there was a similar process.

---

### Post by PaulW2U on 2016-10-28
Well there's this - [Migrate/Upgrade Ubuntu 14.04 LTS (Trusty Tahr) GNU/Linux from 32 bit to 64 bit HowTo]("http://www.ewan.cc/?q=node/132") - not something I'd attempt though.

---

### Post by mörgæs on 2016-10-29
Why do you want to convert? Performance problems?

---

### Post by kevdog on 2016-10-29
Conversion for a few reasons.  32 bit not likely to be supported in future.  The hotpatching kernel mechanism canonical released this week is only compatible with 64 bit installation.

---

### Post by kevdog on 2016-10-29
It took me nearly all day to follow the instructions here: [http://www.ewan.cc/?q=node/132](http://www.ewan.cc/?q=node/132) but I can confirm I successfully was able to update the 32-bit 16.04 32-bit install to the 64-bit install.  I had to modify some of the instructions to account for xenial (16.04), and some of the lines didn't work all the time but were easily fixed with apt-get -f install.  All in all, I could have never have made the jump without these instructions.  I'm only posting this here in case someone doubts whether the instructions are still applicable to 16.04 since the instructions reference 14.04.  I can confirm they are. 

Thanks for the link.

---

### Post by mörgæs on 2016-10-31
Good, please mark the thread 'solved'.

Just so people don't get the wrong impression from reading the thread: There are speculations that 32 bit will drift out of support some day but no decision has been made. At least we will have the 18.04 LTS with support through the year 2023.

---

