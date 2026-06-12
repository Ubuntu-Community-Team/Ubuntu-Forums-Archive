---
title: "Problem with Mouse Cursor movement with Ubuntu 7.10 64 bit in a VM"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by jholmblad on 2007-12-06
All,

I have a problem that came about as a result of the need to install the 64 bit version of Ubuntu since, it seems the 32 bit Ubuntu CD that I received form Canonical is defective.

**Here is the problem I am having:**

The mouse cursor has great difficulty recognizing the full dimensions of the monitor screen. It seems to prefer the right hand side of the screen and getting it to move to the left is very difficult. 

[B]Here is how my installation is configured
[/B]

I have installed Ubuntu V 7.10 64 bit as a VMware Server Virtual Machine running on a dual core Athlon 64 system with plenty of RAM. The host OS is Microsoft Windows Home Serve (WHS) which is a 32 bit OS. I have confirmed, using a check utility from VMware, that this particular processor DOES support 64 bit guest OS's. 

Furthermore I access the guest OS by using the Microsoft RDP client from a Windows XP SP2 system connecting to the WHS host, and, from there launching the Ubuntu VM in a window opened up by the VMware server.

The Mouse I am using on my Windows XP system is a RF (bluetooth I think) wireless optical mouse and it works fine with other 32 bit guest OS's running on the same system but with Microsoft Virtual Server which, unfortunately, itself does NOT support 64 bit guest OS's.

Furthermore the display device on my Windows XP system is a 22' Viewsonic and the resolution is set to 1680x1050 pixels as is the RDP client. When I connect to WHS using RDP and check the desktop properties it shows the same resoluition, i.e. 1680x1050.

**Speculation**

Perhaps the problem results from the fact that I am running the 64 bit guest OS under the control of an instance of VMware Server running on a 32 bit host OS?

Any help would be appreciated.

---

### Post by brunjes on 2008-02-16
I cannot offer a solution here, but I have a bit more data.

I have the same problem but I am running 32-bit Ubuntu under VMware. There is something that VMware Workstation 6 has done to make this happen. Under VMware Workstation 5.5, this problem did not happen. I believe (just a hunch really) that it has something to do with that annoying VMware menu that hangs around the top of the screen (you can make it go away by unpinning it or by selecting "Exclusive Mode" but it does not matter, eventually the problem comes back. I find that visiting websites in Firefox seems to make this problem surface more frequently.

Anyone have a workaround?

Thanks,

Roy

---

