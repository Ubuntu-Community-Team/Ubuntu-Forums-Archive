---
title: "Ubuntu 9.1 32-bit installation on x64 Windows 7 Virtual PC"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by nkelly on 2009-11-19
Hi,
 
I am trying to get Ubuntu 9.1 32-bit to run in a virtual machine on x64 Windows 7 Enterprise (RTM, fully patched).
 
The installer runs through fine (with noreplace-paravirt) however upon booting the VM I receive Segmentation Fault errors. Booting from the live CD will run the operating system so I know it is possible to have it running in Virtual PC.
 
I have read through various web boards and forum posts, tried all the suggestions however the machine won't boot.
 
The information I have read (Limited on the web) regarding the segmentation fault error suggests it relates to a memory addressing issue.
 
I have noticed that the image that is trying to boot has -pae on the end of it. 
 
linux /boot/vmlinuz-2.6.31-14-generic-pae
 
My machine currently has 2GB of RAM. Correct me if I am wrong (I come from a windows world) but Physical Address Extension was designed to over come the physical 4GB RAM limit with 32-bit computing, allow a 32-bit operating system to address more than 4GB of RAM.
 
I really would like to get this up and running using Virtual PC (Not interested in the other "Fantastic Packages" I can use to have the OS booting virtually in Windows 7). I am a fan of VMWare and have been a virtualisation consultant in the server arena for several years now.
 
Any assistance anyone can offer will be greatly appreciated. Once I iron out all the kinks in the installation procedure I will write a fully featured how-to installation guide as a gift to community.
 
Regards,
 
Noel

---

### Post by Mark Phelps on 2009-11-19
Are you using Virtual PC 2007? Asking because this issue has come up several times and each time, folks referenced the fact that supported OSs does not include any Linux OSs.

---

### Post by nkelly on 2009-11-19
Hi,
 
Thanks for your reply.
 
No I am using the built-in windows 7 virtual pc.
 
Whilst I recognise microsoft do not list Ubuntu as a supported OS in Microsoft virtual enviroments the fact that I can run off the boot CD in a VM leads me to believe that the OS is capable of booting of the hard drive itself.
 
Regards,
 
Noel

---

### Post by jagbarcelo on 2009-11-22
I can confirm your problem. I am running Windows 7 x64 and Virtual PC (all in final relase, not betas, nor RC). I downloaded and installed Ubuntu 9.10 Server and everything runs Ok during the installation process. At the end, the VM restarts and Segmentation fault occurrs. I have tried to install Ubuntu 9.10 Server with noapic, nolapic, acpi=off and other options with the same results. Sometimes Segmentation faults occurs, other times the VM window simply closes (equivalent to a turn-off?).
However, I was able to successfully install Ubuntu 9.10 beta on Virtual PC 2007 in Windows Vista 32bits without any problem. I even installed ubuntu-desktop package and run the server with gnome withou any video problems (besides of not having Virtual Machine Additions installed for the linux guest).
 
At work, we have been able to install Ubuntu 9.10 Server under the Hyper-V, the virtualization service provided by Windows Server 2008.
 
I have been working on this problem since the final release of Ubuntu 9.10 Server and I have found a workaround for this problem that involves disabling CPU XD bit in the BIOS host. You can read the full story in my blog post [[COLOR=#13b3bd]Segmentation fault on Ubuntu 9.10 Server under Windows 7 x64 Virtual PC [/COLOR]]("http://jagbarcelo.blogspot.com/2009/11/segmentation-fault-ubuntu-virtual-pc.html")
 
I hope it helps. Regards.

---

