---
title: "&quot;Fixing recursive fault, but reboot is needed&quot;: error after upgrading to 16.10"
date: 2016-11-24
forum: Installation &amp; Upgrades
---

### Post by renato.a on 2016-11-24
Hello all:

My computer worked flawlessly with Xenial. After I upgraded to 16.10 I simply cannot boot with the new kernel. I always get stuck with the error:
"Fixing recursive fault, but reboot is needed".
If I choose the old 16.04 kernel option at grub menu, the system boots without problems.
Any ideas about what is going wrong?
The system configuration is:
- DX-580G Intel mobo
- Core i7 960 processor.
- 5x2G Kingston DDR3 memory sticks 
- 2 Sata WD HDs.
- Nvidia 9800GT, 2G viedeocard.

Thanks in advance.

---

### Post by DuckHook on 2016-11-25
Welcome to the forums renato.a

Do you need 16.10 for a particular reason, like an app or a device that isn't supported in Xenial? Some users new to the 'buntus do not realize that Xenial, being LTS, is supported for 5 years and is meant for general users who value stability over the bleeding edge, whereas 16.10, being non-LTS, is only supported for 9 months and is meant for power users or others who must have only the latest kernel/drivers. Being on the cutting edge means less stability and possibly regressions that will affect your performance/usability.

If you must use 16.10, then logs are always a good place to look. The unsuccessful boots may still generate log entries in syslog and kern.log.

Sorry, I'm on the road for the next few days and have no access to my resources and help database that are at home, but review your logs for helpful hints. Post back to this thread any errors or odd looking entries for others who may be able to help.

---

### Post by renato.a on 2016-11-28
Thanks for your reply **DuckHook:**

I decided to follow your shrewd advice. I do not need  experiencing the bleeding edge, either in software or system resources. However, I was surprised at 16.10 installation failure: from Ubuntu 8.x up to now, I've never had any trouble regarding upgrading the system. 
I decided to reformat the HD and perform a 16.04 fresh installation. 

Thanks again.

---

