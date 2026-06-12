---
title: "Linux VHD Boot Made Possible"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by huisinro on 2010-04-11
**1 Linux as Real Appliance**
 
With VBoot for Linux, you can pre-install and pre-configure Linux OS and its applications, then distribute the resulting virtual disk file in VHD format. The vhd can boot a real computer, with configuration and apps instantly available. This way, operating systems are truly manageable, as simple as files. We call such a Linux VHD to be a real appliance, in the sense that it boots physical computers.
 
It's very easy to setup and boot a computer with a vhd file. You download the vhd file, drop it to Windows or Linux file system, then configure the boot loader, and reboot the computer.
 
**2 Linux as Virtual Appliance**
 
The exact same vhd file also runs as a virtual machine using virtualization software, such as VMLite Workstation, VirtualBox, Xen and Virtual PC and Hyper-V, etc. By default, it's optimized for VMLite Workstation. 
 
If VMLite Workstation is installed, you can simply double click the ubuntu-910-desktop-i386.mop file to launch the vhd as a virtual machine with VMLite Workstation. 
 
**3 USB Boot Made Easy**
 
You just need to store the vhd file to usb drive, then hook the USB to different computers to boot.
 
 
A sample Ubuntu VHD package is ready for download:
 
[http://www.vmlite.com/index.php/download/22-appliances](http://www.vmlite.com/index.php/download/22-appliances) (free site registration required)
 
download, extract it, then double click setup.exe on Windows, reboot
On Linux, need to configure boot loaders.
 
detailed instructions:
 
[http://www.vmlite.com/appliances/ubuntu-910-readme.html](http://www.vmlite.com/appliances/ubuntu-910-readme.html)
 
screenshot:
 
[IMG]http://www.vmlite.com/images/vboot/vboot-grub2.png[/IMG]
 
VMLite Team

---

