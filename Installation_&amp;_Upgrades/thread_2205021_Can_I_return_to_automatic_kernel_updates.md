---
title: "Can I return to automatic kernel updates?"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by ACGilbert on 2014-02-11
I recently noticed that the current kernel is 3.11.
Checking my system I find that I'm still on kernel 3.2 which I apparently 'manually installed' at some point.
I have been running Ubuntu 12.04 LTS since it's release.
Synaptic  says I'm up to date. Looking at Synaptic 'not installed' I see I have 100's of later image and kernel files which downloaded, but never installed.
How do I get my system to 12.04.4 where I'd like it to be and return to automatic kernel updates?
Thanks in advance,
AC

---

### Post by kostkon on 2014-02-11
Original 12.04 systems don't get updated to the latest 12.04.4 (saucy) stack, but you can do it manually, instructions are [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

---

### Post by ACGilbert on 2014-02-12
kostkon,
Thanks for the reply. I read through the instructions and went with the following:

sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy

Rebooted and I am now on kernel 3.11.0-15-generic. So all is well!
There is still much cruft in synaptic relating to all the kernels, images, headers, extras, tools, etc. that downloaded, but never installed over several months. I'll just remove that stuff manually. Now I need to figure out how to mark this as solved.
Thanks,
AC

---

### Post by Bucky Ball on 2014-02-12
These three commands in a terminal:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

... hitting 'enter' after each. This will not upgrade the release but everything in the current one that needs it. Report any errors.

Incidentally, there is talk that there will be, for the first time, a .5 release of 12.04 which will include the Saucy stack. Rumour has it that will be be post-Trusty release.

Here's another version of the gossip. I read mine on a Launchpad group somewhere, which was different to this:

[http://news.softpedia.com/news/Ubuntu-12-04-5-with-the-Linux-Kernel-from-Ubuntu-14-04-Might-Arrive-in-September-425723.shtml](http://news.softpedia.com/news/Ubuntu-12-04-5-with-the-Linux-Kernel-from-Ubuntu-14-04-Might-Arrive-in-September-425723.shtml)

---

### Post by ACGilbert on 2014-02-14
Thanks Bucky Ball,
I got the 3.11 kernel I wanted and am happy with 12.04.
Previously I installed every version since 5.04 I think.
13 is the first version I skipped and I think I might skip 14 as well and go with 12.04.5.
AC

---

