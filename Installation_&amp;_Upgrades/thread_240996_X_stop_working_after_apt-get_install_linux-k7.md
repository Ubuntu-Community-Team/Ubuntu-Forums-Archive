---
title: "X stop working after apt-get install linux-k7"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by phabulosa on 2006-08-21
I did
"apt-get install linux-k7"

to improve the performace of my laptop (HP L2000/Compaq V2000)

I was using i386 kernel and everything was working perfectly.

However, after I did this kernel upgrade, X stop working.

I am wondering what's going on and how to fix this problem.

Thanks a lot!

---

### Post by avtolle on 2006-08-21
What video card are you using, and did you install the drivers for it on your earlier kernel? Please be aware that when one changes kernels, it is necessary to reinstall video drivers if that was required before. Hope this helps.

---

### Post by meng on 2006-08-21
Have you tried logging into console mode and
sudo dpkg-reconfigure xserver-xorg
?

---

### Post by phabulosa on 2006-08-21
> **avtolle said:**
> What video card are you using, and did you install the drivers for it on your earlier kernel? Please be aware that when one changes kernels, it is necessary to reinstall video drivers if that was required before. Hope this helps.

I was using xorg-driver-fglrx. 
Thanks!

---

### Post by phabulosa on 2006-08-21
> **phabulosa said:**
> I did
"apt-get install linux-k7"

to improve the performace of my laptop (HP L2000/Compaq V2000)

I was using i386 kernel and everything was working perfectly.

However, after I did this kernel upgrade, X stop working.

I am wondering what's going on and how to fix this problem.

Thanks a lot!

I can fix this issue by 

apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

because some people are reporting their X also broke after system update.

I am not sure the real reason behind this problem and I am hoping for some expert give me an answer

Thanks:KS

---

### Post by cnhzcy14 on 2006-08-22
Not just for k7, all the ubuntu are broken!

---

