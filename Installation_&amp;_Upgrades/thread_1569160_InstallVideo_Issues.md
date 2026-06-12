---
title: "Install/Video Issues"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by TOinaeraser on 2010-09-06
Hello everyone, I'm new around here, but I've been using Ubuntu since 8.04, so I know a little of my way around. No hardcore terminal stuff yet, but slowly picking things up.

I am trying to install 10.04.1, and am having a lot of trouble. It is for EMC2 so the computer needs to meet very specific requirements, and using another one/swapping out hardware is not really an option. Using an earlier version is also not an option, 10.04 only.

The hardware specifics are:
ASUS P4G8X motherboard
P4 at 2.4Ghz
1GB RAM
32MB NVIDIA AGP-PRO video (I suspect this might be part of the problem, but can't change it to another card :( )
120GB ATA drive with 8.04LTS installed
40GB ATA drive target for 10.04
DVD-ROM drive


Anyway, the problem seems similar to what many other people are having, but I still cannot seem to resolve it. So here is what i think will be the most helpful, if any other information is required, just let me know.

On first installation, the computer would boot the cd, the purple screen with the person and keyboard would come up, and then the screen would go black with a flashing cursor. After a moment, the screen would flash black, no cursor, than go back to the blinking cursor black screen.

After this I tried a second download/write thinking the dvd was corrupt. This did not fix the problem.

I then tried the alternate install cd, which worked flawlessly, but on trying to boot into the new install, the same black screen problem would happen.

At this point I started reading about possible solutions, so the next thing I tried was booting with the nomodeset option. This improved thing slightly, now the screen saying ubuntu with the dots comes up.

This is where the current problem is. The computer hangs with all the dots orange. With escape pressed as it enters the loading screen, it hangs at:

```
* Setting sensors limit      [OK]
```

Thats it I think. Thank you very much for helping everyone.

---

### Post by TOinaeraser on 2010-09-06
Quick update:

I'm trying to install right now with the alternate cd (thinking maybe it is a cd problem where it hangs?) which worked before, but without video. Now I am using the nomodeset option, which helped get video working in the past. If this doesn't work I guess I'll have to go back to 8.04, unless anyone has other ideas.

Thanks a lot, TO.

---

### Post by TOinaeraser on 2010-09-06
OK, I got ubuntu successfully installed, but it still hangs at startup.
The last message, when not displaying splash is:
```
* Starting AppArmour Profiles
```

Edit:

Ok, I was able to boot in recovery mode. I choose failsafe graphics, and everything seems to be working. I have just been guessing my way along up to this point, so if anyone has any insight whatsoever, I will be thrilled... I'll keep bumbling along till that point.

Thanks again.

---

### Post by TOinaeraser on 2010-09-07
Ok, I've tried everything I know how to, so it looks like I'm installing windows xp (with mach3)... My last thought is to try finding out what video driver is running in 8.04 which is currently working, and installing that one. Except that there is no easy way to find out what driver is running in 8.04. Refer to this: [https://bugs.launchpad.net/ubuntu/+bug/214126](https://bugs.launchpad.net/ubuntu/+bug/214126)

I'm very frustrated. If no one has any ideas, I'm going to use windows... Thats right, I said it, windows!

In all seriousness though, thank you to anyone that has taken the time to look over my problem.

---

