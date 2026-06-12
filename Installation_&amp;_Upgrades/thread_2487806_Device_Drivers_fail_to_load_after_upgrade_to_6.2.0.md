---
title: "Device Drivers fail to load after upgrade to 6.2.0-1003-oracle"
date: 2023-06-15
forum: Installation &amp; Upgrades
---

### Post by phil_hood on 2023-06-15
Yesterday I ran a regular update to my Ubuntu 23.04 laptop.  This resulted in kernel 6.2.0-1003-oracle being installed.  Several device drivers failed to load afterwards including those for  NVidia drivers and Realtek Network.  Rebooting under the previous kernel 6.2.0-20-generic works just fine.  Looks like something broke in that kernel upgrade.

---

### Post by phil_hood on 2023-06-15
I have temporarily resolved this by removing the oracle kernel (apt remove linux_image_6.2.0-1003-oracle) which tried to replace it with an unsigned version of the oracle image which I also had to remove (apt remove linux_image_6.2.0-1003-unsigned-oracle).  Now everything boots up in the low latency version of the image and works fine.  Not sure why it installed the oracle version to begin with.

---

### Post by tln7 on 2023-06-15
This occured for me as well. This seems to be something that keeps hitting people unexpectedly, according to the trails it leaves in various forums and other sites.

Perhaps one clue is that this might have been installed, in my case, through manual use of the Ubuntu Updater. I recall changing the Ubuntu Software & Updates->Updates->"Subscribed to:" option to "All Updates" a while ago. Setting back to "Security and recommended updates" appears to exhibit better behavior in sticking to "generic" over "oracle".

---

### Post by claytonwramsey on 2023-06-15
I made an account just to say this too. I (naively?) just let Software Updater do its thing. Notably, as tln7 says, it was set to "All Updates." The update this morning broke all of my drivers :(. I "fixed" it so far by rolling back to 6.20.0-20-generic.

---

### Post by phil_hood on 2023-06-15
Thanks for the tip! I have changed to Security and recommended updates.  Fingers crossed.....

---

