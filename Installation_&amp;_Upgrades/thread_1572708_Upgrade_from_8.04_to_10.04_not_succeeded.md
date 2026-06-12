---
title: "Upgrade from 8.04 to 10.04 not succeeded"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by noorman on 2010-09-11
After the upgrade on this AMD Athlon Barton 2500+ system, root device not found.
The Grub install had failed; the new grub.cfg file was non-existent. In the Grub folder there was only a env file !
Succeeded in installing Grub2, but without the cfg file it didn't help any, of course.
Very disappointed that the new Grub install didn't succeed and that there is no 'repair' for such an event on the Live CD of 10.04.1 ... :(

Had done a few upgrades, from 7.04 to 7.10 and to 8.04 without problems.
Very surprised and shocked that an upgrade from one LTS to the following LTS does not work 'out of the box' ](*,)

Did a fresh install in the end :shock:

.

---

### Post by kostkon on 2010-09-11
Mine was successful. But I don't think that the 8.04 &#8594; 10.04 upgrade installs Grub2, it keeps the old Grub. At least, in my case, that's what happened.

---

### Post by noorman on 2010-09-12
.

It was my deduction of the fact that I found the path, listed in the Grub2 pages (this forum), which made me conclude that it had been installed; it only lacked the very important grub.cfg file ...

Anyway, the upgraded system couldn't find the system root and thus would not start up.
I consulted my brother-in-law (Unix pro) who told me not to spend too much time trying to fix this and back up the Home folder, then install afresh / I did and that worked.
Now though, I 've only lost my wife's address-book (Thunderbird) ](*,)

.

---

