---
title: "Unable to create the installation CD!"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by mekondelta on 2008-04-24
I've been trying to install 8.04 RC and can't seem to create the CD without errors. I've tried with several burners on the same PC. I always get 1 error when checking the CD via the Ubuntu install checker on the CD. I can work my way through the install screens but the installer stops about half way through and says there is an error and prompts me to abort the installation.

I find it weird that I get the same error on multiple CDs that I have tried to write the ISO file to. I'm using an 800MB CD and I believe it's a 700MB cd that the ISO is designed for. Is this the problem?

Any help appreciated. I'll try again when 8.04 is released but I'm getting a bit sick of all these coasters! :-)

---

### Post by iaculallad on 2008-04-24
Try lowering your write speed to 2x or 4x (try also to check its md5 hash). if all else fails, try downloading  and burning the alternate CD.

---

### Post by mekondelta on 2008-04-24
> **iaculallad said:**
> Try lowering your write speed to 2x or 4x. if all else fails, try downloading  and burning the alternate CD.
Thanks. I tried burning at 2x and 10x. Same result. Can I get the same installation of Ubuntu from the alternate CD as the original one?

---

### Post by iaculallad on 2008-04-24
Definitely, you could get the same installation.

---

### Post by mekondelta on 2008-04-25
I solved my problem. I was using the DownThemAll Firefox plugin to download the ISO file. For some reason DownThemAll was corrupting the ISO file but not reporting any error. So although the file size was correct, the MD5 checksum was wrong. Did a conventional (slower!) download and all is fine. Look forward to installing this finally!

---

