---
title: "&quot;OS not found&quot; problem - fresh hard drive in sony vaio E series with no other OS."
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by rahul11 on 2014-04-07
So I recently got a brand new harddrive for my laptop sony vaio E series. The brand isn't same as the one given by Sony (They gave Toshiba and now I have WD). And I decided to install ubuntu instead of windows.
I followed the steps given in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
but the system gives an error "OS not found" whenever I boot.
I also did boot repair following the instructions in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but with no luck.

Here's the link that I got from boot-repair - [http://paste.ubuntu.com/7216824](http://paste.ubuntu.com/7216824)

I do not understand the problem at all. I'm just a rookie when it comes to ubuntu.

the change in manufacturer of hard-disk shouldn't be a factor because the same error was given by sony vaio E series when I tried to install windows 7 in a different laptop (with the same harddrive as it came with that laptop's manufacturer) using a usb stick. Also, in just 4$ service charges many sellers here install windows in new harddrives all the time.

Any help would be much appreciated.

---

### Post by TheFu on 2014-04-07
13.04 support ended 2 months ago.
13.10 would be good and is the only way to get to 14.04 in a few weeks.

Boot off a 13.04 live CD (or USB drive), then open a terminal and run
```
sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```
Reboot and all should be fine.

---

### Post by rahul11 on 2014-04-07
Thanks a lot man. it worked. :D :D

---

### Post by TheFu on 2014-04-07
BTW, you got lucky - I had to do the same thing on my Chromebook C720 this morning after removing all the ChromeOS partitions (like 8 of them) and moving the Ubuntu install around. It was all fresh in my mind. ;)  I didn't have a clue how this worked yesterday.

---

