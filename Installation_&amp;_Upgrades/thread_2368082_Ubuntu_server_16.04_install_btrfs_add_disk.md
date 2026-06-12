---
title: "Ubuntu server 16.04 install btrfs add disk"
date: 2017-08-06
forum: Installation &amp; Upgrades
---

### Post by josh60 on 2017-08-06
&#8203;[https://www.youtube.com/watch?v=a04jsmufQFY](https://www.youtube.com/watch?v=a04jsmufQFY)
 
[FONT=verdana]So I mostly followed this install but I did raid 1 instead. I'm beginning to think this isn't right tho. I'm trying to add another disk to this setup but I keep getting.[/FONT]
[FONT=verdana]/dev/sdb1 not large enough to join array btrfs[/FONT]
[FONT=verdana]Correct me if I'm wrong but this way looks like it's using mdadm with btrfs on top. Isn't the point of btrfs to not have to use another raid it's supposed to be it's own raid right? Also I was reading about not even having to making partitions with btrfs.[/FONT]
[FONT=verdana]My main question is is this installation correct? and how would I add an extra disk to this or delete the mdadm raid and get it to work with just the btrfs?[/FONT]

---

