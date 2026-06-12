---
title: "Stuck in low graphics: Output LVDS enabled but has no modes"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by DvirK on 2008-11-02
Hi,

I am using an ASUS Z70A with an Intel 915GM chipset (no graphics card).
So I recently upgraded from 8.04 to 8.10 and now whenever I turn on my computer, a black screen comes up and then I see :

```

(EE) intel(0): Output LVDS enabled but has no modes
(EE) intel(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration
```

I then have the choice of either 
"troubleshooting" the error - changing my xorg.conf file, 
reconfiguring my graphics - which just ends up in a blank screen
starting in low-graphics mode


I've been looking on the forums and apparently this issue was fixed in beta (not for me!):
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/274045]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/274045")

I've tried updating the intel xserver driver:
```
sudo apt-get install xserver-xorg-video-intel
```
but the terminal told me that this was up to date.

I've attached my xorg.conf file, my xorg.0.log file, and an error file :0.log. If anyone wants me to post anything else, please let me know. 

HELP!

---

### Post by dugb on 2008-11-16
Hi, I too am using an Intel on-board graphics MB. I have had no problems with 7.04 to 8.04, but having recently upgraded to 8.10 I am now getting the same issue as described in this post. I have researched the net and forums and have not been able to find the answer to the problem.

DvirK, have you found an answer to your problem?

---

### Post by DvirK on 2008-11-20
Unfortunately, I haven't. I tried playing around with xorg.conf, but that didn't work out. I wanted to try and install another version of xserver-xorg-core or xserver-xorg, but only one is available for 8.10. I hope the problem will be solved when they update xserver... If I somehow get it fixed I'll let you know (let me know if you can fix it too!)

---

### Post by dugb on 2008-11-20
Thanks for your reply DvirK.

I have essentially given up and look for updates to the services in the daily updates.

In time I am planning to revert to 8.04 since it worked correctly.

I will let you know if I see something else.

---

### Post by uMuppet on 2009-01-19
I've had no luck with this either.  I tried Jaunty Alpha 3 but no luck there.

I've gone back to 8.04 after reading your posts.  Thanks for the (temp) fix

---

