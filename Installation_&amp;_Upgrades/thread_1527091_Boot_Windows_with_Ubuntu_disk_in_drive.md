---
title: "Boot Windows with Ubuntu disk in drive"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by Peter7895 on 2010-07-08
I have been very stupid and dove into Ubuntu without knowing anything about it. I inserted the disk described in    [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)    without Linux. I want to know how to get out of the command prompt and enter Windows so I can eject the disk and reboot my system. Please note, if you view this post that it is time sensative and I really need to get started on a report. Thanks in advance, Ububtu Community!

---

### Post by Peter7895 on 2010-07-08
Additionally, I am running Windows Vista, Home Premium.

---

### Post by lindsay7 on 2010-07-08
Turn off your computer. Stick a paper clip end into the hole in the cd or dvd drive face plate, take out the cd disk and turn your computer back on.

---

### Post by cavalier911 on 2010-07-08
```
sudo poweroff
```
DVD drive should eject the disk. 
When you remove it hit enter and computer should poweroff.

---

### Post by oldfred on 2010-07-08
As everything with computers there is more than one way:

sudo shutdown -h now
sudo shutdown -r 

h is halt
r is reboot
now is immediately

---

### Post by Peter7895 on 2010-07-09
Thanks, it worked!=D>

---

