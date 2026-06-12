---
title: "TPM error during installation"
date: 2017-02-21
forum: Installation &amp; Upgrades
---

### Post by rezor91 on 2017-02-21
Hello everyone! 


I have brand new Asus GL552VW-DM777T-32 and it came to me with preinstalled Windows 10. I tried to install ubuntu 16.04 as dual boot but some errors came out and i don't know how to fix them.


When i run graphics installation wizard all i can see is orange dots animation that getting stuck after a while.
When i change view to cli output i can see error like this:


[ 15. 655099] tpm_crb MSFT0101:00: can't request region for resource [mem 0xfed400080-0xfed40fff]


After that nothing more happen.


I also tried Ubuntu 16.10 but nothing changes expect that i saw two errors. tpm_crb like above and:


lwlwifi 0000:02:00.0 Unsupported splx structure


Before attempting to installation process i have disabled SecureBoot option in UEFI.
Unfortunately I couldn't find option to disable TPM module.
All attempts were made with bootable USB stick.


Is there anything that i can do to bypass this problem?

---

### Post by gordintoronto on 2017-02-21
This might help:
[http://askubuntu.com/questions/757573/installing-linux-on-rog-gl552vw-beginner](http://askubuntu.com/questions/757573/installing-linux-on-rog-gl552vw-beginner)

---

