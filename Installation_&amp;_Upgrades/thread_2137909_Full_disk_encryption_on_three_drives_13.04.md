---
title: "Full disk encryption on three drives 13.04"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by benj23673 on 2013-04-22
I have right now followed this guide [http://ubuntuforums.org/showthread.php?t=1782296](http://ubuntuforums.org/showthread.php?t=1782296) and have my three hard drives in one lvm then split into home, root, and swap groups like in the tutorial from above. I am trying to use the full disk encryption option on the graphical install of 13.04 but when ever it try's to boot into the cd I get to pick my language and it just hangs there after clicking continue.  I know I can use luks to encrypt then decrypt and install on that which might have to be an option I was just wondering if anyone had any advice on a best possible solution to encrypting the hard drisks on a ubuntu install? Using 12.10 is also not an option since it does not play nice with my video card.

---

### Post by Cheesemill on 2013-04-22
There's a known bug in the 13.04 installer that causes the hang.

Try running the 'Try Ubuntu' option, then mounting your partitions by clicking on them in the file manager, and then running the installer. This has always worked for me.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

---

### Post by benj23673 on 2013-04-22
Thank you, I could not find anything last night when I was looking online.

---

