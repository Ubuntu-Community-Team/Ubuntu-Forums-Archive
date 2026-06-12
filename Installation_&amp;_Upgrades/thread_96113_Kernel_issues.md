---
title: "Kernel issues"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by sfabel on 2005-11-28
Hi ppl,

Ubuntu is a great Distro, I like to use it, and forget about the OS itself, but instead focus on my work. Ubuntu lets me to exactly that. Having said that, there is one thing that is getting on my nerves, and that is the issue of supporting new kernels.

2.6.12 might look like a good enough version for a kernel, but in fact, it has many problems in the SMP sector (and I happen to own a X2 Dual-Core AMD64). The problem known as "double-speed clock" could not be solved with whatever tricks were posted both here and in the kernel mailing list. Several kernel parameters do simply not work on that hardware, or freeze up my computer. I got rid of the AMD64 Version of Ubuntu and installed the i386 Kubuntu Version, just to see if this problem would still be there. It became worse. With my AMD64 Version I could at least pass the kernel parameter "notsc" and not have to watch fast forward DVD's or not being able to listen to MP3's since they were played back fast.

The kernel team recommended upgrading to 2.6.13 or later. In fact, as far as I know 2.6.15 is out there already. 

I don't understand why Canonical is not looking at these kernel developments and putting out upgrades when severe bugs as this one become known. It is strange to have to wait 6 months for a kernel upgrade. 

Oh, I know I can compile a kernel myself. But that's not very user friendly, is it. Besides that I don't have the slightest idea what kind of kernel patches Canonical has been using to make Ubuntu work the way it does.

Being able to upgrade minor kernel versions has been integrated in Distributions as far as I can remember, and I don't see a valid reason for taking it out. Even on SuSE I could start up YaST, and it would present a new kernel version if there was one.

Don't get me wrong; I got this distro free of charge, and I know I can't **demand** anything. But, I don't see a big issue of putting out minor kernel upgrades or at least putting out patches for re-compilation of a newer version. Users can download the kernel source with the Ubuntu patches included, so why not release a patch that would upgrade this source tree to a newer linux kernel version?

I don't think it would be too much work, since there's gotta be a kernel team working on this core component already (since there are unique Ubuntu patches or so I've been told).

Wait until April until my computer works again and doesn't repeat every character on the screen X times? Don't think so.

Stephan :???:

---

### Post by bwog on 2005-11-28
Did you upgrade the i386 kernel to k7-smp?

The 6-month distribution upgrade is a choice made for this distro, it had advantages and disavantages. Developers need to make certain choices and stick to it, so that users know what to expect.

---

### Post by sfabel on 2005-11-28
Hi bwog, yes, I did install the correct kernel package. I am not trying to debate over the 6 month distribution upgrade policy, that is fine with me. Just de-couple the kernel versions with distro releases. I am talking about minor-upgrades. If this was a company and I bought the system from them, I'd say that they didn't test their software enough. Why even release a buggy SMP kernel version? Stephan

Edit: This has been working with applications that run on top of the operating systems => backports. Just why minor kernel releases are not included there is a miracle to me.

---

### Post by bwog on 2005-11-28
I understand that this post is related to installation, but its main topic is ubuntu's policies. So, perhaps it is better to continu this discussion in the chat section. There are lots of well-informed users there who will be anxious to reply.

---

