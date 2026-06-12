---
title: "Software Raid in Feisty"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by linuxer_de on 2007-03-22
Hi,

I'm using LVM on top of a Software-Raid built by mdadm which works just fine 
with edgy.

Now I tried to install the latest daily built of Feisty and I run into a problem.
When starting up the partitioner (alternate install cd) Feisty tries to initialize
the Software-Raid devices under /dev/md/X but they are listed under
/dev/mdX. This problems exists since Herd1 and isn't fixed yet, or am I the only
one having it?

I fixed this by creating a sym-link in the console and then Feisty installed and worked without any problems. 
After 2 days of usage, Feisty doesn't boot anymore, it says:

mdadm: no devices listed in conf were found... dropping to a shell

any solutions or hints?

---

