---
title: "Problem installing 11.04"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by leo_s84 on 2011-06-28
Hi!

I've been an Ubuntu user/enthusiast for the past 6 years and have never been in a problem like I am now. 

I tried installing 11.04 on my new alienware m17x system and I can't get it to run. Tried wubi at first and the screen flickered before even starting to install (All bunch of colors on the screen) so I tried the alternate install instead. 

After the successful install (alternate), the flickering would come back when trying to boot into the system. I tried a whole bunch of grub commands i found on the internet to force a vesa driver which didn't work. I also tried to install the 32bit version of the system to no avail.

My specs are:

core i7 2630qm

amd radeon 6970m (The probable culprit)


I really have no idea what to do next, so any comments are welcome. Thanks!

---

### Post by lightstream on 2011-06-28
what happens when the screen flickers? does the system hang? if so, how long have you left it? Sometimes you can get weird graphics artifacts on boot up as the system switches video modes.

---

### Post by leo_s84 on 2011-06-28
Nothing happens after a while. And by screen flickering i mean the whole screen covered with colors, no menu or anything. I sometimes also get a complete blank screen that i left on for a couple of minutes to see if anything happened but nothing.

Any ideas?

---

### Post by Rubi1200 on 2011-06-28
Hi and welcome to the forums leo_s84 :)

Take a look at the options in this link for setting boot options:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

I would start by trying nomodeset.

---

### Post by leo_s84 on 2011-06-28
Thanks for that Rubi1200. The nomodeset did the trick to at least get into ubuntu.

My new problem comes now because no matter what ati driver i install(Proprietary or open source), the desktop doesn't come on and the flickering comes back. The only way to get in ubuntu is to add the nomodeset permamently to the grub conf but obviously it looks like hell and can't change the resolution plus no 3D.

Do i have to wait for another ati driver update or ubuntu release?

---

