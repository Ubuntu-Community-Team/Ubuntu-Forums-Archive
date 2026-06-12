---
title: "Nviidia GT220 Upgrade"
date: 2023-05-12
forum: Installation &amp; Upgrades
---

### Post by Ian Hewitt on 2023-05-12
Hi,

I have been experiencing problems with my current NVIDIA GT215 card which is running under a GT220 driver. I have tried to use the recommended GT240 driver but this will not work.

I am thinking of upgrading the graphics card to a more recent one that is supported for Ubuntu 22.04.

Any recommendations for a suitable alternative that is not too expensive or over specified for my system - 16Gb Intel i5-4570.

Many thanks

Ian

---

### Post by TheFu on 2023-05-12
Avoid nvidia.  Go with a cheap AMD.  AMD drivers are built-into the kernel, so no more wondering if you have the right drivers or dealing with nvidia deciding to end support.   
When I moved to 16.04, lost support for an nvidia 7200GS card that had been working perfect, at the resolution of the monitor (1920x1200) for years. ZERO hardware changes.  At the time, I didn't know better and got a $70 1030GT ... which was pre-COVID/pre-crypto mining. A few times every year, the proprietary driver for that card would fail with DKMS and I'd need to re-install the drivers manually.  Nothing but hassles.  Last fall, I'd had enough and upgraded the CPU to a Ryzen with a built-in GPU and started using it.  The Ryzen GPU is more powerful/faster/better/cheaper than the nvidia 1030GT (ddr5 version).  No issues since.  It just works.

So, I've come to this conclusion.  If you aren't spending $800+ on a GPU, stick with AMD and be happy.  This assumes the build-in iGPU with the CPU isn't sufficient.  All my laptops the last 15+ yrs had intel iGPUs and they were fine for all my needs ... well, except the Atom N270, but that was before mpeg2 and h.264 video support was always included in the on-board graphics.  Since 2012, that hasn't been any issue at all.

I have an nvidia 430GT still in a system here. I've been planning to retire that box about 4 yrs, but just haven't gotten around to it.  It is a static web server and backup server, so moving what it does to other systems will take a little planning.  Most backups have already been migrated, but there's always a few dependencies keeping that Core i5-750 around. Sigh.

Get an AMD GPU. Be happier.

---

### Post by #&amp;thj^% on 2023-05-12
Before buying and plugging a graphics card on your Linux system, you should know a little bit about AMD and Nvidia support for Linux.

AMD uses open-source drivers for their graphics card whereas Nvidia uses proprietary (closed-source) drivers for their products.

Linux is open-source, so are the operating systems based on Linux kernel like Ubuntu, Fedora, Arch Linux etc. Most Linux based distributions don&#8217;t ship with proprietary drivers.

That&#8217;s why most users prefer AMD Radeon graphics cards as the drivers are open-source and in-built in the Linux kernel. So, you don&#8217;t need to go through any hassle of installing drivers manually.

In the case of Nvidia, you will have to install the drivers manually._ In some cases, it might even create some compatibility issues like the login loop on your Linux system._ You might have to try out different driver versions to make the graphics card work properly.

Both AMD and Nvidia creates amazing piece of hardware. However, if you want to go with the Nvidia graphics card, then do your research about compatibility with your particular Linux distro.
If you take your time and read up on the nVidia cards your interested in then should have clear sailing.
I've used nVidia for over 19 years now and i wont give it up.

However there is lot to be said Good, with TheFu post

---

