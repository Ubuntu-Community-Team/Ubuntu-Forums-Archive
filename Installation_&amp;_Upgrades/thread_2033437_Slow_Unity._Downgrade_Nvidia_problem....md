---
title: "Slow Unity. Downgrade Nvidia problem..."
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by wxnker on 2012-07-26
Hi, I've seen a number of results on Google, but I can't make the suggested solution work. I'm sorry if this was already posted. I've seen a couple of threads on this forum, but I didn't find a solution. 

I would like to downgrade nvidia-current to v 295.33 to improve responsiveness in 12.04 Unity. I've recently upgraded to 302.17. It helped, but Unity is still kinda sluggish.

My Nvidia card: GeForce GT 240M.
Ubuntu: 12.04 32bit.

So I found this solution:
[http://askubuntu.com/questions/125608/unity-3d-no-longer-works-after-installing-12-04](http://askubuntu.com/questions/125608/unity-3d-no-longer-works-after-installing-12-04)

CTRL+ALT+F1
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

I've added the ppa as shown in the first command, but when running apt-get install I get an error similar to this:
> nvidia-current=295.33-0ubuntu1~precise~xup1 for nvidia-current was not found.

- How to solve this?
- Is this solution even known to work?
- Other suggestions?

Thanks in advance.

---

