---
title: "Intel graphics corruption on a Lucid/Win7 dual boot laptop"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by g-a-c on 2010-03-16
Hi, I can't find a specific Lucid/Ubuntu+1 forum any more, have these been removed? I've put my post here for now, but if anyone knows a more appropriate place then please feel free to move it!

I have a Toshiba Portege A600 (Intel U9300 CPU, Intel GM45 graphics). This runs Ubuntu Lucid (upgraded from Karmic at ~Alpha 2 stage) and Windows 7 in what I believe to be a pretty standard dual boot installation (GRUB2, everything's kept completely separate and there isn't even a shared data partition). Usually I switch between the two by hibernating and then turning back on and selecting the correct option from the boot menu.

I've noticed recently that when I resume Windows, I often get some graphical corruption, which I can only cure by logging in and then shutting down/restarting. Example pictures are [here](http://teh-intar.net/11032010016.jpg) and [here](http://teh-intar.net/11032010017.jpg). Has anyone else seen this? I don't want to report it as a Ubuntu bug because the display in Ubuntu is always 100% perfect, however it only seems to have been happening since a few days after I upgraded to Lucid, my Karmic/Win7 dual boot on the same laptop was always fine.

Is it possible that, for example, the version of the Intel drivers in Lucid are leaving the hardware in some kind of "unknown" state which even though I hibernate (implying a poweroff) is then confusing the Windows drivers until I reboot a second time?

---

### Post by Mark Phelps on 2010-03-16
Looks a lot like what I saw when my Dell flat panel started failing. 

Started getting wierd artifacts on shutdown. Noticed they were heat-related.  When fist booting (monitor cold), no problems.  But when shutting down (monitor hot), got artifacts.

Didn't notice them other times -- at first.  But, over time, they got worse and worse.  After a few months, had to replace the monitor.

Suggest you try connecting your machine to an external monitor to see if these artifacts appear.  Also, try booting cold and immediately shutting down.

---

