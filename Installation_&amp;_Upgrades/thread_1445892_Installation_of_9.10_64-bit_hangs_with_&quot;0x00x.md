---
title: "Installation of 9.10 64-bit hangs with &quot;0x0/0x20&quot; on Asrock 939 Dual-Sata 2"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by tar- on 2010-04-03
While attempting to install ubuntu 64 bit the installation process hangs on "[...] ? child_rip 0x0/0x20" and will not go any further. 

The 32-bit version of ubuntu seemed to install fine up to the point of "please restart" (after which my psu died). This leads me to think it's a driver-issue.

MBoard: Asrock 939 Dual Sata II
CPU: AMD Athlon 64 3200+ Venice 
Graphics: ATI Radeon X1600 Pro

Where can I rtm on all these "? child_rip 0x0/0x20" messages?
How do I find out which driver is missing based on this message?
Anyone else with this setup who's made it work (preferably without recompiling a kernel)?

I also have 2 disks in a striped raid-array using the onboard controller. The on-board controller should've displayed it as one disk to ubuntu, however it ended up as two separate disks. Any suggestions on how to recover the raid?

---

### Post by djmoore7.11 on 2010-05-09
I'm having the same problem with 10.04 no matter if I use a DVD boot or USB boot!

Would using the 32-bit version work for me, you think?  I'd prefer the 64-bit.  Is there still a RAM limitation like with Windows?

---

### Post by Dave Gravox on 2010-05-17
I'm having the same issue. I've tried 10.04 alternative and desktop iso. 9.10 doesn't work either but doesn't come up with the child_rip message.

Toshiba Pro Satellite L510 PSLGXA-002002
Core i3 2.13, 4GB RAM, ATI Mobility Radeon HD 5145

---

### Post by tovarcf on 2010-05-21
Hi All.

I know it's not very useful only to see more people having the same problem as us, but I just want to state that it seems we all have a common problem. 

I have same problem when trying to install 10.04. I've tried both 32 and 64-bit versions, even netbook and desktop releases. I even tried the Windows installer which added "ubuntu" to operating system list at boot. All of them failed with child_rip message.

My machine is a Toshiba Satellite L500-SP6018M with Intel i3 and 3 GB of RAM. It also has a 320 GB disk and a HD display. There are a few new items that might cause our problem: probably HD display, disk capacity or the new i3 processor.

I hope we find the solution soon, since I have hope to be able to transform my father into Linux.

Regards.

Carlos.

> **Dave Gravox said:**
> I'm having the same issue. I've tried 10.04 alternative and desktop iso. 9.10 doesn't work either but doesn't come up with the child_rip message.

Toshiba Pro Satellite L510 PSLGXA-002002
Core i3 2.13, 4GB RAM, ATI Mobility Radeon HD 5145

---

### Post by Dave Gravox on 2010-05-28
Bump

Seriously? This seems quite serious. There must be more people out there with this problem.

---

### Post by jpillman on 2010-06-04
Same issue here when I try to install Ubuntu 10.04 64 bit.  My machine is a Toshiba Satellite L505 with Intel i3 and 4 GB of  RAM. It also has a 320 GB disk and a HD display.  Does anyone have any solutions?  I have also tried Fedora and experience the same problem.

---

