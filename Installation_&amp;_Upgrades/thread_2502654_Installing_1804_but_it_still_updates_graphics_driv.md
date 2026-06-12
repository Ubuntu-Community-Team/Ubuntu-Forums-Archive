---
title: "Installing 1804 but it still updates graphics drivers"
date: 2024-11-23
forum: Installation &amp; Upgrades
---

### Post by kezzy19661966 on 2024-11-23
I have an old Sony Vaio laptop that has a Radion HD3470 graphics chip. If it is upgraded past 18.04 the display 'shakes'.

I understand that this chip was dropped from the kernel after 18.04(.02?)

I thought that if I installed Ubuntu and registered with Ubuntu Pro it would only update the security and presumed the graphics would be left as is. 
I enabled Livepatch when I installed it

From terminal, I sudo pro attach but I have some services  showing disabled:


sudo pro status
SERVICE   ENTITLED  STATUS       DESCRIPTION
cc-eal            yes       disabled     Common Criteria EAL2 Provisioning Packages
cis                  yes       disabled     Security compliance and audit tools
esm-apps      yes       enabled      Expanded Security Maintenance for Applications
esm-infra        yes       enabled      Expanded Security Maintenance for Infrastructure
fips                yes       disabled     NIST-certified FIPS crypto packages
fips-updates   yes       disabled     FIPS compliant crypto packages with stable security updates

**livepatch        yes       warning      Current kernel is not covered by livepatch**

ros                 yes       disabled     Security Updates for the Robot Operating System
ros-updates   yes       disabled     All Updates for the Robot Operating System

so quite a few services disabled and livepatch not working.

So when I do run the updates, the graphics part is upgraded and the display brakes. 

Any suggestions how to solve this ?

Post add:
I typed $ uname -r
and get 
4.18.0-15-generic

Does that mean I am NOT on the LTS version and not covered by ubuntu pro ?

I typed $  hostnamectl 

and got back:
   Static hostname: k-VGN-SR19VN
    Icon name: computer-laptop
    Chassis: laptop
    Machine ID: 616676546e464ac6b6a28d04eac0d08
    Boot ID: 70ce2605309d46e38f25631916b6b878
    Operating System: Ubuntu 18.04.2 LTS
    Kernel: Linux 4.18.0-15-generic
    Architecture: x86-64

---

### Post by deadflowr on 2024-11-23
the 4.18 kernel was what came with the 18.04.2 point release.
It's the hwe stack that 18.04.2 used which was the kernel series used for the 18.10 release.
That kernel hit end of life when 18.04.3 came out ( which itself used the 19.04 kernel stack).

Prior to 22.04, livepatch only supported the original kernel stack or the last hwe stack which was the stack used from the next LTS.
(Or that's how I remember it working, maybe it was different)


That non-sense said,
you should still be able to get the livepatch working by downgrading the kernel to the original kernel stack for 18.04.
```
sudo apt install linux-generic
```
reboot and at the GRUB boot selection screen go to the Advanced options and toggle to the entry for the 4.15 kernel. ( I think that's the original kernel stack series for 18.04)
Once in that kernel run uname to double check and then proceed to remove the hwe kernel stack

Command to remove should be
```
sudo apt purge linux-image-generic-hwe-18.04 linux-headers-generic-hwe-18.04 linux-generic-hwe-18.04 linux-image-4.18.0-15-generic linux-headers-4.18.0-15-generic
```

Ubuntu kernel HWE ref: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

