---
title: "Wubi 10.04 No specified Filesystem Error"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by nkhosla on 2012-03-25
Hi,

I tried to install Ubuntu 10.04 on my computer (windows 7) using WUBI.  It installed from windows, but when I went to boot up I got an error saying that there was no specified root filesystem. My progress bar was also at 271%, so something was clearly wrong.  

I looked over and saw a couple of people had this problem, but most of those threads were from 2010 or 2011 and were unclear and did not really offer a resolution. From what I  understand, the problem has to do with my partition table and somewhere something overwrote the beginning or end of a partition (as I said things were unclear, so that may be wrong).

 So...can anyone explain this to me?  I would really love to get this working.

Thanks,
Nkhosla

---

### Post by bcbc on 2012-03-25
The easiest way to figure out the Wubi 'no root file system is defined' issue is to boot from an Ubuntu CD/USB and select "Try Ubuntu". Then post the result of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

You could manually obtain some diagnostics when you get that error, but you'd have to take a picture or write it down (which is a pain).
e.g. hit Ctrl+Alt+F1 to drop to a terminal. Then run
```
sudo parted -l
```
```
sudo fdisk -l
```
Both the above commands use lower case -L (not -1).
Also
```
sudo blkid
``` might tell if there is some fakeraid issue.
When you're done getting the diagnostics, reboot using:
```
sudo reboot
```

---

