---
title: "Kernel Upgrade to 2.6.32-23-generic broke my LVM, RAID and GRUB"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by atwskris on 2010-07-04
Hi, 

I recently updated the kernel to the newest version(2.6.32-23-generic) using the update manager and now I am unable to boot in to my Lucid installation. 

My setup is LVM on top of a RAID 0 array. My computer had been running in this configuration since Lucid was  released.

The Error Code I get on Boot is to the effect of:  /dev/mapper/ubuntu-os is not available.. and then I get kicked in to Busy Box. 

Once in Busy Box if I try to use mdadm to mount the RAID array I get this error:

CREATE user root not found
CREATE group disk not found

If I boot in to the live CD I can mount all of the partitions and LVM  volumes, so it does not appear to be a failed drive or volume.

I have looked in the mdadm.conf, lvm config and grub config files and searched the "Google" for an answer with no-avail...

Ultimately I would like to find a solution which doesn't involve a re-installation. ;)
I am not sure what additional information would be required from me, so please ask.

Any help (or direction) would be appreciated.
Thanks!

---

### Post by atwskris on 2010-07-04
Update..

Well it appears that the newest Kernel(2.6.32-23-generic) is the issue. 

After uninstalling the newest Kernel(2.6.32-23-generic) back to Kernel (2.6-32-22-generic) everything was back to where I left off and I am able to boot back in.

It really seems far-out that a kernel update would be neglecting something like LVM, or RAID in a new release. 

Guess I won't be updating for a couple versions...
Well off to Launchpad, hopefully this helps someone else in this situation.

K

---

### Post by surfer on 2010-07-06
same problem here!

...any suggestions?

i suspect there is a problem in the initrd. ...not confirmed!

---

### Post by ACupOfCoffee on 2010-07-06
You're not alone. After upgrading I got "Error 16: Inconsistent filesystem structure". I have no RAID setup. I see that GRUB was messed up for you. It wasn't for me.

---

### Post by atwskris on 2010-07-06
Here is my bug report to Launchpad confirmed there as well... 
Make sure you add that you are effected!

[https://bugs.launchpad.net/ubuntu/+bug/601740](https://bugs.launchpad.net/ubuntu/+bug/601740)

K

---

### Post by alexdodo on 2010-07-09
Hi,
today I experienced the same problem as you: I upgraded from 9.10 to 10.04, and while performing the first boot after the upgrade, I was no more able to mount my raid-1 (LVM) devices.
The only way I found to quickly solve the problem (and let my raid devices to be mounted again) was to go back to my old kernel (2.6.31-14).
Googling for some solution, I found this: [http://ubuntuforums.org/showthread.php?t=1486460](http://ubuntuforums.org/showthread.php?t=1486460), but the above solution is not good for me, perhaps because i'm using LVM (i'm not a Linux expert)!
I have an Intel i5 on a P55 Express Chipset, and I'm using the integrated SATA controller to use my SATA disks.
Any idea on how can I solve the problem?
thanks in advance!

Alessandro

---

### Post by jrrader on 2010-07-16
This kernel also does not work with my RealTek Ethernet card:

```
f@DeepThought:~$ sudo lshw | grep "Ether"
[sudo] password for f: 
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                description: Ethernet interface
                product: 3c900B-TPO Etherlink XL [Cyclone]
       description: Ethernet interface
f@DeepThought:~$ 
```

To use it I am back on the 2.6.32-22 kernel.  I just wanted to add that to this so anyone who is having an issue with this NIC will see it.  

Before I figured out the problem I had installed a secondary NIC, a very slow one from about 10 years ago...

---

