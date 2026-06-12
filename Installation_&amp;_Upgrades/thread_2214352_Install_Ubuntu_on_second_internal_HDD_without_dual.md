---
title: "Install Ubuntu on second internal HDD without dual-booting?"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by emurselovic on 2014-03-31
Hi there,

Sorry if the title doesn't make perfect sense, I'll try to elaborate and clarify:

I would like to buy a second internal hard drive for my desktop, and install Ubuntu (and possibly other distros in the future) on that hard drive, but I want to do so without affecting the regular boot-up for the PC. That is to say, I would like the PC to automatically boot into Windows without ever running into a bootloader or even being able to access that secondary drive at all through windows. I want to basically only be able to boot up Ubuntu by entering the boot menu manually on a restart/boot and choosing to boot from the secondary drive.

So an example would be:

C:\ 1TB Internal w/ Windows 7, boots automatically when PC is turned on, and is unable to access files on D:\
D:\ 1TB Internal w/ Ubuntu and/or other linux distros, boots only when one enters advanced boot settings when turning on a computer and manually choosing to boot from that drive.

Thank you very much in advance for any help anyone can offer with this.

---

### Post by oldfred on 2014-03-31
Windows does not see Linux partitions, so that should not be an issue. Ubuntu will see the Windows partitions unless you specifically mount and hide them

You just have to be sure to install grub2's boot loader to the MBR of the Ubuntu drive, leaving the Windows boot loader on the Windows drive. Default installs always install grub to sda which usually is the Windows install. So you can either disconnect Windows drive or use Something else which on partition, format & select mount points screen also has a combo box for which drive to install boot loader. My install shows me overwriting an old install and combo box still shows installing to the drive that is sda.

 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

