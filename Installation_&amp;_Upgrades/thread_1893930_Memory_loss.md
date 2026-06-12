---
title: "Memory loss"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by Cyber Sheep on 2011-12-11
Hello, Ubuntu Forums.

I have run into a problem. My laptop (HP Pavilion dv6 3240-us entertainment PC with AMD premium tri-core processor) originally had Windows when I bought it. Naturally, I wanted to change it to Ubuntu. I did so.

However,  when I checked my memory and RAM, my memory was only 20GB. My laptop came with 570GB of memory and 4GB RAM. I don't know if this problem was caused by me being careless and installing Ubuntu on a different partition other than the main one or what. Is there any way I can get my full memory back without re-installing?

---

### Post by bluexrider on 2011-12-11
You want to know how much space you have on your hard drive?

In terminal run this command 

sudo fdisk -l       "small -L"

---

### Post by WasMeHere on 2011-12-11
Welcome to the Ubuntu Forums, Cyber Sheep :-)

What flavour of Ubuntu have you installed (vanilla Ubuntu with Unity Desktop)? And which version (11.10 or an earlier version)?

Please post the results of the following two terminal commands
```
sudo fdisk -lu
sudo df
```
Knowing this makes it easier to help.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Cyber Sheep on 2011-12-11
> **bluexrider said:**
> You want to know how much space you have on your hard drive?

No, I only have 20GB on my hard drive when I'm supposed to have 570GB.

---

### Post by Cyber Sheep on 2011-12-11
> **Olle Wiklund said:**
> Welcome to the Ubuntu Forums, Cyber Sheep :-)

What flavour of Ubuntu have you installed (vanilla Ubuntu with Unity Desktop)? And which version (11.10 or an earlier version)?

Please post the results of the following two terminal commands
```
sudo fdisk -lu
sudo df
```Knowing this makes it easier to help.

Have fun finding out about Ubuntu :-)
Olle

Thank you :)
I'm running Ubuntu 11.10 Oneiric Ocelot with GNOME shell.

```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4b88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1225687039   612842496   83  Linux
/dev/sda2      1225689086  1250263039    12286977    5  Extended
/dev/sda5      1225689088  1250263039    12286976   82  Linux swap / Solaris


```

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            603225904  66356448 506227332  12% /
udev                   1922340         4   1922336   1% /dev
tmpfs                   772892      1028    771864   1% /run
none                      5120         0      5120   0% /run/lock
none                   1932224      1360   1930864   1% /run/shm
/home/omer/.Private  603225904  66356448 506227332  12% /home/omer


```

---

### Post by WasMeHere on 2011-12-11
You have [COLOR="red"]603[/COLOR][COLOR="blue"]225[/COLOR]904 kbytes
in your ubuntu file system ([COLOR="red"]approx. 603 GB[/COLOR] and you use only 12% of it now, so there is approx. 500 GB free to use :-)
> ```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            603225904  66356448 506227332  12% /
```
How did you come to the conclusion, that you have only 20GB?

---

### Post by Cyber Sheep on 2011-12-11
> **Olle Wiklund said:**
> You have [COLOR=red]603[/COLOR][COLOR=blue]225[/COLOR]904 kbytes
in your ubuntu file system ([COLOR=red]approx. 603 GB[/COLOR] and you use only 12% of it now, so there is approx. 500 GB free to use :-)

How did you come to the conclusion, that you have only 20GB?
Maybe even less. I ran this in the terminal:

```

omer@Omer:~$ grep MemTotal /proc/meminfo
MemTotal:        3864452 kB

```

Meaning this many GB: 3.68543

---

### Post by CryptAck on 2011-12-11
> **Cyber Sheep said:**
> Maybe even less. I ran this in the terminal:

Meaning this many GB: 3.68543

You are confusing hard drive space and memory. "Memory" typically refers to "RAM", not hard drive space.

---

### Post by WasMeHere on 2011-12-11
That is the available RAM. I suggest that you use the GUI tool
***gnome-system-monitor*** to get such information. It is also a menu item.

---

### Post by Cyber Sheep on 2011-12-11
> **CryptAck said:**
> You are confusing hard drive space and memory. "Memory" typically refers to "RAM", not hard drive space.

Hmm... I see. Thanks for this. I'll look into it.

---

### Post by Cyber Sheep on 2011-12-11
According to ***gnome-system-monitor, ***I have approximately 500GB left, as Olle said.

This has been resolved, thank you to everyone for helping me.

---

### Post by CryptAck on 2011-12-11
> **Cyber Sheep said:**
> According to ***gnome-system-monitor, ***I have approximately 500GB left, as Olle said.

This has been resolved, thank you to everyone for helping me.

You're Welcome! :)

Please mark the thread "SOLVED". To do so, Select "Thread Tools > Mark Solved".

Thanks!

---

### Post by bluexrider on 2011-12-11
> **bluexrider said:**
> You want to know how much space you have on your hard drive?

In terminal run this command 

sudo fdisk -l       "small -L"

humm reason for my original question. redundant now

Mark this

(SOLVED)

---

