---
title: "Compiz problems after upgrade to 12.10"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2012-10-20
I have Nvidia GEForce 6200 TC card and driver 304.51 if that is significant. Things were working fine under 12.04. 
This is a 32-bit (Intel Core 2) system with 4Gb.
Here are the main issues:
1. Trying to move windows is very slow and jerky.
2. I cannot resize windows at all.
3. If the Unity Launcher is in auto-hide mode, it will never appear when I move the mouse to the left side of the screen.
I did try setting to defaults in ccsm. Did not help.
Possibly related: How do I bring up the "Additional/Restricted Drivers" screen in 12.10? There is no "indicator" for it in the top panel.
Thanks.
-- David

---

### Post by ivarss on 2012-10-23
And how did they manage to screw this all again? :confused: I am using GeForce 9500 GT with nvidia-current-updates driver version                   304.51-0ubuntu.

I upgraded and immediately had performance problems I did not have with 12.04. Created another user account with default Unity and Compiz settings - all the same.

Sounds like whining, but I am really fed up with this experience. Every release update is always worse than the previous one. That's consistent for the last two years. :guitar:
Sorry guys, after six years with Ubuntu I am finally giving up. Sitting now in front of my desktop with CPU fan screaming.

Regarding restricted drivers - they have moved it to Software Sources or whatever it is called in English, I am using localized Ubuntu desktop. There is a [last] tab now listing restricted drivers.

Adios, Ubuntu.

---

### Post by shochatd on 2012-10-23
Well, I was able to get some improvement by creating a fresh home directory for myself (while logged in to another admin account). Now I can re-size windows if I drag very slowly. I have systematically tried all 3 of the Nvidia drivers available under the tab you mention. With the 304.51, the Launcher will not un-hide but with the other two it will. I ran nvidia-bug-report.sh and am waiting to post to their forum once my account has been approved. If nothing comes of that, I may end up reverting this system to 12.04. Or switch to Xfce or something. But I'm not ready to give up yet.
-- David

---

### Post by shochatd on 2012-10-26
Breakthrough! I noticed that 12.10 uses compiz 0.9.8 while 12.04 uses 0.9.7. I was going to check the Changelog but decided to try launchpad first, and finally was led to:
[https://bugs.launchpad.net/compiz/+bug/1024304](https://bugs.launchpad.net/compiz/+bug/1024304)
What is referred to there as "WORKAROUND 1" (uncheck the 3 checkboxes in ccsm under OpenGL) makes my problem go away. I will watch that bug (or wait for compiz 0.9.9 to come out) at which point I will try re-selecting those 3 checkboxes and see if the problem is gone. As I understand what I'm reading in LP, the workaround restores things to work as they did in 12.04 so I think it makes sense to set this thread to Fixed although it is technically a workaround.
-- David

---

### Post by cstoh on 2012-10-26
I had Compiz error message on startup after installation. seemed to have gone. but now I cannot run softwre update. ends with an error message and the only action is to stop it. so how am i going to get software updtes?

---

### Post by shochatd on 2012-10-27
> **cstoh said:**
> I had Compiz error message on startup after installation. seemed to have gone. but now I cannot run softwre update. ends with an error message and the only action is to stop it. so how am i going to get software updtes?

What does the error message say? I had a problem like that which I dealt with by removing a couple of problematic software sources. If you can't run Software Sources from System Settings, you can also run it using software-properties-gtk from a terminal. And if compiz is dead, you might be able to bring up a terminal using right mouse on the desktop. You can also run ccsm that way if necessary.
-- David

---

### Post by llanitedave on 2012-10-27
My problems may be Compiz-related too.

After 6 months of flawless operation from Unity 12.04 on my homebuilt AMD Athlon 64 with an ATI Radeon  HD 4670 graphics card, I decided to take the risk and do a system upgrade rather than a clean install.

Disaster.

Neither the top panel nor the launcher will diplay at all under any circumstances.  The mouse cursor flickers rapidly.  I can get to system settings by right-clicking on the desktop, but none of the options I chose made any difference.

I ended up starting from scratch, and did a clean install from the Xubuntu 12.10 usb stick that I'df already made for my father-in-law.  That ended up working perfectly.

So far I've had great results from Xubuntu 12.10 and Kubuntu 12.10 on my laptop, Xubuntu on my desktop, and I'm afraid to even try Ubuntu.

If I do, it will be a clean install next time.

---

### Post by vandamme on 2012-10-28
> **llanitedave said:**
> My problems may be Compiz-related too.


Neither the top panel nor the launcher will diplay at all under any circumstances. 

Same here. I used Cinnamon on 12.04, so I blamed it on that. Maybe not the case??

---

### Post by ivarss on 2012-10-29
> **shochatd said:**
> 
What is referred to there as "WORKAROUND 1" (uncheck the 3 checkboxes in ccsm under OpenGL) makes my problem go away.
-- David

Thanks for info and the link, but no, it didn't help me at all. compiz still running at 12-70 % of CPU. 
My PC is really old, so every time devs mess up with performance I notice that firsthand.
Obviously, compiz and unity is the evil thing here so my workaround for the moment is that I trashed them for Gnome Shell + Docky, but the whole trend somewhat makes me **very** unhappy and I for sure will look for a viable alternative to Ubuntu :(
Br,
Ivars

---

### Post by bcollignon on 2013-04-25
By unchecking CCSM Open-GL boxes altogether, I was, at least, able to get Compiz to stop locking my computer.  GeForce 8300 CUDA Cores 8, VBIOS Version 62.77.22.00.01.  No effects, like water or fire, even though they're enabled and properly keyed from what I can tell.  Not overly impressed, as I had all of this running at some point prior to Unity.  Clearly there's lots of work here, considering various platforms, rendering methods and GPUs.  Good Luck.

---

### Post by bcollignon on 2013-04-25
UPDATE: CCSM, Preferences, Enable Integration into the Desktop Environment... box unchecked, most of the special effects and desktop wall, switching, etc., reappeared and worked.  This might be latest NVidia driver issue, however unchecking the environment integration box seemed to work for me, so far.  The only effect I can't get to work, of the ones I've played with, is Paint Fire on Desktop.  Also, the Unity Tweak tool seems to have some of the same tweaks.  Whether this performs many of the same functions as CCSM or whether it's conflicting, I don't know.  Again, good luck.

---

