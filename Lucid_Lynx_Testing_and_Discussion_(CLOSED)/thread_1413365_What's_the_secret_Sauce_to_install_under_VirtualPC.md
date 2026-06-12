---
title: "What's the secret Sauce to install under VirtualPC, Windows7"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mattisking on 2010-02-22
At the office everyone runs Windows. As a developer I have a certain amount of flexibility others do not. As such, I've always maintained a virtual machine running the current copy of Ubuntu. Even recently with the switch to Windows7 for IT/Management, I kept VMWare Workstation installed with an Ubuntu vm. However, I've had to remove VMWare Workstation. The version I have is too flaky under Windows7 64-bit and my need to rather often utilize the Windows7 "XP Mode" for certain applications means I'm regularly using Microsoft VirtualPC, built into Windows7. 

In the past I was always able to get Ubuntu working under VirtualPC using various kernel arguments like:
 noreplace-paravirt vga=791

With the recent changes to GRUB it says these are no longer valid and indeed, they no longer work. One time I managed to actually get through the installer only to fail to boot at all but if I do nothing and just run with either installer (desktop or alternate) without modifying the bootup it just crashes immediately and closes the VM.

Could anyone that has this working stick up a current "how to"? I've googled it a good bit but always end up with previous versions of Windows, VPC, and Ubuntu which always offer the same kernel parameters I've already mentioned.

Thanks!

---

### Post by Merk42 on 2010-02-22
Does the VirtualPC in Windows 7 even support Linux? I thought that was mostly for people needing XP or 16bit applications (in a 64bit OS)

If you can't use VMWare, use Virtualbox as it supports Linux fine.

---

### Post by mattisking on 2010-02-22
The only reason I ultimately abandoned VMWare (which is my favorite) is because for whatever reason it couldn't run at the same time as VirtualPC. Since "XP Mode" keeps VirtualPC running (hibernated) most of the time, as soon as VMWare made a grab for resources when starting a VM it would crash.

Yes, VirtualPC CAN run Linux, it's just always required a little playing with the boot options. I did manage to get the first alpha to install until it updated itself and got the new GRUB and kernel at which point it didn't like the kernel options I used to get it that far and would no longer boot. I really do hate being stuck with VirtualPC but it's my only real way to run Windows7 as my developer PC since we're still stuck maintaining (gradually replacing) old VB6 and even one VB4 app.

---

