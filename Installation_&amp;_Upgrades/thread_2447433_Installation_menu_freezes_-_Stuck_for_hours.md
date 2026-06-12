---
title: "Installation menu freezes - Stuck for hours"
date: 2020-07-18
forum: Installation &amp; Upgrades
---

### Post by linuxboi2 on 2020-07-18
I’m currently on Windows 10 (Acer Aspire 7), but want to completely switch to Ubuntu. However, I’ve been running into a problem during installation. Namely, when in the manual partitioning menu the installation would just freeze at random points. Sometimes at the first partition, sometimes when I'm all done right before clicking “Install Now”. The mouse can be moved, the loading wheel is spinning, but nothing can be clicked. And it stays like that indefinitely.

Secure boot and fast boot are disabled. I’m on UEFI, but I still created one MBR and one GPT bootable USB and tried both a bunch of times (even redownloaded the image just in case), but this happens every time.

Note: When booting, before the installation menu, “error communicating to tpm chip” appears briefly.

Any ideas what could be causing this?

---

### Post by crip720 on 2020-07-18
Can try to make partitions before installation with gparted when trying ubuntu.  For the error can see this link,  [https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot](https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot) .  Will need to install same as Win 10, UEFI and GPT,  other ways are more troublesome.  If link does not help, can google your error for more ideas.  Install should only take about 20 minutes, any thing than 40, should cancel.

---

