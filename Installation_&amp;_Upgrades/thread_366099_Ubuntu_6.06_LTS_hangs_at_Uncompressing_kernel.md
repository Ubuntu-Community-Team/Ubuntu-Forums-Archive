---
title: "Ubuntu 6.06 LTS hangs at Uncompressing kernel"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by petestaar on 2007-02-20
Helle people!

I've been runing Ubuntu 6.06 on my IBM Thinkpad T40p, 1.6 Centrino, 1 Gb ram and with dual harddrive. The reason why I have a dual harddrive is, that i'm runing a dual boot with XP. Thus I've replaced the dvd-drive with a harddrive. 

The first time I installed Ubuntu I used a extern USB CD-drive, which worked perfectly. However when I'm trying to reinstall Ubuntu the install system hangs during uncompressing ther kernel. 

I've tried to use boot parameters: ''acpi=off, noapic, nolapic''. ''acpi=off'' makes the installation go a step further, but then I get a USB error like this ''usb 4-3: device descriptor read...''


Hope you can help me out

---

### Post by tgalati4 on 2007-02-22
Perhaps the disk is scratched.  Ubuntu disks have a way of getting around.

Are you trying to install Edgy?  Perhaps there is a video problem.

CD drives do fail.  Can you do a CD check and see if the ISO image is intact?  If you get a failure in the checksum then it could either be a bad disk or a failing or dirty CD drive.

Good luck

---

### Post by petestaar on 2007-03-02
Hello, and thank you for your reply. I've tried to install both 'dapper drake' and 'edgy'. The disk are brand new, and shiped out from Unbuntu. 

I've found out that there is a problem with USB support during installation in these two kernel versions. I found a solution to the problem, with the use of PXE boot. I downloaded a netboot version of 'dapper drake' from: [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz)

Afterwards I used a program called tftpd32.exe and installed it on a windows machine. My Thinkpad booted just fine from PXE, after which the installation process was a **succes**.

---

### Post by tgalati4 on 2007-03-03
That's great news, but a supreme pain in the butt for installation.  I am amazed at the great lengths people will go through to get Ubuntu on there machines!

Now that you have a working system, you can share your disks with others.

Good luck and welcome to the community.

---

