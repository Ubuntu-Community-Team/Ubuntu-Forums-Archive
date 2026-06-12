---
title: "Glipper problem"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by McTek on 2008-04-27
Up grade trashed glipper, re-installed from synaptic but glipper will not load, ideas anyone?

---

### Post by Bronto on 2008-04-27
[http://ubuntuforums.org/showthread.php?t=767640&highlight=glipper](http://ubuntuforums.org/showthread.php?t=767640&highlight=glipper)

---

### Post by crazy ivan on 2008-04-27
Yeah.. But my glipper also won't work. If I add it to panel it hangs. If I run '/usr/lib/glipper/glipper' it hangs. 
With gutsy there was aswell a link in some executive path aswell as full funtionality. Now with hardy I have to switch to klipper, which sometimes won't fit in the panel. See thread: [http://ubuntuforums.org/showthread.php?p=4811883#post4811883](http://ubuntuforums.org/showthread.php?p=4811883#post4811883)
Too bad parcellite or DDM are not yet in the repositories. I use the second one for screenshots and can quite recomend it.

---

### Post by crazy ivan on 2008-04-27
Update: if add it to panel upon restart it is there, but when I click on it, thers only a white line left! very strange

---

### Post by zeronothing on 2008-04-27
hey guys I was having the same problem. I noticed that the newest version for some reason doesn't install into the /usr/bin area. it will install in /usr/lib/glipper directory. This is in my case I dont know about anybody else. So I tried to build a new package, and it built but with the same problem. anyways I have built a package again using an older version and it works. I did just build this package only for x86 and not x86_64. I hope this can help some people out. also you may have to lock the glipper package version with synaptic so it doesn't try and install the one from the repository.

---

### Post by crazy ivan on 2008-05-02
Nice workaround zeronothing :) 
But I "solved" the problem for me in another way: 

Funnily the glipper works exaktly then, when klipper wont load - so I always have ONE tool to do the job. Guess its some DCOP difficulties for both of them.. On these rare occasions glipper asks me "glipper has been shut down, do you want to resart it". And then it works...

---

