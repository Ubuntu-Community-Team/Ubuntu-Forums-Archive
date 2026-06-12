---
title: "Ubuntu boots _sloooowly_"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by niigatapeter on 2005-07-20
I installed the Hoary Hedgehog with dualboot on my computer a couple of months ago, and although I like it works very well, it is a bit slow. Once it's loaded, Ubuntu is only slightly slower than Windows XP on my computer, but when it comes to booting, it takes more than twice the time to boot Ubuntu, than XP. 

My computer isn't exactly new; actually it's an old laptop (P3 700  196MB), so I don't expect any amazing speeds. What surprises though, is the results compared to XP's.  I've managed to  configure Windows so that it boots in less than a minute.   Ubuntu on the other hands takes more than two minutes, which makes me choose Windows XP at the dual-boot  menu, most of the time. 

I've tried a lot of things to configure Ubuntu to boot faster, but it just doesn't work.  Does anybody have any tips?  I read somewhere that compiling a new kernel might be a good idea, but I'm not really sure how to do.

Any ideas anyone?

Thanks!

---

### Post by dmsynck on 2005-07-20
[QUOTE=niigatapeter]I installed the Hoary Hedgehog with dualboot on my computer a couple of months ago, and although I like it works very well, it is a bit slow. Once it's loaded, Ubuntu is only slightly slower than Windows XP on my computer, but when it comes to booting, it takes more than twice the time to boot Ubuntu, than XP. 

My computer isn't exactly new; actually it's an old laptop (P3 700  196MB), so I don't expect any amazing speeds. What surprises though, is the results compared to XP's.  I've managed to  configure Windows so that it boots in less than a minute.   Ubuntu on the other hands takes more than two minutes, which makes me choose Windows XP at the dual-boot  menu, most of the time. 

I've tried a lot of things to configure Ubuntu to boot faster, but it just doesn't work.  Does anybody have any tips?  I read somewhere that compiling a new kernel might be a good idea, but I'm not really sure how to do.

Any ideas anyone?

Thanks![/QUOTE]
 Hi there, 

Rather than trying to recompile a new kernel, you might try installing the 686 optimized kernel through Synaptic. I believe the package name is linux-image-686 or something along those lines. Try that and if it does not help your problem, maybe there is a service trying to startup that is misconfigured and causing the system to halt while the service tries to initialize.
Hope this helps and good luck.

---

### Post by niigatapeter on 2005-07-23
The new 686 Kernel unfortunately didn't make any difference for the boot time. What's the best way to know if a service doesn't work properly? Is there some log I could check?  Ubuntu might just be too new for my computer. Maybe I should try to install something from its time, such as Red Hat 7... To bad if that's the case, because I really like Ubuntu. Is there anything else that I could do to speed up the whole thing?

Thanks

---

### Post by dmsynck on 2005-07-24
[QUOTE=niigatapeter]The new 686 Kernel unfortunately didn't make any difference for the boot time. What's the best way to know if a service doesn't work properly? Is there some log I could check?  Ubuntu might just be too new for my computer. Maybe I should try to install something from its time, such as Red Hat 7... To bad if that's the case, because I really like Ubuntu. Is there anything else that I could do to speed up the whole thing?

Thanks[/QUOTE]
 You might try the  dmesg command (kernel log) or looking into either /var/log/messages or /var/log/syslog. Also watch carefully as system boots up to see if any services show "failed" as they try to startup. I am far from a unix/linux expert, so I hope that this helps you.

---

