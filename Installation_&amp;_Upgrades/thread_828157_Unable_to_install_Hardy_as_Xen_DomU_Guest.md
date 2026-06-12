---
title: "Unable to install Hardy as Xen DomU Guest"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by aspasiasf on 2008-06-13
Hello all,

I have googled and searched through the forums and realize that there is an issue vis a vis Hardy within the context of it being a Xen DomU guest.  I have reviewed and attempted to apply the kernel as being discussed in this following thread:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126)

and also posted this same question - wanted to try this forum too in case anyone has encountered same issues and have overcomed it:


Xen host - dom0 - Centos 5.1

I would like to install Ubuntu hardy as a domU.  The only Ubuntu
version I can install properly with no problem is dapper (6.06).

What I have done so far:

1.  Install dapper as DomU (using the virt-install Xen CLI tool)
2.  Upgrade dapper - using Ubuntu instructions to upgrade.
3.  Dapper is upgraded successfully to a kernel:  2.6.15-51-amd64-generic
4.  I tried to upgrade to 8.04 - gksu "update-manager -c"
5.  The long process completed successfully and I rebooted.
6.  Upon reboot the new kernel was stuck - and would not boot - it
seems like it is unable to load the virtual HDisks driver

7.  I found the above thread and downloaded the kernel and installed via:
dpkg -i <file>

8.  It generated the kernels:
vmlinuz-2.6.24-19-xen
and initrd image:
initrd.img-2.6.24-19-xen

9.  Attempt to boot, I am unable to successfully boot - process pauses
with the error:

"Error 13: ... unsupported executable format" ... (indicates the xen kernel) "

Any thought or suggestions would be greatly appreciated.

Regards,

aspasia.

---

### Post by SoftDux on 2008-07-27
Hey, 

Have you had any luck in getting Hardy installed as a domU guest?

---

