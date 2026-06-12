---
title: "Stuck on &quot;Checking battery state&quot; after installing nvidia driver 10.10"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Dlx738 on 2011-04-21
Hi I just installed ubuntu on my m11x and am completely new to ubuntu. After installing the latest driver for the 335m I am stuck at checking battery state and there is no way I can get to the gui anymore. The only access I have to are the tty's and I don't know what to do. I have already tried finding a solution for a couple of hours, but cannot find any. Please help me solve this problem, I do not want to reinstall again. 
Thanks

---

### Post by dino99 on 2011-04-21
from a terminal:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

[http://ubuntuforums.org/showthread.php?t=1396552](http://ubuntuforums.org/showthread.php?t=1396552)
[http://en.community.dell.com/owners-club/alienware/f/3746.aspx](http://en.community.dell.com/owners-club/alienware/f/3746.aspx)

---

### Post by Dlx738 on 2011-04-21
Thanks for your reply but the thing is I do not have an Internet connection so I can't run those commands. Is there any other way? Thanks

---

