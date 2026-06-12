---
title: "The famous kernel panic when upgrading kernel"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by power_cut on 2005-04-26
Hello,

When I upgrade the kernel (to 2.6.10-5 for example) and reboot, I have a kernel panic. (like many people it seems)
I tried to debug this by mounting initrd and compare the file loadmodules in the kernel 2.6.10-4 initrd and kernel 2.6.10-5 initrd. There is no big differences. I tried to add some modules related to my Sata disks, without success.  

I read that there is some tricks to debug this, by adding commands in initrd scripts in order to print debug informations at boot time, during loading the initrd image. 

So my question is : what can we do to debug the initrd ? I think this will be useful for everybody having this problem. 

Regards

---

