---
title: "Dual boot in UEFI Ubuntu with Windows 8.1 with Bitlocker encryption"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by guillaume_dsde on 2015-03-13
Hi everyone i've decided I want to switch to Linux, but keep windows on the sidelines for Gaming.
I have a SAMSUNG 840 EVO 256GB encrypted using Samsung's Drive encryption through Bitlocker with a TPM module
In addition my Windows 8.1 x64 Pro boots in UEFI, and UEFI only (no CSM compatibility settings enabled+full secure boot)
I would like to dual boot Ubuntu with Windows, how can I go about this?

Thank you in advance :)

---

### Post by oldfred on 2015-03-13
I had never heard of TPM until I read this. And none of the current Ubuntu distributions use that new of a kernel yet.

[http://www.phoronix.com/scan.php?page=news_item&px=Linux-3.20-TPM-2.0-Security](http://www.phoronix.com/scan.php?page=news_item&px=Linux-3.20-TPM-2.0-Security)

I believe 3.2 is the one renamed to 4.0 kernel. You may be able to install the newest version of Ubuntu and then use a ppa to update to the very newest kernel. But not sure if you can even install without new kernel??

---

### Post by guillaume_dsde on 2015-03-14
Thanks for the answer, its fine, my TPM module is a TPM version 1.2 not 2.0. TPM shouldn't cause any issues because ubuntu won't be using it, it is just used to boot into encrypted Windows, but I was wondering wether it is possible to install Ubuntu on the same encrypted drive as Windows

---

### Post by oldfred on 2015-03-14
Does the TPM restrict what you can even boot? 
Can you select flash drive & boot live mode Ubuntu installer?

---

