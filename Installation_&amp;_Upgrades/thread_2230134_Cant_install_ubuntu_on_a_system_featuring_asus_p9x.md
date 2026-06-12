---
title: "Cant install ubuntu on a system featuring asus p9x79 and i7 4820 k"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2014-06-17
Dear fellows

I have a system featuring motherboard: Asus P9X79  and CPU: i7 4820 k

I have a windows 8 O.S. on this computer beforehand.

I have tried to install ubuntu 12.10 on this system. But after clicking on the option: [COLOR=#ff0000]Install ubuntu[/COLOR] and then telling the system to install ubuntu along the windows 8 which is on the system beforehand, the system comes out of the installation process and ejects the installation DVD of ubuntu.

On the Monitor I have:

   > Acpid=exiting Speech-dispatcher disabled, edit/etc/default/speech-dispatcher
  *asking all remaining processes to terminate

Would somebody PLZ hint me what is the problem?

   Regards
    Bobi

---

### Post by Bucky Ball on 2014-06-17
Don't go there. 12.10 is no longer supported. Try 12.04 or 14.04. Thanks.

Please refer to this:

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Feel free to post a new thread if you have any problems installing a supported release. Good luck. ;)

*Thread closed.*

---

### Post by oldfred on 2014-06-17
Since new Haswell processor better to use 14.04 as Intel has made improvements to kernel, support software & video driver that is now only in 14.04 and further improvements will be in future releases. Some are testing newer kernels i 14.04.

A different model X79 system:
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset

Are you installing in BIOS or UEFI boot mode?

---

