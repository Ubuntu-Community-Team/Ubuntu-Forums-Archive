---
title: "Kernel Panic not syncing: Attempted to kill init! (upgrade from 5.04 to 6.10)"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by aalr1986 on 2007-02-12
I'm using Hoary (v5.04), so well here's my problem in details:

I put the 6.10 cd, which I had burned 5 minutes before that.
I restart.
It automatically boots from the CD, and gives me a menu.
I choose the first option: Install or Run Ubuntu
I get a black screen with a lot of stuff, and in the botom, the last msg is:

[  20.828484]  <0>Kernel Panic - not syncing: Attempted to kill init!

ps: I get the same error msg choosing the second option, which is Install in safe graphics mode.


I've searched in a lot of forums, for hours, for the last two days, and I can't really find an answer for this.
Any help is useful.
Thanks a lot!

---

### Post by aalr1986 on 2007-02-13
any ideas....?

---

### Post by aalr1986 on 2007-02-13
...

---

### Post by w3ath3rman on 2007-02-25
I found this [link]("https://answers.launchpad.net/ubuntu/+ticket/3694") that states you should set acpi=force.  I press F6 after booting with the CD-ROM and added it to the end of the boot params.  I have not been able to get it to work.  But, many others are having success with it.  If this works for you please tell me how you did it.

---

### Post by w3ath3rman on 2007-02-25
Sorry, that was the wrong link.  Try [http://www.linuxforums.org/forum/debian-linux-help/44858-ubuntu-install-problems.html](http://www.linuxforums.org/forum/debian-linux-help/44858-ubuntu-install-problems.html)

---

