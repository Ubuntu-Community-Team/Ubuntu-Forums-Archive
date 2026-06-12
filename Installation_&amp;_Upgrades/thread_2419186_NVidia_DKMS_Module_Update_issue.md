---
title: "NVidia DKMS Module Update issue"
date: 2019-05-17
forum: Installation &amp; Upgrades
---

### Post by affenmaster02 on 2019-05-17
So,

I just started my PC today - and noticed that my NVidia Driver wasnt loading.

I figured out that it was an Kernel Update - on which DKMS tried to load the NVidia Module again, but failed.

ATM I have removed the old Nvidia driver version and installed a new one with Ignoring the CC check - as this seemed to be the error - 

Still the problem remains, as i will have the problem again on the next kernel update, cause DKMS cant load the module into the kernel.

in the log this seems to be the main Issue: 

```
Compiler version check failed:


The major and minor number of the compiler used to
compile the kernel:


gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)


does not match the compiler used here:


cc (Ubuntu 7.4.0-1ubuntu1~18.04) 7.4.0




```


I cannot downgrade gcc-7-base to the needed version as it would remove everything else too, like DMKS itself, xubuntu-core, xubuntu-desktop, ...

I have the newest driver 430.14 downloaded and ready for reinstall, i just need to find a way to use the older gcc version...

Also i cannot remember an incident where i may have messed with my compiler settings as i dont compile programs myself.

I'm open for any help :D 

THX 
Bastian

---

### Post by ubfan1 on 2019-05-17
No one's posted a solution to this problem yet: [https://askubuntu.com/questions/1139364/nvidia-installer-fails-when-upgrading-kernel](https://askubuntu.com/questions/1139364/nvidia-installer-fails-when-upgrading-kernel)
(other than your ignoring the CC check on each kernel update).

---

### Post by affenmaster02 on 2019-05-18
oh okay , well - seems like i need to wait for the next kernel - they'll probably compile it with the new version then

i have filed a launchpad bug report for this issue 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1829598](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1829598)

if it affects you too, add in there

---

