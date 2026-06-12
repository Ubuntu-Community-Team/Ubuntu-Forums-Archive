---
title: "PXE boot into RAM"
date: 2021-09-03
forum: Installation &amp; Upgrades
---

### Post by wrender2 on 2021-09-03
I'm trying to setup a bunch of servers to pxe boot Ubuntu fully into RAM (No hard drives), and run software fully in memory.  I'm following the instructions here:  [https://itectec.com/ubuntu/ubuntu-automated-20-04-server-installation-using-pxe-and-live-server-image/](https://itectec.com/ubuntu/ubuntu-automated-20-04-server-installation-using-pxe-and-live-server-image/).  So far my ipxe boot process works fine, and loads onto a server without a hard disk, but it just boots to the Installer screen (where it asks to select language, network settings etc...).

My current ipxe boot file looks like this:
```

#!ipxe

set base http://192.168.1.142/tftp

kernel ${base}/vmlinuz initrd=initrd.img url=http://192.168.1.142/tftp/ubuntu-20.04-live-server-amd64.iso autoinstall ds="nocloud-net;s=http://192.168.1.142/tftp/" root=/dev/ram0 cloud-config-url=/dev/null ip=dhcp
initrd ${base}/initrd
boot

```

I just have a few basic questions that someone familiar with Ubuntu could probably answer:

1.  Is it possible to ipxe boot Ubuntu fully into RAM using the ubuntu-20.04-live-server-amd64.iso image, or do I need to create a custom iso somehow?
2.  I've come across cloud images at: [https://cloud-images.ubuntu.com/focal/current/](https://cloud-images.ubuntu.com/focal/current/)  , but just a bit confused on how I could boot these in a private cloud. Is there any documentation or example ipxe files?
3.  Is cloud-init compatible with booting a server fully into ram and configuring it in RAM?

---

### Post by grahammechanical on 2021-09-03
My understanding (which is very limited) of Preboot Execution Environment (PXE) that it allows installation of an operating system over a network. I think it makes it possible for an IT administrator to install or re-install an OS without being physically present using the target machine. I may be wrong about this. So, I do not think that PXE is meant for installing an OS onto a machine without some kind of storage device.

It is possible to run an OS in a RAM disc but I guess that some storage would be needed to hold and run the initial part of the OS that needs to load to create the RAM disc from which the OS runs from. If you get my meaning.

[https://askubuntu.com/questions/1212390/how-would-i-run-my-system-solely-in-a-ramdisk-after-logging-in-or-optionally-on](https://askubuntu.com/questions/1212390/how-would-i-run-my-system-solely-in-a-ramdisk-after-logging-in-or-optionally-on)

Without any on machine storage it seems to me that the machine would become a dumb terminal running an OS on another machine over the network. Which is where computing was before IBM invented the Personal Computer.

Regards

---

### Post by Tadaen_Sylvermane on 2021-09-03
Go to [https://ltsp.org/](https://ltsp.org/) 

This automates damn near the whole process. I gave up trying to piece it together myself long time ago and found this. It works quite well, even full desktops. Is just a bunch of shell scripts and some python so you can look at them if you wish to see how it works.

---

### Post by wrender2 on 2021-09-03
Thanks. Tadaen. Looks interesting. I'll check it out over the weekend.

---

