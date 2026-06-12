---
title: "Less disk space after reinstalling ubuntu 14.04"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by matogolf on 2016-10-15
I had some problem with my ubuntu so I decited to reinstall it. I had 21GB assigned... After reinstalling ubuntu there is only 12.6GB total [COLOR=#000000][FONT=arial]according to[/FONT][/COLOR] system monitor.

Edit: I figured out that there is 8GB swap partition. Is it possible somehow to merge swap partition with main partition to create 21GB total and not lose data? 

(I have dual boot - windows 10)

Thanks
-Martin

---

### Post by howefield on 2016-10-15
Can we see the output of the terminal command...

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

---

### Post by matogolf on 2016-10-16
I figured out everything. I just deleted swap partition and then extented home partition... Thanks anyway. Very simple. I am quite silly...

---

### Post by RobGoss on 2016-10-16
Glad you resolved your issue, if you don't mind can you mark this thread as** solved,** you can do this by using the **Thread tool option** from the drop down menu at the top of this post. Thanks so much

---

