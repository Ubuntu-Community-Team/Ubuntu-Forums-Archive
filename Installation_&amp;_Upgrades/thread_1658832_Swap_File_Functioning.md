---
title: "Swap File Functioning?"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by danost on 2011-01-03
During the install of Ubuntu 10.1 from CD, something went wrong, the partitioning of the empty hard drive was a mess. I then wiped the drive clean and used Parted Magic 5.8 to set up a partition for Linux 13 Gigs, and a swap file of 2 Gigs.  Then I installed Ubuntu from the CD.

My question is, as the swap file was setup not using the Ubuntu setup CD, how can I be sure that Ubuntu is recognizing and using the swap file that I set up via Parted Magic?

Thank You
Dan

---

### Post by ajgreeny on 2011-01-03
Let's see the output of the command ```
free -m
``` in terminal.

That will show the amount of ram in use, and the swap size and usage as well.

---

### Post by matt_symes on 2011-01-03
Hi

Open a terminal and type

```
free -m
```

This is mine.

```
matthew@matthew-laptop:~/linux-2.6.32/arch/x86/boot$ free -m
             total       used       free     shared    buffers     cached
Mem:          2770       2388        381          0        143        754
-/+ buffers/cache:       1491       1279
**Swap:         2088         30       2058**
```

a swap total of zero represent a swap file of 0.

You can turn swap on and off using the comands

```
swapon
swapoff
```

and you can check it is hooked up in you fstab file

```
cat /etc/fstab
```

This is mine

```
# / was on /dev/sda5 during installation
UUID=3d48429c-7361-4ab8-8689-54407673b141 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
**UUID=b1c6171a-075e-4291-af69-64baf751d10e none            swap    sw 0 0** 
``` 

Use 

```
sudo blkid
```

to get the id for the swap parition 

Kind regards

---

### Post by lithopsian on 2011-01-03
free is far from the best or easiest way to examine your swap, since a swap total of zero may just mean nothing has yet been swapped.  swapon itself will show you exactly what's going on if you supply the -s parameter.
```
sudo swapon -s
```Typical output (looks prettier in xterm!):
```
Filename                Type        Size    Used    Priority
/dev/ramzswap0                          partition    65528    6720    10
/media/512Mb.swap                       file        524280    0    -1

```

---

### Post by matt_symes on 2011-01-03
Hi

> free is far from the best or easiest way to examine your swap, since a swap total of zero may just mean nothing has yet been swapped.

?

Swap total gives you the total amount of swap available.
Swap used gives the amount of swap used (which is what i think you mean and can be zero as below).
Swap free gives the amount of swap free.

```
matthew@matthew-laptop:/usr/share/sounds/ubuntu/stereo$ free -m
             total       used       free     shared    buffers     cached
Mem:          2770       1306       1464          0         61        386
-/+ buffers/cache:        857       1912
Swap:         2088          0       2088
```

Kind regards

---

### Post by uRock on 2011-01-03
The free command is perfect for this. Even if nothing is sent to swap, it shows that the swap is there and usable.

Another way to see that swap is there and if it is being used is with the System monitor in the System> Administration menu.

---

### Post by danost on 2011-01-04
Many thanks for the kind input from each of you, its very much appreciated, especially as there is a lot to learn in Linux. I'm going to try your recommendation today.
Dan

---

