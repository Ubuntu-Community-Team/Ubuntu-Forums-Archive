---
title: "New machine install freezing (22.04 Server)"
date: 2023-11-26
forum: Installation &amp; Upgrades
---

### Post by pnutbutter on 2023-11-26
Hi All,

I just built a new server to run a large Plex library and a few other things, the hardware is below:

ASUS Prime H770-PLUS D4
Intel Core i7-12700K
2x 32GB Crucial Pro
Crucial 1TB NVMe
Toshiba 10TB HDD

When booting from the 22.04 Server flash drive, I get the initial options to install Ubuntu, etc. Once I click on install, it goes through it's initialization, but gets stuck about 1.5 seconds in - different places every time. I have tried:
- Using a different flash drive
- Using a new iso
- Using a different USB port (Case, MB)
- Enable/Disable secure boot
- Enable/Disable CSM
- Write in iso mode (Rufus)
- Write in DD mode (Rufus)
- Ubuntu 21.04 Server
- Using DP instead of HDMI (in case of graphics issue)

And it is all freezing. Could it be a compatibility issue? I have 20.04 running on 90% of my rack and everything works great. I can not use 20 on this config as the NIC (2.5G Realtek) does not have a driver - it fails to detect a NIC.

Is there anything else I can try?

Thank you!

---

### Post by oldfred on 2023-11-26
Have you updated UEFI firmware & NVMe firmware. Even new systems may have updates.
Are drives correctly seen in UEFI settings?
Are drives both gpt partitioned?
Often installer fails when it cannot correctly see drive/partitions.

---

### Post by pnutbutter on 2023-11-26
You know what, I was just messing around after updating the UEFI and was able to install it using the HWE option on the menu. Thanks for the recommendations!

---

### Post by MAFoElffen on 2023-11-26
If you have solved this, please visit the "Thread Tools" link in the upper giht of the page and mark your thread as "Solved" so that other may find what worked for you to solve their similar problems.

---

