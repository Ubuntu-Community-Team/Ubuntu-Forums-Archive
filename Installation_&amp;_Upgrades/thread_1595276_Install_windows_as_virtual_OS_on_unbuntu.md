---
title: "Install windows as virtual OS on unbuntu"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by jlab on 2010-10-13
So currently I'm dual booting windows 7 and Ubuntu. I love ubuntu, but I need windows cause I'm an engineer major and a lot of the programs I use don't work well in ubuntu. Its a hassle to switch between OSes. So is installing windows as a virtual machine a good option for me. Also does iTunes work in a virtual machine?

---

### Post by lechien73 on 2010-10-13
It depends on what programs you're using in Windows, really. They will, in all likelihood, work fine in a virtual machine - with maybe a little performance hit. You probably want to try them first before making a decision.

For the record, I'm using customised proprietary software in a Windows virtual machine that links to phone and alarm systems through USB. It works fine.

Regarding iTunes, there was a problem with newer versions under VirtualBox. Anything after 9.02 would crash if your processor didn't have virtualisation extensions. That appears to be fixed, though, because I'm now happily running iTunes 10 on a Windows 7 VM under VirtualBox 3.2.8 and it's working fine.

---

### Post by jlab on 2010-10-13
Thanks for the response! I've tried my programs and they work. 

But now I have a question about formatting my drive. I have 3 partitions, windows, storage, ubuntu , with all my data being in the storage partition. Do I need to reformat my harddrive first or keep it the way I have it. Because honestly I'm a little confused on how the virtual box thing works

---

### Post by coffeecat on 2010-10-13
You need to format your partitions to suit the host OS, not the guest OS. I have Vista running* as a guest OS in VirtualBox with Ubuntu as the host. I have two data partitions, both formatted ext4. I have set up the data partitions as shared folders in Vista, and Vista can read and write to both. That's because Ubuntu is doing the reading and writing.

I've also had Ubuntu as a guest OS in VirtualBox in MacOS as the host, with Ubuntu seemingly writing to the MacOS hfs+ (journalled) filesystem through a shared folder - which is not something you see every day. In reality, of course, it was MacOS writing to the hfs+ filesystem.

* "Vista running". Hmmm. Now that would be a good idea. :-k

---

### Post by jlab on 2010-10-14
So does it make sense to just keep my storage partition and delete my windows partition?

---

### Post by coffeecat on 2010-10-14
> **jlab said:**
> So does it make sense to just keep my storage partition and delete my windows partition?

If you're happy with Windows running in VirtualBox, I guess so. You might want  to keep the native install of Windows for a little while just in case you find the VBox one gives you any trouble you can't solve - unlikely though that is. Just so long as that doesn't run foul of the activation of Windows, assuming you're having to use the same product key to install the virtualised Windows.

---

### Post by Elwood4Pena on 2010-10-14
[B]Hi.. I am new in this forum.
I really like the features and applications of unbuntu.
so i want to install windows as virtual OS on unbuntu.
Please suggest me some easy ways t install it.
[/B]

---

### Post by jlab on 2010-10-15
> **coffeecat said:**
> If you're happy with Windows running in VirtualBox, I guess so. You might want  to keep the native install of Windows for a little while just in case you find the VBox one gives you any trouble you can't solve - unlikely though that is. Just so long as that doesn't run foul of the activation of Windows, assuming you're having to use the same product key to install the virtualised Windows.

thanks I was thinking if I should keep the dual boot or not. I keep it for now I guess and see how every goes from there. Thanks for you help guys

and so far it looks like either use virtual box or vmware to run a ghost os

---

### Post by ark1-87 on 2010-10-15
has anyone had issues with upgrading to 10.10 with vmware installed?

---

