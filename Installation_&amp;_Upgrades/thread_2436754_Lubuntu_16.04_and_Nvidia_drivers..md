---
title: "Lubuntu 16.04 and Nvidia drivers."
date: 2020-02-12
forum: Installation &amp; Upgrades
---

### Post by O)9(yo&amp;# on 2020-02-12
Hi, my question is about Lubuntu. My 8400GS video card died recently, putting my Gateway GT5656 desktop back to on-board graphics (6150SE n430). I have been experimenting with various lite distros, the most recent being Lubuntu. I chose 16.04 because it will let me install Nvidia drivers on it (304, the last one that supports these graphics). However, before I switched to them, I decided to update immediately for security. but that put me on a kernel (4.15) which is too recent for Nvidia to work. If I find I need Nvidia drivers, I could reinstall and stay with an earlier kernel (I'm not sure which one that would be, most likely 3.x). For comparison, I have Linux Lite 3.0 working well with Nvidia 304, but I have not updated to the next point release (3.2). The reason I may do better with Nvidia vs Nouveau is that I get display freezes with Nouveau. It hasn't happened yet with Lubuntu 16.04, but when I tried 18.04 earlier, it did. And I could not install Nvidia drivers on 18.04.

I use Vivaldi as my browser, and I disable acceleration and several other things that may cause problems. So, the question is, if I find I need to use Nvidia, should I reinstall and avoid updating to the 4.x kernel? Is that safe to do? Another option may be to choose which kernel to boot from. Would that be better to do?

Thanks, 

Mike

---

### Post by EuclideanCoffee on 2020-02-12
> [COLOR=#000000]should I reinstall and avoid updating to the 4.x kernel? Is that safe to do? Another option may be to choose which kernel to boot from. Would that be better to do?[/COLOR]

Simply consider how much threat you are willing to accept. If you want to browse websites, then you might want the most secure stable kernel. But if you want higher performance and do not care to browse as many websites (say you know the owners of the websites you browse), then you won't need to care so much about kernel security patches, since the likelihood of having a browsing session take over your computer is less.

Something else you can consider, you may want to add attack mitigation to your browsing habits. So you can use browser applications that allow you to visit a website, disable javascript, and then enable javascript based on your browsing habits.

I recommend ublock and umatrix for this.

---

### Post by CatKiller on 2020-02-12
> **michael_diemer said:**
> I chose 16.04 because it will let me install Nvidia drivers on it (304, the last one that supports these graphics). However, before I switched to them, I decided to update immediately for security. but that put me on a kernel (4.15) which is too recent for Nvidia to work. 

If you install the linux-generic metapackage rather than the HWE (hardware enablement) one, you'll be on the 4.4 kernel branch rather than 4.15. That will still get security updates for the full support period of 16.04. I couldn't tell you for sure if that will work with the legacy nvidia driver you need to use.

---

### Post by mörgæs on 2020-02-12
The Nvidia 6150SE n430 is a special case and the problem is exactly as you describe: Most Geforce cards of the same age run fine with Nouveau but this one needs Nvidia closed source drivers which are not supported by newer kernels. 

I suggest that you try to find a used graphics card to replace the 8400.

---

### Post by bcschmerker on 2020-02-12
**I've some information about *my* experiments with an nForce® slimline.**  During my prepwork on an *e*machines®/ac*e*r® EL1210-09 (2.4 Ghz Advanced Micro Devices® Athlon® LE-1620 (Socket AM2), nVIDIA® nForce® 785 chipset w/ integrated 64-bit geForce® GPU C77) anticipating installation at a house of worship, I went through a number of low-profile geForce® VDA's after replacing the stock LITEON® PSU with a Shuttle® PC6300001, eventually settling on an msi® N610GT-MD1GD3/LP (nVIDIA® 64-bit GPU GF119) - the Fermi is one of the last generations of nVIDIA GPU's not requiring initial microcode load (required for Maxwell, Pascal, Volta, Turing, and likely Ampére).  The EL1210 with its nF785 chipset shuts down and reboots properly on the nVIDIA® CUDA™ driver suite for GPU's up to Kepler; I have reason therefore to estimate that your nF430 will so do with an upgrade GPU.

---

### Post by O)9(yo&amp;# on 2020-02-12
> **ruze said:**
> Simply consider how much threat you are willing to accept. If you want to browse websites, then you might want the most secure stable kernel. But if you want higher performance and do not care to browse as many websites (say you know the owners of the websites you browse), then you won't need to care so much about kernel security patches, since the likelihood of having a browsing session take over your computer is less.

Something else you can consider, you may want to add attack mitigation to your browsing habits. So you can use browser applications that allow you to visit a website, disable javascript, and then enable javascript based on your browsing habits.

I recommend ublock and umatrix for this.

Thanks, some very good points there. As for browsing, I have a handful of forums I visit daily, maybe 5-10 most days. Then there is research, tutorials, etc. My general habits are safe, so I may get away fine on an older kernel. to my knowledge, I have never had a virus on windows or linux. The only bad experience was on a BSD system. I was on a music forum, left my computer for a bit, and when I came back someone had opened up a terminal and was typing. I caught them just as they were attempting to change root. I shut down immediately, uninstalled the system, and ran a cleaner to thoroughly erase any crap they might have planted. No idea who it was, or how they got in, but I have avoided BSD ever since. Which may be an over-reaction, but it scared the heck out of me. I will check into adding an extension as you suggested. I've been wondering about that anyway.

---

### Post by O)9(yo&amp;# on 2020-02-12
> **CatKiller said:**
> If you install the linux-generic metapackage rather than the HWE (hardware enablement) one, you'll be on the 4.4 kernel branch rather than 4.15. That will still get security updates for the full support period of 16.04. I couldn't tell you for sure if that will work with the legacy nvidia driver you need to use.

I'm guessing it won't. Every system I have tried lets me switch to 304.135 or 304.137 after installing, but after updating it becomes non-functional (everything looks like Vesa drivers, 3X the size it should, and no way to change resolution). I'm hoping I saved the Nvidia forum thread that discussed this, it may have the last kernel that it will work on (I was on another Linus system at the time; I'm going to see if I saved it).

---

### Post by O)9(yo&amp;# on 2020-02-12
[I]morgaes said:

[COLOR=#000000]The Nvidia 6150SE n430 is a special case and the problem is exactly as you describe: Most Geforce cards of the same age run fine with Nouveau but this one needs Nvidia closed source drivers which are not supported by newer kernels.[/COLOR]

[COLOR=#000000]I suggest that you try to find a used graphics card to replace the 8400.[/COLOR][/I]

Yep, I'm planning on keeping my eyes peeled for a good deal. In the meantime, things are working well enough with Nouveau on Lubuntu and Linux Lite 3.0. At least I have a year of support left on those systems. They have been the best so far and will likely be my keepers for the time being. Who knows, the computer may die anyway soon, it came out around 2008.

---

### Post by O)9(yo&amp;# on 2020-02-12
> **bcschmerker said:**
> **I've some information about *my* experiments with an nForce® slimline.**  During my prepwork on an *e*machines®/acer® EL1210-09 (2.4 Ghz Advanced Micro Devices® Athlon® LE-1620 (Socket AM2), nVIDIA® nForce® 785 chipset w/ integrated 64-bit geForce® GPU C77) anticipating installation at a house of worship, I went through a number of low-profile geForce® VDA's after replacing the stock LITEON® PSU with a Shuttle® PC6300001, eventually settling on an msi® N610GT-MD1GD3/LP (nVIDIA® 64-bit GPU GF119) - the Fermi is one of the last generations of nVIDIA GPU's not requiring initial microcode load (required for Maxwell, Pascal, Volta, Turing, and likely Ampére).  The EL1210 with its nF785 chipset shuts down and reboots properly on the nVIDIA® CUDA™ driver suite for GPU's up to Kepler; I have reason therefore to estimate that your nF430 will so do with an upgrade GPU.

Wow, this looks to be way beyond my level of expertise. I'm not sure what you are talking about here. Do you mean installing another card, or a program that boosts the on-board graphics?

---

### Post by O)9(yo&amp;# on 2020-02-13
I booted the 4.4 kernel, and it runs the Nvidia 304 fine. But the 4.15 kernel won't, so 4.4 appears to be the last one it works on. I have it running and everything seems fine. And as CatKiller said, 4.4 will be supported for the duration of 16.04. So, For now I'm good, but I will be on the lookout for a cheap card.

---

### Post by O)9(yo&amp;# on 2020-02-13
> **CatKiller said:**
> If you install the linux-generic metapackage rather than the HWE (hardware enablement) one, you'll be on the 4.4 kernel branch rather than 4.15. That will still get security updates for the full support period of 16.04. I couldn't tell you for sure if that will work with the legacy nvidia driver you need to use.

Update: you were right, 4.4 does let me install the 304. I just booted the 4.4 Linux generic and then ran the Driver Manager. On it now, so far so good. but, I'm not sure if this is the metapackage or not. I definitely want the support, so I need to know if I am on the right package, and if not, how to get it.

---

### Post by CatKiller on 2020-02-13
> **michael_diemer said:**
> Update: you were right, 4.4 does let me install the 304. I just booted the 4.4 Linux generic and then ran the Driver Manager. On it now, so far so good. but, I'm not sure if this is the metapackage or not. I definitely want the support, so I need to know if I am on the right package, and if not, how to get it.

The linux-generic metapackage doesn't install anything by itself, it just depends on the latest (non-HWE) kernel. When a newer version of the kernel comes out, the metapackage's dependencies are updated so that it pulls in the newer kernel. The kernel packages themselves are thus marked "automatically installed" so old ones can be autoremoved at the appropriate time, and you can always have multiple versions of the kernel without any conflicts. The linux-generic-hwe-16.04 metapackage is similar, but will always depend on the latest HWE kernel.

Glad to hear it all worked for you.

---

### Post by guiverc on 2020-02-13
Lubuntu 16.04 LTS is EOL & has been awhile ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)). 

Ubuntu 16.04 LTS as a server (no desktop), Desktop (default Unity desktop, or with Kylin desktop) was given five years of support and is thus supported, but all other flavors are EOL now.

> [COLOR=#333333]Maintenance updates are provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, Ubuntu Base, and Ubuntu Kylin. All the remaining flavours are supported for 3 years.[/COLOR]

[http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

I suggest examining `ubuntu-support-status` for your actual system to explore what parts of your system are still supported, and don't forget many parts of 16.04 LTS (including the Lubuntu desktop) are already EOL & unsupported.

If you do need to use 16.04, consider the default Unity 7 desktop as it has five years of support (ending 2021-April).

---

### Post by O)9(yo&amp;# on 2020-02-13
> **guiverc said:**
> Lubuntu 16.04 LTS is EOL & has been awhile ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)). 

Ubuntu 16.04 LTS as a server (no desktop), Desktop (default Unity desktop, or with Kylin desktop) was given five years of support and is thus supported, but all other flavors are EOL now.



[http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

I suggest examining `ubuntu-support-status` for your actual system to explore what parts of your system are still supported, and don't forget many parts of 16.04 LTS (including the Lubuntu desktop) are already EOL & unsupported.

If you do need to use 16.04, consider the default Unity 7 desktop as it has five years of support (ending 2021-April).

Thanks for setting me straight on that!  Running Unity is very iffy; I have found that only light systems work well on these old graphics. I'm going to see if I can run Lubuntu 18.04 but use the 4.4 kernel.

Edit: just checked, 18.04 ships with 5.x kernel. Doesn't look like that will work. Guess I need to do more research.

---

### Post by guiverc on 2020-02-13
Lubuntu 18.04 LTS ships with the 4.15 kernel if installed with a 18.04, 18.04.1 ISO image.
The 18.04.2 ISO ships with the 4.18 kernel & stack from 18.10
The 18.04.3 ISO ships with the 5.0 kernel & stack from 19.04
The 18.04.4 ISO ships with the 5.3 kernel & stack from 19.10

Any install of 18.04.2 & later (with HWE enabled) will auto-upgrade to the latest stack, currently 18.04.4 and 19.10's stack and eventually get the 20.04 stack as it's final destination.

Installs with the original media (18.04 or 18.04.1) will stay on 4.15 unless HWE is enabled by the user.  See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for more details.

This detail applies to any flavor of Ubuntu, not just Lubuntu.

---

### Post by bcschmerker on 2020-02-14
> **michael_diemer said:**
> Wow, this looks to be way beyond my level of expertise. I'm not sure what you are talking about here. Do you mean installing another card, or a program that boosts the on-board graphics?
**An add-in card to by-pass the 64-bit geForce® GPU in the nForce® 430 chipset.**  A system as old as your GT5656 will probably not handle a card with wider than 128-bit video memory; I therefore suggest a GT 520 or 610, which packs an nVIDIA® GF119 GPU and 1 GiB GDDR4 64-bit video memory.

---

### Post by mikewhatever on 2020-02-14
Lubuntu 16.04 is only good as a short term solution. All of Lubuntu packages went EoL in 2019, and the base support will follow in 2021. I'd start planning for hardware with nvidia-340 support, which is available in 18.04 and, hopefully, 20.04.
You can see the supported cards here [https://www.nvidia.com/download/driverResults.aspx/77224/en-us](https://www.nvidia.com/download/driverResults.aspx/77224/en-us).

---

### Post by CatKiller on 2020-02-14
> **guiverc said:**
> I suggest examining `ubuntu-support-status` for your actual system to explore what parts of your system are still supported, and don't forget many parts of 16.04 LTS (including the Lubuntu desktop) are already EOL & unsupported.

This is a good suggestion, so that the OP can see the exact status. 

The Ubuntu flavours all use the same repositories, so they all get the same updates. The kernel, the web browsers, and the shared applications and libraries will all still get the same security updates. It's the flavour-specific stuff that doesn't get those updates: the teams that put together the flavours don't have the resources to backport things to five or six concurrent releases, so they can't commit to as long a support period.

---

### Post by O)9(yo&amp;# on 2020-02-14
> **guiverc said:**
> Lubuntu 16.04 LTS is EOL & has been awhile ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)). 

Ubuntu 16.04 LTS as a server (no desktop), Desktop (default Unity desktop, or with Kylin desktop) was given five years of support and is thus supported, but all other flavors are EOL now.



[http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

I suggest examining `ubuntu-support-status` for your actual system to explore what parts of your system are still supported, and don't forget many parts of 16.04 LTS (including the Lubuntu desktop) are already EOL & unsupported.

If you do need to use 16.04, consider the default Unity 7 desktop as it has five years of support (ending 2021-April).

I must have misunderstood the info on the Lubuntu page. I thought the community supported it for 5 years. I figured that would be fine.

---

### Post by O)9(yo&amp;# on 2020-02-14
> **bcschmerker said:**
> **An add-in card to by-pass the 64-bit geForce® GPU in the nForce® 430 chipset.**  A system as old as your GT5656 will probably not handle a card with wider than 128-bit video memory; I therefore suggest a GT 520 or 610, which packs an nVIDIA® GF119 GPU and 1 GiB GDDR4 64-bit video memory.

Thank you, I will look into those cards. The 8400GS worked fine until it went. The fan was making a terrible noise. I took it apart to try to fix it but managed only to make it worse....

---

### Post by O)9(yo&amp;# on 2020-02-25
I have discovered that Linux Lite 3.8 allows the 304 drivers, and is supported until 04/21, so I am using that. No display problems at all. For now I'm calling it solved. A year from now, who knows...

---

### Post by O)9(yo&amp;# on 2020-08-09
Update: I also have installed Ubuntu 14.04, with the Extended Security Maintenance. so I have two systems that are working fine. I should be able to get Ubuntu 16.04 going with the 304 driver, I may try that soon. Eventually I'll need to get a new card I suppose, but for now things are fine.

---

