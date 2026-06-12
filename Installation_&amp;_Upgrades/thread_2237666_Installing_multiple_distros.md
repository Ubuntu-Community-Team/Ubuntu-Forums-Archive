---
title: "Installing multiple distros"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by Bob_Younkin on 2014-08-03
I am taking the Linux Foundation MOOC "Introduction to Linux".  They use Ubuntu, CentOS, and Open SUSE for practice.  I only need one and I have Ubuntu loaded on my primary drive.  I have a second drive formatted into 4 partitions.  I want to install CentOS and OpenSUSE into those partitions.  Ubuntu just installed "automatically" but I don't want to corrupt that installation when I try to install the others.  Can somebody point me in the right direction? 
Bob

---

### Post by oldfred on 2014-08-03
I have not installed either CentOS or Open Suse, but have many installs of Ubuntu.
Is system BIOS or UEFI. All systems should be in same boot mode for ease of dual booting, unless wanting to experiment with UEFI.

With Ubuntu you can use gpt partitioning with BIOS or UEFI boot and change if you have efi partition or bios_grub partition. Not sure about others, but expect by now they also work with gpt. Only Windows needs gpt for UEFI boot and MBR(msdos) for BIOS boot.

It sounds like you used one of the auto install options to install Ubuntu which only gives you / (root) & swap. And if multi-booting better to have a separate data partition but owner or UID can be an issue between different distributions. Debian based systems first user is 1000, but some others have used 500.

I think it is CentOS that has a default install with separate /boot and LVM which is good for a full drive but not so good for multiple booting unless you want every install inside the LVM. Some suggest just manually installing to an ext4 partition.

So with each install best to use whatever manual options are available so you have control over partitions, formats, and where boot loader is installed. If concerned you can disconnect Ubuntu hard drive so you know it will not get corrupted. 

Of course good backups are always required before any major system change.

I would keep Ubuntu's grub in the MBR of the first drive, and let one of the other installs install to the MBR of the second drive for direct booting from BIOS or one time boot key. Generally grub2's os-prober is good at finding other installs so when rebooting into Ubuntu you can run sudo update-grub and have it find the other installs.

This is an example of Ubuntu's Something Else or manual install.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

I installed Redhat 15 years ago and while screens are prettier, basic install process has not changed much. Basically you choose type of install, keyboard, time zone, partitions (formats, mounts), user and password and install.  Some details have changed, but basic install is still Linux.

---

### Post by Rob Sayer on 2014-08-04
"... basic install is still Linux".

That's what I was thinking.  I'm not convinced that in a Linux fundamentals course you really need all those distros.  They may use some different tools, esp. for package management, but it's still Linux.  The kernel version may be different but it's still the standard linux kernel.  The architecture/topology of  the system is the same.

In fact I've used the arch linux docs a number of times for ubuntu even though many of the tools like packaging are different.

---

### Post by yancek on 2014-08-04
CentOS as of release 6.5, is still using Grub Legacy and you do have the option to select to install to a single partition, without a boot partition.  Opensuse uses Grub2 and has a lot of different options to install the bootloader which other systems don't have.  You're better off installing CentOS to the drive before Opensuse and then adding CentOS to the Opensuse grub.cfg file.  If you are going to want to boot from the Ubuntu grub2, make sure you have an Ubuntu DVD/flash drive in case you overwrite the mbr on your internal drive with Ubuntu, or disconnect it if you are really paranoid.

---

