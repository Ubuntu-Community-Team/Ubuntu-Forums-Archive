---
title: "Problem While Installing Ubuntu 10.04 Lucid Lynx"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Nosophorus on 2011-01-04
Hi!

I am a 8.04 user and I am willing to upgrade to 10.04 but during the install I got the following error message:

**ubi-language failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.**

Is there something I could do?

Thank you!

---

### Post by nomko on 2011-01-04
My advise: never upgrade an existing system. Always do a fresh/clean install! Only by that you can avoid a lot of trouble. I think that the new installation runs into some problems. Some conflict between the older version and newer version.
 
Best thing to do: like i mentioned above. Do a fresh/clean installation. Backup your files and remove 8.04 completly. You can do thius during the installation of 10.04 when you enter the partition manager. There you can simply remove the partiotion which contains 8.04 (mostly partition /dev/sda1)

---

### Post by Nosophorus on 2011-01-04
Hi!

Thank you for your reply.

I tried to do a clean installations and the same problem happened. . .

The same error message appeared again and the same problems.

Thank you!

---

### Post by nomko on 2011-01-04
So, its got nothing to do with 8.04 then??
 
When you did a complete clean/fresh installation, did you removed the partition containing the 8.04 installation??

---

### Post by Nosophorus on 2011-01-04
Hi!

Thank you for your reply.

> When you did a complete clean/fresh installation, did you removed the partition containing the 8.04 installation??

I tried to install from the CD-ROM. I restarted my computer and booted it from the CD-ROM. When the screen with a keyboard and a human showed up, I pressed any key and tried to install from there, but those aforementioned error messages appeared again.

When I moved from Ubuntu 7.10 to 8.04 I did not need to remove the previous Ubuntu install (7.10), since 8.04 overwritten it and I can't understand why 10.04 is not doing the same.

Thank you!

---

### Post by nomko on 2011-01-04
Normally it shouldn't give any problems. But what can cause problems are settings used by the older version which might conflict with files from the newer version. So, therefore i advisedyou to do a fresh/clean installation. And also when i read this: ***.....Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken..... ***there's a high risk of ending up with a new installatuion which is completly crappy. 
 
I always remove partitions with a live-cd of Gparted before installing a new version of Ubuntu and it never gave me any problems.

---

### Post by Nosophorus on 2011-01-04
Hi!

Thank you for your reply!

I'll try what you suggested and see if it works. If not, I'll come back here.

Thank you!

---

### Post by nomko on 2011-01-04
> **Nosophorus said:**
> Hi!
 
Thank you for your reply!
 
I'll try what you suggested and see if it works. If no, I'll come back here.
 
Thank you!
 
And i'll be here to help you again!

---

### Post by Nosophorus on 2011-01-04
Hi! 

I finally could install Ubuntu 10.04 here. The problem was the CD I used to burn Ubuntu. I first used an Imation CD-R and when I tried to install Ubuntu, it simply did not work! Then I burned a Nipponic CD-R and the installation flowed swiftly.

It is strange because during the burning process no error message was issued or something like that. The fact is that I shall not use Imation CDs to burn a Ubuntu ISO again.

By the way, thank you very much for your kind replies and support! That's the soul and essence of Ubuntu's community!

See You!

Thank You!

---

