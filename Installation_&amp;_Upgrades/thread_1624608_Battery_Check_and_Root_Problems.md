---
title: "Battery Check and Root Problems"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Jessi on 2010-11-17
My friend is having trouble installing Ubuntu on his Asus laptop. He says that when he boots it takes him to a root menu then fails a battery check:

> 
23:37:23] Brandawg joins conversation
[23:37:27] Jessi Ray says:
What's shakin?
[23:37:34] Brandawg says:
it won't move beyond 'battery check'
[23:37:44] Jessi Ray says:
D**n. You have horrible luck with this.
[23:37:47] Brandawg says:
lol
[23:37:50] Brandawg says:
ftw
[23:38:00] Brandawg says:
i probably bring these things on myself
[23:38:28] Jessi Ray says:
I've installed Ubuntu on 3 different machines
[23:38:34] Brandawg says:
well i'm looking at this
[23:38:37] Brandawg says:
the hdd is partitioned
[23:38:43] Brandawg says:
it just won't finish the install
[23:38:48] Brandawg says:
it stops at 'battery check'
[23:38:50] Brandawg says:
and won't do anything
[23:40:03] Jessi Ray says:
try a failsafe boot, if that's an option in the grub
[23:40:28] Brandawg says:
it is
[23:41:32] Brandawg says:
should I start in recovery mode
[23:41:42] Jessi Ray says:
try it, see what is avaliable
[23:41:45] Jessi Ray says:
meet me on facebook
[23:41:47] Brandawg says:
okay
[23:42:02] Brandawg leaves conversation
[23:45:21] Brandawg joins conversation
[23:45:21] Brandawg says:
okay
[23:45:24] Brandawg says:
when I start in recovery
[23:45:27] Brandawg says:
it passes that battery check
[23:45:33] Brandawg says:
then it goes stright to root menu
[23:45:38] Brandawg says:
and it asks me for my comp name and password
[23:45:48] Brandawg says:
after I put that in it says 'welcome to ubuntu' but stays in the root menu
[23:45:51] Brandawg says:
and tells me I can use sudo
[23:45:54] Brandawg says:
and I don't know what to do
[23:46:05] Jessi Ray says:
Recovery must be the terminal
[23:46:09] Brandawg says:
it did this before tho
[23:46:09] Jessi Ray says:
if I'm correct
[23:46:13] Brandawg says:
it did this when I went regular
[23:46:27] Brandawg says:
it does this instead of going to the regular login
[23:46:29] Brandawg says:
it starts up in root
23:46:13] Brandawg says:
it did this when I went regular
[23:46:27] Brandawg says:
it does this instead of going to the regular login
[23:46:29] Brandawg says:
it starts up in root
[23:46:44] Jessi Ray says:
let me take this to the ubuntu help forum
[23:46:49] Brandawg says:
hmm
[23:46:53] Brandawg says:
it shouldn't be this complicated
[23:46:58] Jessi Ray says:
it shouldn't
[23:47:16] Jessi Ray says:
I have installed it on 3 different machines and 4 different times
[23:47:21] Brandawg says:
yeah
[23:47:22] Jessi Ray says:
never had a problem
[23:47:26] Brandawg says:
yeah
[23:47:32] Brandawg says:
should I reinstall it?
[23:47:39] Brandawg says:
would that delete the partition and start over?
[23:47:52] Jessi Ray says:
no, hold up
Any help on the issue before the poor boy looses hope?

---

### Post by sikander3786 on 2010-11-19
Once he gets to the terminal, what is the output of

```
sudo service gdm restart
```

or

```
sudo service gdm start
```

In fact, it would be better if your friend answers these directly.

We also need some more hardware info, graphics card etc.

And which version of Ubuntu is this?

---

### Post by Jessi on 2010-11-19
He's trying to get 10.10 to work.

We got it to install now, but it wants to boot in command line. He can get it to boot in graphic's safe recovery mode, but regular Ubuntu boots in command line.

---

### Post by sikander3786 on 2010-11-20
Which graphics card is it? Are the proprietary drivers installed?

Can he boot into safe graphics and try to install or remove the drivers from System > Administration > Additional Drivers.

---

