---
title: "Boot failed in my compiled kernel image"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by ezhilRaj on 2012-04-24
Hai all,

I have compiled the kernel 2.6.25 source code from [www.kernel.org.After]("http://www.kernel.org.after/") compilation ,when i am trying to boot my image(kernel image),i got below errors.

Please let me know the solution for this problem ......

Note:I followed grub.cfg and initrams steps. 

*************************************************************
Decompressing Linux ....done
Booting the kernel.
[8.326933]Cpufreq:No nForce2 chipset
mount :Mounting none on /dev Failed:No such device
udevd[62]:error getting socket:Invalid argument error initializing netlink socket
udevd[62]:error initializing netlink socket.

libudev:udev_Monitor_new_from_netlink:error gettingsocket:Invalid  argument Segmentation fault.Gave up waiting for root device,common  problems:
         -Boot args(cat /proc/cmdline)
                -check   root delay =(did the system wait long enough ?)
                -check root =(did the system wait for the right device ?)
        -missing modules (cat /proc/modules: ls /dev)
ALERT ! /dev/disk/by_uuid/33e3e/e4-131c-4e47-84ca-633a80bbec87 does not exist.Dropping to shell !

BusyBox v1.13.3(ubuntu 1:1.13.3-1ubuntu11)built-in shell(ash)
Enter 'F' help for a list of builtin commands
(initramfs)

*****************************************************************

---

