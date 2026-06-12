---
title: "Adaptec 1430SA driver trouble"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by sig313 on 2007-08-09
I have trouble getting Ubuntu Server to work with Adaptec 1430SA SATA controller. Seems I have to compile the kernel with the new driver. I'm using files from here: [http://www.adaptec.com/en-US/support/raid/sataii/AAR-1430SA/]("http://www.adaptec.com/en-US/support/raid/sataii/AAR-1430SA/")
and the how-to guide here: [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

I've no problem with step 1-3 from howtoforge.com (except I haven't done step 1.1), I assume step 4 isn't applicable for me. Step 5 also goes well, I make no changes in the kernel configuration.

I extract the driver, and execute the Build command according to the instructions provided with the driver by Adaptec. However, this is where things start to go bad. 

I get the error message: "cp: cannot stat 'usr/src/adaptec/shipped-binary/host_raid.o.aar81xx.unknown.4.1.2': No such file or directory". I can't find that file in any directory. I can however select the controller in the kernel configuration (make menuconfig), though when I try to compile the kernel, it stops and I get errors when it gets to my controller  (drivers/scsi/aar81xx).

I'm new to Linux, I've just built an (home) file server that is going to replace a Windows file server. I would rather not have to use Windows on this new computer as well, so please help me :)

---

### Post by sig313 on 2007-08-18
Anyone? I would really like to get the Adaptec controller to work.

---

