---
title: "Ubuntu not booting"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by harikrrissh on 2012-01-25
I installed Ubuntu 11.10 alongside windows xp in C drive using a Live USB flash drive. Installation went smoothly and after installation it asked to restart. I restarted and removed the flash drive. It automatically booted into XP without showing OS boot options and did all sorts of check scans and In MY COMPUTER i saw that the 7 GB i allocated to ubuntu is gone. I restarted again and it only shows XP no ubuntu boot option.

Please help !!

---

### Post by carl4926 on 2012-01-26
Use the live USB and boot up to the live desktop
Open a terminal and post the result of

```
sudo fdisk -l
```

---

### Post by nipunshakya on 2012-01-26
Ubuntu doesn't have any label as windows has(like c: or d: etc.) When u open disk management, you can see all your machine's partitions(even the ubuntu). But you don't see any label labelled in ubuntu's partitions and instead, under the 'Free' column , you see 100% of the partition is free...but the fact is, your ubuntu is right there.

Its better we see your partitions first and then suggest you anything.... type the command suggested above, copy paste your output here...

Regards,WinuxUser

---

### Post by harikrrissh on 2012-01-26
UPDATE:
Problem solved. I accidently installed GRUB to another partition:lolflag:
I booted live cd once again and clicked install, it asked whether to replace existing ubuntu and install, I clicked OK and voila everything is working !!

Its running on my netbook like a dream:p
But sometimes the temp reaches around 70 degrees !! Is that normal ??

And thanks for all the replies. Loving the community !!

---

### Post by nipunshakya on 2012-01-26
Glad to know you fixed it out....
Btw, the temperature u mentioned is optimal temperature or new machines to run..... read more info on following site if u would like:
[http://mobileoffice.about.com/od/laptopstabletpcs/f/how-to-check-laptop-temperature.htm](http://mobileoffice.about.com/od/laptopstabletpcs/f/how-to-check-laptop-temperature.htm)

Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-26
Have a happy Linuxing and safe journey ahead with your linux....

---

