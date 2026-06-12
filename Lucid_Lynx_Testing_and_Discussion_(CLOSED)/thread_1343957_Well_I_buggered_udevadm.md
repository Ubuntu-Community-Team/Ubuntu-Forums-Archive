---
title: "Well I buggered udevadm"
date: 2009-12-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-02
On my main (StonedLizard) OS, after update, I get udevadm not configured and eventually I get a initramfs prompt that i do not know what to do with except "reboot"

Looking for this problem I found a bug for 9.04 that at least one person had with 9.10 with the same song and dance.

The solution described was to run;
```

sudo dpkg-reconfigure udev

```
and;
```

sudo update-initramfs -u -k 2.6.32-6-generic

```
I chrooted in and ran these (minus "sudo") and it still is a problem.

I hope that someone has a suggestion as I am out of ideas.

---

### Post by ranch hand on 2009-12-07
This has been a problem through 2 kernel updates on this 9.04>9.10>10.04 upgrade and for one kernel on my clean install.

I did not like the looks of the remove list on todays updates so I just selected everything related to mesa and the new kernel and left the others back on the 2 troubled OS'.

They both boot great now from the normal generated entry, and better yet, the symbolic entry.

Edit

all signs of flickering while booting have gone from Lounge Lizard.

---

