---
title: "Update Manager problem after updating to  Ubuntu 8.04"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by fdubru on 2008-06-06
Hello,

I have been having problem with Ubuntu Updates since I have upgraded to  Ubuntu 8.04. The Update Manager doesn't find any updates anymore and show this message:

"Your system is up to date
It is unknown when the package information was updated last. Please try clicking on the 'Check' button to update the information"

I have tried to update the info many times without success.

I would not like to proceed with the re-installtion from srcatch, any help  most welcome.

Thanks a lot for your time,
Fred

---

### Post by ricemanwm on 2008-06-06
I have exactly the same problem and I'm very interested if anyone has a solution.  I installed Hardy 3 months ago and have not received any updates.  I've tried Synaptic Package Manager / Mark All  Upgrades too.  No updates.  I'm not interested in rebuilding the disk from scratch.  Mark

---

### Post by ricemanwm on 2008-06-06
Fred,
  I figured out our problem, or at least mine.  I just installed over 200 updates.  Go to System / Administration / Synaptic Package Manager / settings / repositories / updates 

I checked all four boxes for ubuntu updates.

I then did a update and lots of updates came in.

---

### Post by iaculallad on 2008-06-06
Try using your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Bubba64 on 2008-06-06
> **ricemanwm said:**
> Fred,
  I figured out our problem, or at least mine.  I just installed over 200 updates.  Go to System / Administration / Synaptic Package Manager / settings / repositories / updates 

I checked all four boxes for ubuntu updates.

I then did a update and lots of updates came in.

Also installing medibuntu is a good idea.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by fdubru on 2008-06-07
I am afraid that none of the solution listed above works :-(

Fred

---

### Post by cainmark on 2008-06-09
> **fdubru said:**
> I am afraid that none of the solution listed above works :-(

Fred

Same problem, no matter even if I use the US main server, any close to me, or the main repository--I keep getting "It's been No. days since your last update", even if I just went through all the update steps, synaptic or terminal.  Worked fine till 19 days ago.  Don't know what was different.  The listings say, "malformed index file?" as it speeds by.

UPDATE:  I cleaned up my /etc/sources.lst and that helped. Some.  Still saying my last package update was 20 days ago, when I just updated it now.

---

