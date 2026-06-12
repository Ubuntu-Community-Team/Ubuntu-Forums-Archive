---
title: "Swap drive not found"
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by HSovieticus on 2017-11-15
I just can't get my swap to work

[https://imgur.com/iLJpSmA](https://imgur.com/iLJpSmA)
on the right console you can see the error message.
on the left you can see its not using swap.
i removed my swapfile and created a bigger swap partition and did everything in the swapwiki here, but it cant find the device.


[https://imgur.com/s8ZUJRP](https://imgur.com/s8ZUJRP)
here is fstab and gparted with info

if you need more info just ask. i'm a complete novice. but i followed the directions on [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by deadflowr on 2017-11-15
The UUIDs don't match in fstab and gparted.
Copy the UUID from the gparted info page and remove the current one in the fstab file and place the one from the gparted output into it.

---

### Post by HSovieticus on 2017-11-15
ya oddly enough the uuid keeps changing everytime i go through the process.

---

### Post by HSovieticus on 2017-11-15
[IMG]https://i.imgur.com/DBBXgxS.png[/IMG]
I got the lines correct but Swap is not booting.

err. ok, i was informed that its not supposed to boot. so i have no idea why swap isnt working.

---

### Post by HSovieticus on 2017-11-15
[IMG]https://i.imgur.com/GYgXo7B.png[/IMG]
mem declining with more open processes, but no swap use.

i checked the swap drive for bad blocks. none

EDIT: it seems to be working at swappiness 50.

---

### Post by oldfred on 2017-11-15
You do not want to use swap as it is orders of magnitude slower than RAM.
And the Linux kernel uses RAM up to its limit before removing older apps and using newer ones.
Only if your working apps use more than available RAM,  do you then use swap.

I had 4GB in my older system and still never (almost never) used swap.

Note that 17.04 or later uses a swap file by default, but will use a swap partition if found.
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by HSovieticus on 2017-11-16
i have less than 2gb and the processor is slow so i think it wasnt able to swap before crashing

---

### Post by photonxp on 2017-11-20
> **HSovieticus said:**
> ya oddly enough the uuid keeps changing everytime i go through the process.

According to [https://unix.stackexchange.com/questions/231001/expand-the-size-of-swap-partition](https://unix.stackexchange.com/questions/231001/expand-the-size-of-swap-partition)
> Note that mkswap generates a new partition UUID when run

---

