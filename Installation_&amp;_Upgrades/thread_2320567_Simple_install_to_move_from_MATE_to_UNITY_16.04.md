---
title: "Simple install to move from MATE to UNITY 16.04?"
date: 2016-04-15
forum: Installation &amp; Upgrades
---

### Post by Jeff_Grant on 2016-04-15
Hi - I'm relatively new to Ubuntu though by no means new to Linux, having worked exclusively in it for seven years now. I've been using Ubuntu MATE for some weeks. I like it, but having checked out a pre-release ISO of 16.04 I'd like to move to that when the final release comes out in  few days' time. What I want to do - and I've done before with another distro - is just to install the OS on the existing /  partition, leaving my other partitions, including my /home partition, unformatted and untouched. I'm not sufficiently familiar yet with the Ubuntu installer to attempt this without some assistance. Can anyone here help?

---

### Post by kc1di on 2016-04-15
Hi Jeff_Grant  and welcome to Ubuntu,

It depends on how you installed mate, did you use a separate Partition for your /home?
if so it's a simple matter of selecting other at the partitioning page when it come up and telling it to only format your / Partion and not the /home one.
you will have to use the same usr name that you used before. 

if you did not do a separate /home partition it's a bit more complicated. 

In any event let us know - and there are ways to do it.

---

### Post by Bucky Ball on 2016-04-15
As above. Choose 'Something Else' at the partitioning section. If you have a separate /home choose the Change> 'use partition' option but do NOT tick the 'Format' box in the Format column in the main window. ;)

And also as above, if you do not have a separate /home (or your data backed up on another partition/drive) then you will need to backup anything on / before you install then put it back where it was previously.

---

### Post by Jeff_Grant on 2016-04-15
Thank you guys, that's what I was looking for - especially the 'use partition' option. I wasn't sure if that should be used or the 'do not use' option. And yes, when I installed MATE I created a separate /home partition. Thanks once again for a very quick solution!

---

