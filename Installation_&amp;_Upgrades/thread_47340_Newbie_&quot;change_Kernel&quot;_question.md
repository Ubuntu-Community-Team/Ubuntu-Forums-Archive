---
title: "Newbie &quot;change Kernel&quot; question"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by pingp on 2005-07-08
Hi, all
I installed Ubuntu with Kernel 2.5.10-5 AMD64 version(I have a A64 Notebook), but I can not got the Cisco VPN Client built on 64bit plattform, and the JDK 1.5.0 64bit and Eclipse 3.01 64bit crashed again and again.
So i have to change Kernel, I deleted the partition(/) and reinstalled Ubuntu. During the there is no chance to chose Kernel, the old kernel would be used again?!

My Question is:
1 Which Kernel should I use, 686?
2 How can I change Kernel (or reinstall with other Kernel)

I am a newbie, sorry for this question.

---

### Post by tread on 2005-07-08
Fire up Synaptic
System->Administration->Synaptic
Search for linux-image, you should get a few kernel options.
Also, if your setup requires modules from the restricted section, search for and choose the appropriate version.

---

### Post by pingp on 2005-07-08
[QUOTE=tread]Fire up Synaptic
System->Administration->Synaptic
Search for linux-image, you should get a few kernel options.
Also, if your setup requires modules from the restricted section, search for and choose the appropriate version.[/QUOTE]

Thanx alot, i have searched in Synaptic with "LINUX", but only got some kernel for AMD64,K8 or X86_64, no package for 686 or 386.

---

### Post by pingp on 2005-07-08
help!

---

### Post by daniel2501 on 2005-07-08
Make sure all your repositories are enabled.
Go to [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories) if you're not sure how.

---

