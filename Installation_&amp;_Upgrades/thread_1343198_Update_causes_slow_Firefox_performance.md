---
title: "Update causes slow Firefox performance"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by Civil_777 on 2009-12-01
I updated my system this morning (currently running 9.10).  I did not pay much attention to what the updates included, but there were several updates.

After I restarted my system, I noticed that Firefox was running very slowly.  I checked the CPU% on the system monitor, and it was running up to 70%.  I thought the problem might be Firefox related, so I switched to Chrome - but Chrome is consuming up to 97% of the CPU!

I'm not sure which component is causing the problem.  Is there any way to check which components were updated and then undo some of the updates?

Any help is appreciated.

---

### Post by Civil_777 on 2009-12-01
I restarted my system and the browsers now work fine.

---

### Post by geodanny on 2009-12-02
This is happening to me as well; however, I do not think it is FF alone. I think there is something in the new code that sucks memory. 

If I let my computer run for a long time, particularly if I Suspend Ubuntu (close the lid) and then unsuspend (open the lid), more than 2/3's of the memory will be taken up without running FF. It isn't any one program but a whole series of them that seem to be hogging memory and not letting it go. I'm not sure which ones since I am forced to restart at that point. I'm on the forums looking for the best logs to get and how to best report the problems. 

Anyone have any suggestions on how to identify the culprit and the best way to report it? I have a Dell Latitude D620.

**********
Commit Log for Tue Dec  1 10:57:53 2009


Upgraded the following packages:
gdm (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
sreadahead (1.0-5) to 1:0.90.3-2
tzdata (2009r-0ubuntu9.10) to 2009s-0ubuntu0.9.10
tzdata-java (2009r-0ubuntu9.10) to 2009s-0ubuntu0.9.10
x11-common (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-input-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-video-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10

Installed the following packages:
ureadahead (0.90.3-2)

---

