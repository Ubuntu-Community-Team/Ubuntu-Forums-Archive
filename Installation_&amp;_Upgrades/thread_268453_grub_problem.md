---
title: "grub problem"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by Belibem on 2006-09-30
I have a strange problem with my grub. Specifically, I was trying to install ubuntu on an old hd. The hd contained two working partions, a linux and a win one. I formatted the old linux partition and installed ubuntu on it. 
Then something went wrong with grub. When I try to boot my pc the OLD grub boot options are displayed (of course they don't work since the old linux installation does not exist anymore). However, if I boot from ubuntu cd and then select "boot from first hard disk" the correct (new) options are displayed. :confused: 

Any recommendations?

---

### Post by Iarwain ben-adar on 2006-09-30
Hi,
try reinstalling grub
```
sudo grub
grub> find /boot/grub/stage1
grub> root (hdx,y)
grub> install hd0
```

That should do the trick i think,
report back if you have any problems :D


Iarwain

---

### Post by Belibem on 2006-10-01
One of the steps  (installation to the mbr) doesn't seem to work

grub> find /boot/grub/stage1
 (hd0,4)
 (hd1,1)

grub> root (hd0,4)

grub> install hd0

Error 1: Filename must be either an absolute pathname or blocklist

---

### Post by Iarwain ben-adar on 2006-10-01
Hi,
what gives ```
grub> install (hd0,4)
```
?


Iarwain

---

### Post by Belibem on 2006-10-01
Hi, thanx for trying to help me :)

I get the same error:

grub> install (hd0,4)

Error 1: Filename must be either an absolute pathname or blocklist

---

### Post by Iarwain ben-adar on 2006-10-03
Sorry,
don't know what could be the problem then :s


Iarwain

---

