---
title: "can't revert back to unity 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by dancelikeaindian on 2011-04-29
i feel really stupid for "upgrading" to gnome 3 to try it out and read warnings saying it can mess up your system. i went on thinking oh it'll be fine and the update process messed up or something. now i have a barely functional desktop and just want to go back to unity 11.04. i added the ppa from [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3). i hope someone can help aid me to downgrade, will be much appreciated! :D

---

### Post by Interista on 2011-04-29
[COLOR=navy]Why is Gnome 3 that bad ?[/COLOR]

---

### Post by dancelikeaindian on 2011-04-29
no, it messed up and its showing icons all blurry and i just rather have unity back for now.

---

### Post by dancelikeaindian on 2011-04-29
> I just experienced the same thing. When I tried to submit crash reports it told me that it wasn't an official gnome version. I could not log into classic or Unity.

I installed ppa-purge and removed the ppa package that I used to get gnome 3. PPA-purge removed the repository and automatically did an apt-get update and told me it wanted to remove many packages and downgrade several others. After clearly laying out what it wanted to do, it asked me if I wanted to accept this solution. 

I said "yes". 

After it did it's thing I rebooted back into Unity and everything works as before 

I hope this works for others as well.
solved the problem from here.
[http://ubuntuforums.org/showthread.php?t=1726755&page=2](http://ubuntuforums.org/showthread.php?t=1726755&page=2)

---

