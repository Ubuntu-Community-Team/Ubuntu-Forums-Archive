---
title: "Ubuntu 9.10 No GUI and Wireless Problem"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Californian on 2009-07-05
I know that these are probably a widespread and easily fixed but I am a total newbie, so please help!
My most pressing issue is that, after updating to Karmic Koala, there is no GUI! It is exactly like when you go out of XServer by pressing CTRL-ALT-F1. I can log in, but it is just a terminal window. What should I do?
Secondly, before updating (in fact, while updating as well), my wireless connection cuts out intermittently, I would estimate every 30 seconds. I have a Linksys Wireless-N router (wrt600n) and an Intel 4965AGN. My connection is not hidden and has WPA2 security.
Please help! Thanks in advance.

---

### Post by XCan on 2009-07-05
Can you start x using

startx

?

---

### Post by Californian on 2009-07-05
No, but I hadn't tried that before. It has a bunch of "failed to load" errors, specifically "the NVIDIA kernel module", "module "nvidia" (module-specific error, 0) and then says "No drivers available". After that, it says "Fatal server error: no screens found". Do you know what the problem is?

---

### Post by LewRockwell on 2009-07-05
ah yes, the infamous missing drivers scenario


NVIDIA strikes again

CLI only...anyone?

.

---

### Post by Californian on 2009-07-05
Oh good, you know the problem! Now how can I fix it?

---

### Post by Californian on 2009-07-05
And yes, CLI only here.

---

### Post by Californian on 2009-07-05
Okay, if no one can solve my problem, can someone at least tell me how to downgrade? Is that possible?

---

### Post by Californian on 2009-07-05
Thanks to those who replied, but I simply cannot wait any longer. I hope no one else encounters this problem, but just in case anyone has a solution, I will not mark this as solved until the day after tomorrow. As for me, I am going to wipe my drive (my dual-boot Windows 7 doesn't work after repartitioning yesterday anyway) and install Kubuntu 9.10 and cross my fingers for a better result. Yeah I know I'm a newb and I shouldn't use such an instable release, but I expect this.

---

### Post by psyke83 on 2009-07-06
> **Californian said:**
> Thanks to those who replied, but I simply cannot wait any longer. I hope no one else encounters this problem, but just in case anyone has a solution, I will not mark this as solved until the day after tomorrow. As for me, I am going to wipe my drive (my dual-boot Windows 7 doesn't work after repartitioning yesterday anyway) and install Kubuntu 9.10 and cross my fingers for a better result. Yeah I know I'm a newb and I shouldn't use such an instable release, but I expect this.

The development release is not even beta-quality yet. This means that you're expected to know how to administer your system via the terminal, and you shouldn't expect binary blob drivers to work without some manual patching (as we're using a release candidate kernel, which *always* causes problems with the NVIDIA binary blob, and sometimes with other out-of-tree drivers).

You really should revert to Jaunty (version 9.04). Installing an alpha release of Kubuntu will make no difference; you'll experiencing the same fundamental problem as with Ubuntu ("no GUI", as you say). 

P.S. You cannot downgrade without doing a fresh re-install.

---

### Post by cariboo on 2009-07-06
+1 if you're going to reinstall, install Jaunty, especially if you are a new user.

---

### Post by Mulenmar on 2009-07-06
Might I suggest a warning or something on the forum homepage warning not to use these prerelease versions unless you are familiar with using the CLI, and nothing else, to fix issues? I'm not exactly the longest-time member here, and I remember people saying they're "having issues with prerelease version, please HHHEEELLLP" since Gutsy Gibbon was relatively new.

I'm not pointing at the OP at all -- in fact, Californian handled it almost perfectly, in my view: knew there would likely be problems, and asked for some help when it didn't work -- without screaming, "help help I'm using this version [9.10, 10.04, whatever is a version ahead of present] and it doesn't work". Kudos to Californian on that.

If someone is going to try a (pre-)beta version of ANY operating system, I strongly recommend doing so on a spare computer, and **not** on your main machine. Else, research how to add the partition for your previous OS to the new bootloader (GRUB has a working example commented out in the configuration file), and then install to a separate partition. Also, have a dose of your favorite legal, non-prescription painkiller on hand, just in case :p

---

### Post by Californian on 2009-07-06
Thanks Mulenmar. I actually did have my other OS in GRUB, but I killed it while repartitioning. This time, I'll install Kubuntu (I'm trying Karmic again, but I expect it to not work) and then the other to solve the previous problem. As of now, I'm copying my media files to my external HDD with Kubuntu 9.10 live and all is going well, so I'm hopeful that the install will work.
My goal now is to have enough experience with Ubuntu so that by the next iteration I'll be helping others instead of being the one posting the confused smiley! I won't learn troubleshooting too quickly if I don't have to do a bit of my own though. Thanks again!

---

### Post by hexsel on 2009-07-06
You can type "sudo nano /etc/X11/xorg.conf" (or whatever filename it is, not on ubuntu now), then look for the string nvidia, replacing it by nv.

---

### Post by alexander.petkov on 2009-09-23
I'm having the same problems like Californian. 

I just happen to found out that need just to remove nvidia driver mentioning from "/etc/X11/xorg.conf", but now will try what hexsel has proposed since I still miss the enough colors. (Thanks hexsel!)

But, just wants to mention that I tried the 9.10 since the wireless was hanging the same way on 9.4. I'm not sure what's this problem exactly but, it disappoint me a lot since it is far-far worst behavior that I have expected and far-far worst then every windows that I've used.

Nevertheless the Ubuntu looks quite cool, but it is still not very usable unless you just need to browse some web pages and you are having pretty common hardware configuration.

---

