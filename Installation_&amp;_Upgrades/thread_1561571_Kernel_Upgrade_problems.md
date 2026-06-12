---
title: "Kernel Upgrade problems"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by lor on 2010-08-26
Hi, I am new to this forum and very new to Linux!
 
I have a Cloud server that comes pre-configured with Ubuntu 8.04 LTS, I tried to upgrade directly to 10.04 LTS keeping all the existing configs but the server would not boot (or it booted but with no ssh access) so I had to do a remote format back to 8.04 LTS.
 
Next tried to upgrade to 10.04LTS again but this time accepted the new configs (so it would select the right kernel ) but had the same problem again.
 
Back to 8.04 LTS and this time tried an incremental upgrade. To cut the story short, if I always select the existing configs I can get as far as version 9.1. It never uses any of the new kernels, just keeps the same one it had for 8.04 LTS which is 2.6.27.39-20091124a . If at any time in the upgrade process I try to use the new installed kernal it will not start.
 
Going above 9.1 will not work with either 2.6.27.39-20091124a or any of the server version kernels.
 
I thought it was possible to go straight from 8.04 LTS to 10.04 LTS but seems it does not work for me.
 
I have never heard of the kernel my server is using! I thought it should have one of the server versions and I am surprised that the kernel from 8.04 lLTS is working on 9.1
 
Can any one please help me upgrade to 10.04 LTS with a newer kernel.
 
Thanks
 
Chris

---

