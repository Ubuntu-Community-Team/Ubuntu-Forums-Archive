---
title: "faster virtualization solution???"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by youbuntoo on 2006-03-24
I have a virtual machine running XP through the use of VMware, but when I run it, the processing is SO FREAKIN' SLOW!  I am getting fed up w/ VMware; I only run the XP VM briefly each day for a few windows apps, but still, I'd like to find a virtualization solution to replace VMware.  I know Microsoft makes VPC, but I've heard that's no good as well.  Anyone heard of/know anything about Parallels Workstation?  Is it worth giving a try?

---

### Post by petervk on 2006-03-24
VMWare is probably your best bet for speed. Their known for being the (or one of the) fastest.

You may just need to optimize the setup.
Check how much ram you have allocated to the VM (Virtual Machine), use as much as you can possibly spare. (for a 512mb machine, allocate at least 256mb.) You do have at minimum 512mb or ram, right? Buying more would really help.

Remember that any ram Ubuntu is currently using will not be able to be used properly by the VM (read, will make the VM run really slow), so quit any open applications in Ubuntu before starting the VM. 

Run the system monitor application in Ubuntu to check whats using your virtual memory. Some applets are great, but consume a ton of ram. Oh and firefox is a memory hog, don't use it while running the VM.

Another good idea is to downgrade to Windows 2000. Its much faster then XP and will run a lot better in a VM.

If your sticking with windows XP make sure you've optimized it as much as you can. Get rid of unneeded background processes, get rid of all the fancy effects, etc. You can try following [this guide]("http://www.tweakguides.com/TGTC.html").

Just remember, a VM will at very best be able to run software at 90% of the speed that it would run on the hardware directly. Windows XP is not exactly a speed deamon while on native hardware, so it's never going to be amazingly fast. 

Other VM Programs:
Virtual PC is not for Linux (Its a Microsoft Product)
Parallels Workstation could be worth a try, but I bet VMware is about the same speed wise.
Qemu is opensourced and with the closed-source kernel module it is reported to be somewhat quick, but VMware is definetly faster.
Xen only works for OS's that are built for it. (currently not windows, and really it will be a cold day in hell when windows runs officially in Xen)

---

### Post by adie273 on 2006-03-24
petervk is right,

Vmware is about as fast are your gonna find. You mentioned Microsoft Virtual PC which is only for Windows. Unless its actually Windows XP your using as your host OS. In which case I know from previous experience how **painfully** slow Vmware can be.

Qemu works and as petervk said its opensource. However i've used it before, and even with the Kqemu module, it is slow when running Windows XP as the guest OS. So other than using Qemu and grabbing a copy of Windows 98 or 2000 which should be faster. Your best bet is to just stick with Vmware.

---

### Post by youbuntoo on 2006-03-24
i refuse to accept that fact that VMware is ONLY option!

regardless, I went to [www.parallels.com](www.parallels.com) downloaded the free trial of workstation 2.1 and loaded up XP.  wow, no joke, it's like a whole new world.  Parallels is fast, it's faster than fast.  When my trial period runs out I may just have to throw down the 49 bucks for a license.

---

### Post by youbuntoo on 2006-03-24
.

---

