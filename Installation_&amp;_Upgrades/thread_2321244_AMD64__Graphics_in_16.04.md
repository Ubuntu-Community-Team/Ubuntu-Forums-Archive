---
title: "AMD64  Graphics in 16.04"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2016-04-21
I received this in an email from F.O.S.S advising serious Linux gamers using AMD/ ATI not to upgrade for the moment.  I do not use Ubuntu for gaming but I do use dual monitors. Is it safe for non-gamers to upgrade from 14.04 to 16.04?

[I]**No support for AMD/ATI Radeon proprietary drivers**

If you are serious on Linux gaming, this is the news for you. Ubuntu 16.04 is dropping support for AMD’s Catalyst Linux driver, known as fglrx. This proprietary graphics driver will be replaced by AMDGPU, the open source driver being developed by AMD.

But there are issues with the AMDGPU. First, it’s under development and not ready yet. Second, it’s not compatible with older graphics hardware.

In short, Radeon users, stay away from Ubuntu 16.04 for now.[/I]

---

### Post by grahammechanical on 2016-04-21
> Is it safe for non-gamers to upgrade from 14.04 to 16.04?

What is safe? Just watch the forum sections & see the number of people who are upgrading and failing in some way. This is why some of us recommend a fresh install. And some recommend some advance preparation such as changing from proprietary video drivers to open source video drivers, reverting the desktop to a default standard as much as possible & disabling PPAs. Oh, and backing up important data.

Anyone, using a AMD proprietary video driver & who upgrades to 16.04 will have the proprietary video driver replaced by the open source video driver that is appropriate to the video adapter. So, if a person's computer use depends on using an AMD proprietary video driver, then do not upgrade to 16.04. There will not be one available. Wait & watch until the summer to see what AMD comes up with as regards amdgpu video drivers.

The reason for all of this? Ubuntu 16.04 has a new version of X server that the AMD proprietary video drivers do not like. It is all in the 16.04 release notes. See the section Known Issues.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards.

---

### Post by QIII on 2016-04-21
See my post [here]("http://ubuntuforums.org/showthread.php?t=2321234&p=13473958#post13473958") for a bit of info.

---

### Post by broadcast23 on 2016-04-21
Epic FAIL: I just downloaded the official live DVD and all I get is a monitor that won't turn back on!!
HD6550 AMD GPU (A8 3820 CPU) 2.5GHz

---

### Post by redguy41 on 2016-04-21
[COLOR=#111111][FONT=Ubuntu]Just a quick comment - a clean install worked like a charm - the AMD GPU driver is better than the catalyst in 14.04! At least for this hybrid! ha![/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] 

[/FONT][/COLOR]Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M / R9 M275X/M375X] (rev ff)

---

### Post by sgian on 2016-04-21
I tried out the beta of 16.04 on two different AMD computers, a R5450 and a HD 8370D.  Both were adequate for general use.  It was just gaming that they weren't as good at.

---

