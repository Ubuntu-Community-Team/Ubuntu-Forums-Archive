---
title: "Stuck at GRUB"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by markjo on 2011-03-31
I am having problem with booting.  My PC starts and getting stuck at 'GRUB'.  No, booting takes place. Blank screen with one word 'GRUB' at top-left and blinking cursor.  I have two harddisks. Both at detected in Setup screen. But, in boot priority one of them is missing.  Few days back had the same problem, but got auto solved after few reboots.  Please help.

---

### Post by wilee-nilee on 2011-04-01
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by markjo on 2011-04-01
Hey, it got auto fixed again.  I plugged in some pen-drives and it booted normally. However, in boot priority Hrddisk is first. Also, their is no boot loader installed on any of the pen-drives i plugged in.  Kinda of weird behaviour. I'll try not to shutdown/reboot as much as possible. Anyone knows about such situation?

---

### Post by Hedgehog1 on 2011-04-01
> **markjo said:**
> Hey, it got auto fixed again.  I plugged in some pen-drives and it booted normally. However, in boot priority Hrddisk is first. Also, their is no boot loader installed on any of the pen-drives i plugged in.  Kinda of weird behaviour. I'll try not to shutdown/reboot as much as possible. Anyone knows about such situation?

markjo,

If you would please run the script and post the results that **wilee-nilee** has in his post (Post #2), this will give us the data to try to figure it out.

***The Hedge***

:KS

---

### Post by markjo on 2011-04-01
what info? I dont want to run script which gathers extra info. The result.txt generated aggregates lot of info. Plus, i think it executes some internet related commands too.  do you need fdisk -l, and menu.lst?  Btw, Nothin related to grub & partition setup has been changed though.   The Error situation is not constant. It get stuck at boot time occassionally. I cleaned the RAM, replugged the HDD, but it did not solve the issue. It just started booting again normally, am not sure what really fixes it.  I think its related to HDD & removable drives that r plugged in.  Can anyone please, help me by tell how to add HDD to boot priority?  When the error happened, both my HDD were getting detected, but one of them was absent from boot priority list.  Thanks.

---

### Post by markjo on 2011-04-01
OMG! its stuck again. :(

---

### Post by Hedgehog1 on 2011-04-02
You are making it very hard to help you.

My **GUESS** (and I have to guess sense you don't want to run the script that would give us **REAL** data) is that while the USB sticks are not set to boot, one of them has the **/boot/grub** directory on it that the PC is using when it runs grub.  That is why the PC boots when the right non-booting USB stick is present.

If you can find the right USB stick and get your PC to boot, you can correct this situation by selecting Ubuntu from grub and then doing this:

```
sudo update-grub
```

We will see how good a guesser I am...  Hedgehogs often have a knack for these things... :D


***The Hedge***

:KS

---

