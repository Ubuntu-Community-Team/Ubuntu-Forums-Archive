---
title: "How can i install Ubuntu without having all my hard drive erased?"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by TheFalcon 2010 on 2010-09-13
I wanna install Ubuntu with windows xp (dual boot)no WUBI,but i saw some people on some forums who got their hard disk erased and lost all their data on the HDD when trying to install Ubuntu.So how can i avoid that?
my HDD (160GB) has 4 partitions C,D,E and F.my windows xp is currently installed on partition C although this partition still has 10.4GB free.so will i have to divide the partition C into 2 partitions (with partition magic)? or what should i do else?
Thanks.:)

---

### Post by garvinrick4 on 2010-09-13
Put in your Ubuntu install Cd and Use Try Ubuntu not install Ubuntu and when it boots up go to System/Administration to gparted open gparted and take a screen shot of in and upload it to this thread you have started and lets take a look. They will be sda1, sda2, sda3 and so on in Linux in Windows they use letters.

---

### Post by 0N3 on 2010-09-13
There's an option when installing Ubuntu Install side by side is probably your best option

---

### Post by Felixcasmiry on 2010-09-13
To install ubuntu without deleting the data do the following.
1. Have your ubuntu installation media ie. cd.
2. have a partition in you hdd with enough space  that you want ubuntu to be installed in that case let's say partition 'E' (Note: Data on that partition only will be deleted but not the other partitions)
3. Boot your machine from CD, when you reach on the step that prompt you to 'prepare disk space' select the button  named "specify the partition manually". Then you will see all partition you have ie. sda1, sda2, sda3.
4. Select the parition that you want to install ubuntu ie. "E" then follow the wizard.

NOTE: After you select E you must again create a **swap** partition  (from partion 'E')of at least 3GB  and select the remaining part of that partition to install ubuntu. The partition names will not be seen as in windows but they will be seen in lists as sda1, sda2, sda3 similarly to disk C, D, and E in windows where by C contain windows OS.

---

### Post by TheFalcon 2010 on 2010-09-13
> **0N3 said:**
> There's an option when installing Ubuntu Install side by side is probably your best option

If i selected "Install side by side" in which partition will Ubuntu be installed?

---

### Post by oldfred on 2010-09-13
Side by side will normally shrink you largest partition and create new ones. But if you have used c,d, e, & f then you may have used all four primary partiitons. You can have four primary partitions or one primary can become an extended partition that holds many logical partitions. Linux will install and work from the logical, so you only need to have one available partition to make as the extended to hold the linux partitions.

Also if you only have 10GB free in windows you do not have enought room. Windows will stop working (or slow down greatly) when it gets below about 20% free space. You can install Ubuntu in 10GB but cannot shrink windows too much.

---

