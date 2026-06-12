---
title: "updated kernel will not boot"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by vcallas on 2010-11-28
I recently upgraded Linux kernel headers for version 2.6.35 on x86/x86_64 from 2.6.35-22 to 2.6.35-23. and my system will not reboot to the upgraded kernel. To reboot I have to force shutdown my Toshiba L-450 laptop and the restart. This brings me to the GRUB screen were I can choose to use the previous 2.6.35-22. Normally do not see the GRUB screen as I am only running Ubuntu 10.10 64 bit on this computer. I have tried reinstalling linux-headers-2.6.35-23 and linux-headers-2.6.35-23-generic and got the same result. Any ideas on what else to try

---

### Post by garvinrick4 on 2010-11-28
If -22 works use it, remove offending kernel -23 and wait for -24 to come out in Ubuntu repositories. To discover how a particular kernel does not work on a particular hardware
and driver set could drive one into a straight jacket. Good idea to keep at least 2 kernels so as to stay out of that jacket. Just an opinion.

---

### Post by phillipdhall on 2010-11-28
Thanks for your opinion. I just realized that I've wasted an hour trying to figure out how to make the new update work without even knowing what the update even is... kinda silly now that I think about it.

---

### Post by Shark_AtK12 on 2010-11-29
> **vcallas said:**
> I recently upgraded Linux kernel headers for version 2.6.35 on x86/x86_64 from 2.6.35-22 to 2.6.35-23. and my system will not reboot to the upgraded kernel. To reboot I have to force shutdown my Toshiba L-450 laptop and the restart. This brings me to the GRUB screen were I can choose to use the previous 2.6.35-22. Normally do not see the GRUB screen as I am only running Ubuntu 10.10 64 bit on this computer. I have tried reinstalling linux-headers-2.6.35-23 and linux-headers-2.6.35-23-generic and got the same result. Any ideas on what else to try

My Asus n61-jq freezes while booting the -23 kernel also. Just been using the -22 one

---

### Post by vcallas on 2010-11-30
Thanks for the replies, will keep this in mind in the future. Luckily an upgraded version of 2.6.35-23 released today and everything looks to be working fine now.

---

