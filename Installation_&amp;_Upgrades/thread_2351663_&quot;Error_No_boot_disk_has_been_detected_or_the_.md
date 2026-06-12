---
title: "&quot;Error: No boot disk has been detected or the boot disk failed&quot; after Boot-Repair"
date: 2017-02-05
forum: Installation &amp; Upgrades
---

### Post by luigiwriter2 on 2017-02-05
received "Error: No boot disk has been detected or the boot disk failed" after Boot-Repair.
Initial action was to change secure options in the BIOS* with no success.
The Boot Repair Paste2 is located at"

[HTTP://paste2.org/7NO4kgP6](HTTP://paste2.org/7NO4kgP6)

How I got here.
Discovered my wife's HP110-220z's dual processor too slow for the Ubuntu 16.10 Unity desktop. [finding that bit of information was a journey in itself, after not quite fixing the halting behavior with 4 gig of RAM.]

Removed windows 8 and installed Lubuntu 16.10 over Ubuntu 16.10 using Lubuntu Live, which informed that I needed to correct errors in I assume the boot partition. [It only identified the dev/sda number] 

Following an Ubuntu forum post of instructions [could have been ask.ubuntu] I Used Gparted live to remove the windows partitions, then make them data partitions. [Regret I did not see that Lunix-secure-remix was available on the same download page, or would have grabbed that! :(]

I did not move the boot partition. Gparted did not give me any error messages, and I could find no posts explaining what problem Lubuntu Live was finding in the installation process or how to correct it. Feared reformatting the boot sector as that might add to the problem.

Boot repair exited successfully.

Then received Error: No boot disk has been detected or the boot disk failed 

tried resetting various security settings in the BIOS*

Have continued to receive the error.

I'm a hardware man with 30 years experience in the computer field, so I know enough to be dangerous. My autistic leanings often lead to confusion. I appreciate all that the open-doc community is doing. Thanks in advance for your time and efforts.

---------------------
*  The American megitrends bios secure and legacy setup is very confusing.
*  Tried setting various secure options ver. 2.15.1236 enabled or un-enabled, however in one place >un-enabled actually means enabled where in a different box it means un-enabled at least as far as what I see enabled or un-enabled in the boot order menu.

---

