---
title: "black screen of death"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by boylanmaker on 2006-12-04
ok so I am new to linux but not to computers.  I was attempting to install ubuntu 6.1 on a 40 gig stand alone drive. this is a amd 64 3700 with 1 gig of ddr ram and nvidia 6600 gt agp system.  I loaded the os no problems from a live cd.  installed and rebooted, this is were it gets fun.  the system no longer responds like it has a video card installed.  no video out put.  I reattached my 300 gig raptor winxp pro drive and everything works fine.  so there are no mechanical errors in the loop.  the logical conclusion is a bad driver compatibility for ubuntu.  how do I fix this?  can I fix it using the live cd?  
how do i fix this when the output of video is negative?  

needing help Brian
in the lbc

---

### Post by taurus on 2006-12-04
I have a couple of ways to do it so let's try the first method first.  Boot your Ubuntu into recovery mode from GRUB menu and at the prompt, reconfigure your X again...

```
dpkg-recconfigure xserver-xorg
startx
```
If it works, then reboot.  

Otherwise, let me know and we can go to the next method...

---

