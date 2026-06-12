---
title: "Macbook Air Ubuntu 12.04 rEFIt install"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by jamesgg on 2012-04-26
Hello everyone, 

                      I been waiting for the 12.04 to become available for my first install on a macbook air 13" 2011. Downloaded the amd64 version and I partitioned aside 20gb for the install which was assigned to dev/sda5. I did not assign any swap space. Install from the USB went just fine. Soon after the install I realized I couldn't boot into ubuntu (rookie mistake) so I installed rEFIt. 

Now after I select the ubuntu partition, a new penguin logo with a white background loads, and soon after I become stuck on a black screen with a " - " space that blinks for eternity. Still can't boot in.

Any tips or suggestions? 

Thank you

---

### Post by jamesgg on 2012-04-27
Update: installing GPT fdisk, and redoing the hybrid mbr seemed to help solve the problem, before this i had re-synced partitions under boot menu refit. Left Ubuntu default "splash screen" boot, as there are no problems with the gui, changing to nomodeset generates poor resolution and slow processes.

Figured someone would give some tips before i figured it out, but thanks anyway.

---

