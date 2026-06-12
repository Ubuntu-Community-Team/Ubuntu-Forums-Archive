---
title: "update kernel 3.13.0-105 fails, &quot;Hash Sum mismatch&quot;"
date: 2016-12-20
forum: Installation &amp; Upgrades
---

### Post by Xiguus on 2016-12-20
Hi all, 
I'm trying to update kernel 32-bit 3.13.0-103 to 3.13.0-105. With software Updater the update fails and I get a message "package download failed, check internet connection". Other updates are installed as usual. 
In synaptic, I get a message for linux-image-3.13.0-105-generic that "authentication failed". Other packages download successfully. Taking the option to proceed with the installation tells me 
 ```
Failed to fetch http://mirror.aarnet.edu.au/pub/ubuntu/archive/pool/main/l/linux/linux-image-3.13.0-105-generic_3.13.0-105.152_i386.deb
  Hash Sum mismatch

```
Can we fix this? 
Best Regards, 
Xiguus

---

### Post by Xiguus on 2016-12-21
Hi all,

kernel now updates, 'uname -r' confirms running kernel is 3.13.0-105, thanks to whoever recalulated hash sums, :)

BR,

Xiguus

---

