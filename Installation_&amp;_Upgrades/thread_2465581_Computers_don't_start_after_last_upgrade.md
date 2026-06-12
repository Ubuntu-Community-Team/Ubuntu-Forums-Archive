---
title: "Computers don't start after last upgrade"
date: 2021-08-05
forum: Installation &amp; Upgrades
---

### Post by mippi on 2021-08-05
I have 6 PCs with Nvidia Quadro NVS 295 and I performed upgrade on all of  them on Monday. Since then they are all dead. I tried to reinstall system, but the same effect. The problem is in Nvidia driver 340. It doesn't  work with the newest kernel. Everything works perfectly fine if the driver is generic. When I install a property driver it crashes. If I update a system with driver 340 - the same effect.  Computers do not reboot. They work perfectly fine with the same driver and previous kernel. 

Can anybody know what to do with that problem? Any advice?

---

### Post by MAFoElffen on 2021-08-05
I am here now....

First do and post the results of
```
uname -r
lsb_release -a
lshw -C video
apt-cache show ubuntu-drivers-common
apt-cache show nvideo-340
```
Please post the results within tags like this: [noparse]```
 any_output_text 
```[/noparse]

---

### Post by marcw on 2021-08-08
> **mippi said:**
> I have 6 PCs with Nvidia Quadro NVS 295 and I performed upgrade on all of  them on Monday. Since then they are all dead. I tried to reinstall system, but the same effect. The problem is in Nvidia driver 340. It doesn't  work with the newest kernel. Everything works perfectly fine if the driver is generic. When I install a property driver it crashes. If I update a system with driver 340 - the same effect.  Computers do not reboot. They work perfectly fine with the same driver and previous kernel. 

Can anybody know what to do with that problem? Any advice?

I do not have any advice, just a me-too.  My two older Zotacs use the NV 340.108 driver and both are having the same issue as you.  After the latest update they boot fine but don't display video, just a blank black screen with a randomly blinking cursor.  They're headless but I got into both with ssh in order to uninstall the NV driver and now both boot normally but just use the Nuveau default driver.  Unfortunately I can't use either computer like this (no NV driver).  Afterward, I tried installing the NV driver with Software-Updater but then received this warning after a few minutes:

Error while applying changes
pk-client-error-quark: Error while installing package: installed nvidia-340 package post-installation script subprocess returned error exit status 10(313)
OK

I'm hoping the kernel guys discover their error and do something about it.

---

### Post by monkeybrain20122 on 2021-08-08
So if it is a kernel problem can you boot into the old kernel (hit esc at boot, and choose advanced option then choose the previous kernel) and then delete the new one?

---

### Post by marcw on 2021-08-08
Yes, I could always revert but since they are headless and inconveniently placed it's a pain to attach a keyboard.  And since they are (relatively) unimportant I can wait to see if there's another kernel update coming soon.

---

### Post by hk42 on 2021-08-10
I too have a problem with the latest kernel.
It doesn't seems to recognize my SD card reader and as my home directory is on a SD card I cannot boot.
Same thing on at least 2 computers.
Previous kernels and low latency one are OK

---

### Post by MAFoElffen on 2021-08-10
You still have not provided any of the info asked for in Post #2... Which would give information related to the what and why not's... Just saying more information needed.

In the past, (being an avid NVidia user over the past 20 years) when a Kernel updated there were some problems with NVidia drivers. Mostly because the proprietary dirver binaries needed to be recompiled with the current kernel. Since then, it now has scripts so that things get reconpiled with DKMS during a Kernel update... Although sometimes...

Like I said, just trying to help.

---

### Post by marcw on 2021-08-10
It appears there really is an issue with the latest kernel upgrade and the nvidia 340 driver.  I submitted my issue to Launchpad and it was confirmed and turned in a duplicate of a case that affects 45 other people.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1938978](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1938978)

---

### Post by MAFoElffen on 2021-08-10
Very good to know. Now I can follow that and see that how goes... 

Thank you very much for posting that.

---

