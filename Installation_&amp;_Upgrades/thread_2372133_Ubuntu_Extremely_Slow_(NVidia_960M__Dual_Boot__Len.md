---
title: "Ubuntu Extremely Slow (NVidia 960M / Dual Boot / Lenovo 50-70)"
date: 2017-09-21
forum: Installation &amp; Upgrades
---

### Post by helloworld-21 on 2017-09-21
So I've dual booted windows 10 and Ubuntu 17.xx on my Lenovo y50-70 with a NVidia 860M (OR 960M) graphics card. The only way the install would work, was with the "nomodeset" flag on. It seems buggy because my screen freezes every time the install finishes and I click restart. I then had to do force a shutdown. (I've installed it like 5 times)


Anyways Ubuntu is unusably slow. I can see every frame transition and it takes many seconds for a change on the screen to appear. 
So I've dual booted windows 10 and Ubuntu 17.xx on my Lenovo y50-70 with a NVidia 860M graphics card. The only way the install would work, was with the "nomodeset" flag on. It seems buggy because my screen freezes every time the install finishes and I click restart. I then had to do force a shutdown. (I've installed it like 5 times)



I don't know much about ppas and repos, so this next bit of info might sound off. I've tried installing graphics drivers straight from an Nvidia ppa, generic x-org drivers, and the NVidia-current-update method. All of them on restart either brought me to a purple screen or an endless login loop.


Idk what to do. I don't need to use my NVidia graphics card for Ubuntu, just the intel chip, if that's possible. I can only boot into Linux when I have nomodeset turned on


Also, at times it not slow at all, though it seems rare. (like when I go from windows to Ubuntu). 


What is wrong?

---

### Post by mc4man on 2017-09-21
I had a skylake with 860m last year & never had any issue installing 16.04. Have you tried using the latest 16.04.3 image?
If so make sure you don't enable 3rd party drivers in the install. That would not work out so well.

As far as current, it's probable if you used nomodeset to do the install it's using it now. That would give you poor performance.
What's this show?
```
cat /etc/default/grub
```

---

### Post by helloworld-21 on 2017-09-21
> **mc4man said:**
> I had a skylake with 860m last year & never had any issue installing 16.04. Have you tried using the latest 16.04.3 image?
If so make sure you don't enable 3rd party drivers in the install. That would not work out so well.

As far as current, it's probable if you used nomodeset to do the install it's using it now. That would give you poor performance.
What's this show?
```
cat /etc/default/grub
```

Thanks for the response. Turns out its actually a 960m. And I haven't tried 16.04. I had another Lenovo gaming laptop with an Nvidia card that had nouveau errors at start up and eventually the Ubuntu partition died. This was only after upgrading to 17. Version 15 worked fine with no problems. 

Also, I did choose the option to enable 3rd part drivers. Is that the cause? Both Nvidia and xorgs drivers were install apparently. When I switched to Nvidia's drivers, that's when the endless login loop occurs. 

And I can't post the contents of that file because it Ubuntu is literally too slow to use. Using the terminal alone takes forever. I'm on the windows side currently. It should be the standard grub file. I did make administrative changes to it by permanently adding the "nomodeset" option to it. That is the only way the thing boots up. 

Someone mentioned trying Fedora instead? I'm new to Linux (in college), but I'm going to need a distro good enough for a software developer.

---

