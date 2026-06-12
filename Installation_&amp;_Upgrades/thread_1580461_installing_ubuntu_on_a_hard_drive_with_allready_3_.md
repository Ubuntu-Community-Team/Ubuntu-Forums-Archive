---
title: "installing ubuntu on a hard drive with allready 3 primary partitions"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by jajaja_622 on 2010-09-23
just as the title says, i just bought an hp dm4 and i want to install ubuntu on it, but it allready came with 3 partitions: the C drive where everything goes, a recovery partition and a hp tools partition. I downloaded a partition manager and it says that the 3 paritition are "primary", and i read something about that the MBR only support up to 4 primary partitions, so my question is if ubuntu only needs 1 primary partition to install? 
Pd: sorry for my bad english, its not my first language

---

### Post by sikander3786 on 2010-09-23
Ubuntu doesn't really need a primary partition. You can install it to a logical partition as well. If you prefer, just create a primary partition for /root and install it. Otherwise you can create an extended partition and split it for /root, /home, /tmp, swap etc etc. Post back if you need some more information for installation.

You've read correct about 4 primary partitions on a single HDD. :-)

Regards.

---

### Post by jajaja_622 on 2010-09-24
ah! ok, thanks, i wasnt sure about that, so when it ask me where i want to install it, can i choose "install with my current operating system" as i always do? so it make all the partition automatically?,  and i noticed that it says beta for the x64 version, it is worth installing?

---

### Post by sikander3786 on 2010-09-24
Yes you can choose to install it with your current operating system and it will automatically create partitions itself.

Beta for x64? You might have downloaded 10.10 Maverick Meerkat. It is scheduled to be released in October this year. 10.04.1 is there and is an LTS release. 10.10 should not be used on production machines until the stable is out.

Download from here and select 64-bit on that page.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

For more information on LTS releases.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by jajaja_622 on 2010-09-24
ok.. i will install it just like that, i'm sorry i meant about this "Not recommended for daily desktop usage" about the x64 version, not beta. One last question if it is not too much to ask.. this HP came with an instant on OS that initiates before windows, what would happen to it once i install ubuntu?

---

### Post by sikander3786 on 2010-09-24
"Not recommended for daily desktop usage" is a term that really need to be modified to something else. Like "Recommended for 64-bit capable machines. See your product documentation for details". If you have a 64-bit system, go with the 64-bit Ubuntu.

I don't know about HP's instant OS but I feel it will be something like Asus Express Gate that takes you online in a few seconds. It is an option that can be turned off in the Bios settings. Even if you don't turn it off, you should be able to install Ubuntu.

> One last question if it is not too much to ask

Never mind. You are most welcome. :-)

---

### Post by jajaja_622 on 2010-09-24
thanks again, that was my last doubt, and yes.. it should be changed to something like you said.

---

