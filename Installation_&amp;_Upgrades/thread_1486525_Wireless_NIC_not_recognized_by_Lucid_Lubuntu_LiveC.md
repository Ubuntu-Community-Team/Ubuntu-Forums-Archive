---
title: "Wireless NIC not recognized by Lucid Lubuntu LiveCD"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by uRock on 2010-05-17
I have a Netgear  USB wireless NIC and neither Ubuntu or Lubuntu Live images can see it. I  have tried copying wlan from another machine and installing the  packages, but that doesn't work.

I recently seen a thread showing what the file is that is missing in the Lucid live images that was present on the Karmic and earlier images, but I can't find it nor remember what the file was called.

Regards,
Ronnie

---

### Post by uRock on 2010-05-20
Any thoughts?

---

### Post by uRock on 2010-05-21
I have a netgear usb that is pluged in when I boot the LiveCD and it is not recognized. Is it possible to install ndiswrapper without an internet connect? I have the netgear disk with the driver that I can use to install after getting ndiswrapper installed.

---

### Post by uRock on 2010-05-21
Would installing usb-modeswitch fix this problem or is that only for 3G and not 802.11?

---

### Post by uRock on 2010-07-07
Never mind. Running CAT6 cabling to the host.

---

### Post by oldefoxx on 2010-07-10
Just going around an issue might mean your situation is resolved, but does not answer the fundamental question.  Will a LiveCD of Ubuntu work with Wireless as given?  You had a problem, I have a problem, and given the same circumstances, I expect many others have a problem.  We just don't all see it immediately.

Wireless is not one standard, there is some variance in both hardware and software involved, and connecting wirelessly means having details in hand that involve both ends of connection are called for as well.  What is called for, what is needed, and where to get the information is not evident with the LiveCD.  Fact is, they are not even evident after an install.

Initially it took weeks for me to explore on line, read up on and try enough alternatives before I finally got my install to work over wireless, and I still cannot tell you exactly how or what collectively it took to bridge the gap.  Still can't, for that matter.  Seems to hold up, cause I found that thread and repeated some of the steps to get another install working.  I am about to have to do it again.

But having to get on line first, then search to find, when nonworking wireless is all you have, makes very little sense to me.  Either you have to have access to another connected PC in order to be on line, or you have to have wired access built into the PC, say notebook, as well

But netbooks and ultrasmalls are increasingly coming with just wireless, not a wired capability.  They work with the provided software,
but going to Ubuntu might mean real problems.  And it is not right anyway, because if it is a bit involved or difficult, isn't that the type of problems that PCs are suppose to be good at?  Then why not have the software on the LiveCD and part of the Install that gets wireless up and running for you?

Until that happens, you can find an alternative in getting a USB to ethernet adapter.  now more recent versions of Windows can recognize and use such an adapter, but what goes for Windows does not always go for Linux.  So watch out for that.  Costs can total well under $10 if you shop around.

Meanwhile I was hoping that some of the readers here could kick in with links and details for getting wireless up and running that they know works, and might work for others as well.  When I run down my earlier thread, I hope to get back here to leave a link to it.

---

### Post by uRock on 2010-07-10
I still have Karmic on the machine in question. When I go to do the install I will be moving the machine to the location of my work machine and do the full install with hardwire. Hopefully the up to date kernel will get things up and running. If not, then I will try NDIS Wrapper with the Netgear Driver install disk. If that fails, then I will drop some lines and hardwire it. I plan to have my home network fully wired and only turn on wireless on the router when it is needed.

I agree with the concern over Netbooks and such that may not have an RJ45 adapter built in. 

Hopefully the kernel makers will be on top of that. My current wireless USB NIC is more than 5 years old and probably becoming obsolete.

```
Cheers & Beers
```
uRock

---

