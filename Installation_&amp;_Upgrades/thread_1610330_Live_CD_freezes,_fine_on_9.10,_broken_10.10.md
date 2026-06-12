---
title: "Live CD freezes, fine on 9.10, broken 10.10"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by broughton_g182 on 2010-10-31
Ok so I finally decided to try upgrade to 10.10. I burned the 64 bit ISO in unetbootin to a memory stick. Then rebooted and ran the live CD(is it still called live CD?). However on the desktop, the whole system will crash after anywhere between about 10 and 60 seconds and the only command that work is the big reset button on the front of the PC. This also happened when I tried upgrading from 9.10 to 10.04, to the point where I had to give up trying. Im still using 9.10 at the minute. My suspicions are that this is caused by the graphics card but i really dont know. Also, I dont know if its relevant or not but the cursor instantly moves to the top left corner over the ubuntu logo when it happens, usually with the busy cursur.

AMD athlon 4000 64 dual core
Nvidia Geforce 6200
1GB ram
300Gb HD
Upgrade 9.10 x64 to 10.10 x64

Anything else you need to know let me know :)

---

### Post by oxf on 2010-10-31
> **broughton_g182 said:**
> Ok so I finally decided to try upgrade to 10.10. I burned the 64 bit ISO in unetbootin to a memory stick. Then rebooted and ran the live CD(is it still called live CD?). However on the desktop, the whole system will crash after anywhere between about 10 and 60 seconds and the only command that work is the big reset button on the front of the PC. This also happened when I tried upgrading from 9.10 to 10.04, to the point where I had to give up trying. Im still using 9.10 at the minute. My suspicions are that this is caused by the graphics card but i really dont know. Also, I dont know if its relevant or not but the cursor instantly moves to the top left corner over the ubuntu logo when it happens, usually with the busy cursur.

AMD athlon 4000 64 dual core
Nvidia Geforce 6200
1GB ram
300Gb HD
Upgrade 9.10 x64 to 10.10 x64

Anything else you need to know let me know :)

Have you tried the 32 bit version? There have been many times when users who have trouble with the 64 ISO have success with the 32 bit. 

Just a thought :)

---

### Post by wilee-nilee on 2010-10-31
If you only have 1 gig of ram you should probably be running the 32 bit, as suggested.

Even with 1 gig of ram your system will run pretty well but I would max out your ram on the computer for the best usage.

---

### Post by broughton_g182 on 2010-11-01
Yes ive tried the 32 bit version as well, and the daily updated version with the same result... :(

---

### Post by wilee-nilee on 2010-11-01
> **broughton_g182 said:**
> Yes ive tried the 32 bit version as well, and the daily updated version with the same result... :(

So really to get the best help here, it will be always good to confirm exactly how a attempt at the 32 bit version went as well. I can assume it is similar eg crashing, but that is a assumption.

Since your going to need a graphic card driver to have it run I would use the hold down the shift when you boot Maverick to get to the choice of try or install and other options menu. Hit f6 and tick nomodeset and boot and see if things are different. You will be in a 600x800 resolution probably maybe better in this scenario.

If this works to get you in and install you will need to add the nomodeset to the kernel line at the reboot. Again hold down the shift to see the grub menu, hit e and use the arrow on the keyboard to navigate to the no splash at the end of the first kernel an put in nomodeset before no splash, No splash can be removed to see the text on the screen as it boots up.

This is just to get you in to check for drivers needed. It is a per session use in this manne when you just add text to the kernel line at the grub menu.

---

