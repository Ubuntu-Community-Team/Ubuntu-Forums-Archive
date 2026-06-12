---
title: "Linux swap queries"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by bals on 2011-07-16
hi, i have ubuntu 10.10, mint 9, ubuntu 11.04 and windows 7, all in seperate partitions. installed in my system. i use 10.10 mostly. when i installed it, i had not specified swap space. so hibernate was not working. when i installed 11.04, i had specified 1.1 gb swap space. now, when i boot into 10.04 and check my disk utilities, it says that the 1.1 gb swap space is 'unknown' partition. when i boot into 11.04, it shows the partition as 'linux swap', and i am able to hibernate.

is it possible to get hibernate in 10.04 by formatting this partition as linux swap and turning on swap at the time of booting?

---

### Post by cipherboy_loc on 2011-07-16
Possible solutions:

1) Checking **sudo fdisk -l** to see if it really is a linux swap partition. If it is, and you still don't see it, try reformatting it from 10.04. Not really sure the Firmware/Filesystem changes from the 10.04/10.10 kernels to the 11.04 ones, but there might have been a linux swap partition change. 

2) Copying the line in 11.04's */etc/fstab* file which is under the line that says something like "# swap was on /dev/SOMETHING", or "# swap was on UUID=[UUID]" to the 10.04/10.10 FSTAB. 



I would probably try 2 first and then 1.

Cipherboy

---

### Post by bals on 2011-07-17
tried option 2. no change..

---

### Post by cipherboy_loc on 2011-07-17
Did you reboot? Also, you might try **sudo swapon /dev/sd<swap partition>**. Recreating the swap partition from an older version should be easy, just make sure you don't have 11.04 hibernated before. 


Cipherboy

---

### Post by bals on 2011-07-18
when i did fdisk, the swap space was shown as
/dev/sda8           33538       33671     1073152   82  Linux swap / Solaris
when i did swap on, the following error was displayed
swapon: /dev/sda8: read swap header failed: Invalid argument

earlier when i installed mint 9, this partition was my swap space. then i could swapon the partition in ubuntu and after logging off, i got the hibernate option. but after installing 11.04, this is not possible.

---

### Post by dino99 on 2011-07-18
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)

---

### Post by bals on 2011-07-18
i was able to hibernate with just 1.1 gb swap

---

