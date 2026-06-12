---
title: "Signal out of range. Ubuntu Live Cd"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by rocknrolf77 on 2006-12-26
I have a problem with "signal out of range" when x starts, when trying too run the live cd. It's not the monitor that is the problem cause it works with my own computer on the same screen. 

Tried the alternate install too, and when it was installed I gor the same problem. Any good boot parameters I can include, cause I have no idea what the problem is. 

Dreamlinux and sabayon is working fine, but it's too complicated. Cause I'm trying too install on my fathers computer too get him too use linux. And dreamlinux's documentation is almost only in portugese. :(

---

### Post by meng on 2006-12-26
Assuming this is an LCD monitor you are using, and that the system is sending too high a refresh rate. When you get to the out of range message, hit ctrl-alt-f1 and login to a text console. Then try
sudo dpkg-reconfigure xserver-xorg
and choose the defaults for most things except see if there is a lower refresh rate you can choose (probably 60 Hz)
Not sure if this advice will work, but it can't hurt!

---

### Post by rocknrolf77 on 2006-12-26
Do you get a password promt from the live cd when doing this? In that case is there a "deafult" root password in the live cd? Why does it work on one computer with the same monitor on not on the other one?

---

### Post by wpshooter on 2006-12-26
Rocknfolf77:

Is your video card an ATI ?

---

### Post by rocknrolf77 on 2006-12-26
Yes, but i solved the problem. Worked with the ati driver but not with vesa. It's my fathers computer. Trying to convert him. I'm a happy nvidia owner. But he don't have use for 3d so it's no problem. Or are has ati drivers improved in the last couple of months? :)

---

### Post by wpshooter on 2006-12-27
One more recruit.  Good work.  Keep 'em coming.

---

