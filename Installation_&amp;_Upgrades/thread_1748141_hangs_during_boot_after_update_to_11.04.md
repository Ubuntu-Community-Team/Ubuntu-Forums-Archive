---
title: "hangs during boot after update to 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Zaney Zebra on 2011-05-03
My GRUB is at v1.5 and have just updated UBUNTU to 11.04 from 10.10 I have a AMD processor and am using the 64 bit version of UBUNTU

The system will not start normally, it will hang. with this on the screen

Boot from (hd0,0) ext3 9a590bb3-d88b-40e5-8e48-46c83c0865dd
Starting up ...

I have discovered a way to boot I select the recovery mode then I select failsafeX , next I select restartX . And the system will boot,

I am looking for guidance on what to do to get my system to boot normally without having to use the workaround that I now use,

---

### Post by andrewcow on 2011-05-03
Thanks so much for this fix:) I am having the same problem but and would also love a permanent fix:)

---

### Post by andrewcow on 2011-05-03
Wait I am working again:) I an running Ubuntu in a Virtual Box so I logged in using the FailsafeX method, updated everything and when I restarted, it worked.:)

---

### Post by Zaney Zebra on 2011-05-04
Update, 

I've installed a second HDD in the machine and did a fresh install of 11.04 on it, now upon startup with grub 1.99 I can select the original hdd and OS and the system boot with out issue. 

So I suspect that my problem may be with grub 1.5 :confused:

---

