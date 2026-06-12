---
title: "boot patition full"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2012-09-12
I run a headless server (so please don't tell me to use package manager, as theres no monitor, keyboard or mouse attached to the system, and its in a datacenter).

I ran an apt-get dist-upgrade this afternoon, but it aborted during a new kernel image install, due to the /boot directory being full. I wouldn't normally have an issue, I'd just deinstall some of the old kernels, to make room for the new one.

Unfortunatly, because apt-get is being stupid, when I do apt-get remove linux-image-(whatever), it automatically tries to complete the previous install **first**, and since that fails (obviously it will), it doesnt complete my requested "remove".

So the whole process is a catch-22 situation.

apt-get cant complete the previous command because the directory is full.
apt-get wont execute the new command (to free some space in the directory) because the previous command never completed.
apt-get tries to complete the previous command, but fails because the directory is full.
rinse-repeat.

How can I get apt-get to FORGET the previous command, or execute the REMOVE command first?

---

### Post by darkod on 2012-09-12
There are usually messages when any partition is close to full. You didn't notice anything?

I have never been in similar situation, but what if you simply try to delete some of the older kernels with rm? I guess that should free some space right away.

Of course, watch out which ones you delete.

---

### Post by Milambar on 2012-09-13
Thats essentially what I did. 

I moved all but one of the kernels to my home directory which is on a different disk, with oodles of space, let it complete the install, then moved each kernel back to /boot, one by one, and uninstalled them via apt-get, just to ensure that apt-get knows they were uninstalled.

Its a really annoying thing with apt-get that theres no way to tell it to stop trying to complete an installation.

---

### Post by darkod on 2012-09-14
Well, maybe there is a way to tell it to abort but not obvious one.

On the other hand, I don't want to sound harsh, but it's your job to watch out the usage of the partitions. It looks like your /boot partition is too small, or you keep way too many old kernels without removing them. In any case, you need to watch out the usage and clean it up regularly since there is space problem.

---

