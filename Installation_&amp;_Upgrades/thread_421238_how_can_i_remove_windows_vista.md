---
title: "how can i remove windows vista"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by thomasbaker on 2007-04-24
I have ubuntu linux for about a year now, im am not an expert at all.  I have recently install ubuntu 6.10 to my notebook (dell b130) and i have everything running.  And now that I have my gps working with roadnav I have no use form my windows vista partion. I would like to remove vista and keep 100% ubuntu.  Iknow i can reinstall edgy and use the entire disk, but I don't want to reinstall all the wireless, screen resolution, and gps, crossover office, you get the picture. can anyone offer any solid suggestions?

thanks

thomas

---

### Post by bwhite82 on 2007-04-24
Just delete the partition in gparted. I would leave it that way so you can mess around with other distros at your leisure and if you don't like them, simply delete the parition again.

---

### Post by thomasbaker on 2007-04-24
i thought about that, if i delete it, can i resize, or merge it into my ubuntu drive?

---

### Post by bcmiller on 2007-04-24
If you don't already have a separate /home partition you can format the former Vista partition and then move your /home to that partition. 

Linux isn't as tied to what drive things are on.  You can have almost any of your folders anywhere as long as linux has that drive mounted and knows what you are using it for.

I don't think you can "merge" it but again like I said above there is no need.  If you wanted to make your install drive larger you would have to reformat the whole drive and that won't work unless you have that drive backed up.

---

