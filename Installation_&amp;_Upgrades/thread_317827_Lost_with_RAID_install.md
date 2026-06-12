---
title: "Lost with RAID install"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by joshcrosshairs on 2006-12-13
i have a complicated system and would love to make the conversion from XP to Ubuntu.  the problem is I have a SATA raid 0, and it seems to be the most difficult install.  i am just starting with no linux experience and have almost lost hope on getting this done.  is there any good guides that can help someone in my position?  i have tried many and there just isn't enough detail to get me through.  to be honest i thought it would be a little easier than this.  i haven't quite figured out why dmraid isn't included on the alternate install disk if it is needed in order for raid drives to be seen properly. or if they are why isn't it streamlined so you don't need to manually install it.  on top of all of this i can't use the live cd because of video driver issues.  can someone help me make this happen or do i have to switch to a different release?  is there a linux release that can install "out of the box" to SATA raid drives?  this is my last resort.  the one who helps will be a hero in my book!  thanks.

-josh

System:
Abit NF7-S Nforce2 chipset motherboard
AMD Athalon XP 3200+
1 GB Kingston HyperX
ATI 9600XT AGP 8X
2 WD Raptors in RAID 0
600W PSU

---

### Post by psusi on 2006-12-13
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for info on your fake raid controller.

---

### Post by joshcrosshairs on 2006-12-13
i have read most of it and it doesnt say what version those instructions work for.  is it written for 6.10?  there are still some questions i have about that howto.  it doesn't say how you get to the part where you actually install dmraid.  it also says:

"Create the partitions (the actual commands will vary depending on your choice of tool(s)):"

i'm not sure which "tool(s)" he is useing for this step in order to duplicate his success.  Otherwise that guide would be the perfect one for me since he has close to the same hardware setup that i do.  thanks again for the answers that come.

-josh

---

### Post by joshcrosshairs on 2006-12-13
am i without hope?  if so can someone point me to a linux release that supports raid on the install disk?

---

### Post by onlyoneskwalla on 2006-12-14
Fedora Core 6(possibly also 5 I think) support dmraid out of the box, in the installer.  Haven't tested the livecd just the install dvd.  Since dmraid is produced by redhat/fedora this shouldn't be too big of a suprise.

---

