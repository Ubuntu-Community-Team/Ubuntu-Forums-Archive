---
title: "Nvidia 190.53 driver install help"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by yomnym on 2010-03-10
I currently have installed the hardware driver for my nvidia card that installed  automatically when i installed the my 9.10 OS, i just wanted to install the latest one from the Nvidia website which are the 190.53 and the ones i have are version 185.  I downloaded the file from Nvidia website with the following name "NVIDIA-Linux-x86_64-190.53-pkg2.run" but when i double click it i get the following error.  Im sure i'm doing something wrong here, just wanted to see what you guys recommend doing.  Thanks

---

### Post by cgb on 2010-03-10
check out this link for information regarding driver install...

[http://ubuntuforums.org/showthread.php?t=990978]("http://ubuntuforums.org/showthread.php?t=990978")

---

### Post by yomnym on 2010-03-10
Thank you for your quick reply, i actually went added the nvidia rep
```
 sudo add-apt-repository ppa:nvidia-vdpau/ppa
```

Then went to synaptic and searched "nvidia" the latest drivers where right at the top of the results, so i removed everything that had to do with the old drivers and installed the new ones.

---

