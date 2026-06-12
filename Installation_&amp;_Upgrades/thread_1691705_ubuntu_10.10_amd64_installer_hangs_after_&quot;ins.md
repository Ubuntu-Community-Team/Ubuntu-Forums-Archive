---
title: "ubuntu 10.10 amd64 installer hangs after &quot;install ubuntu&quot;"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by maxpowers43 on 2011-02-20
amd 64 10.10 alternate and normal installer hang up at cursor or black screen after selecting install ubuntu. sata hard drive, sata dvd drive, and nvidia discrete card fyi. going to try other os installer but would really like to use 10.10 if possible. does anyone know what is causing this. been using ubuntu since feisty, fyi. sata issues don't usually come up until partitioning menu. alternate cd usually works for graphics issues.
ubuntu community to the rescue!, i'm under a serious time constraint

---

### Post by sikander3786 on 2011-02-20
Check the MD5SUM of downloaded images and make sure they are healthy.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If sums match, check your disc for any defects.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If burning a new disc, burn it at the lowest possible speed preferrably 4x.

---

### Post by maxpowers43 on 2011-02-20
md5sum is correct
check disc for errors won't run either
tried debian 6 installer-reboots when hitting down arrow key at first screen
i'll see if i have a non debian iso to try
removed usb keyboard and installed ps/2 keyboard to rule that out-no luck
thanks
any other ideas?

---

### Post by Quackers on 2011-02-20
If the disc check won't run I would suspect the cd.

---

### Post by sikander3786 on 2011-02-20
Yes burn a new disc at the lowest possible speeds.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by maxpowers43 on 2011-02-20
ok i got it! the core unlocker feature on asus m4a87td usb3 was causing the problem. don't know why but that is definatly the reason.
thanks a lot for the help

---

