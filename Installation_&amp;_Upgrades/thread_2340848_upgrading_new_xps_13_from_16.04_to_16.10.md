---
title: "upgrading new xps 13 from 16.04 to 16.10"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by jmogey on 2016-10-22
I recently received a dell xps 13 9360 with 16.04 pre-installed and am wondering about upgrading to 16.10. I am unsure whether there are special dell hardware tweaks I should be aware of or whether a stock 16.10 would install on the hardware. I also wonder if the difference between 16.04 and 16.10 is slight enough that it doesn't make sense to do this upgrade. I'd appreciate thoughts about this. Thanks.

---

### Post by monkeybrain20122 on 2016-10-22
The question of whether a vanilla Ubuntu iso would work is an interesting one. But why would you want to upgrade if it is working? 16.04 is barely 6 months old. New releases usually are somewhat buggy and in this case it is supported for only 9 months. To check whether you can install, you can try install it in an external hard drive ad boot off the xps That way you can test to your heart's content without having to risk your working system. If you can afford an xps you can probably get an external hard drive if you don't have one already.

---

### Post by RobGoss on 2016-10-22
If you have 16.04, on that machine I would stick with it there's not much of a difference in 16.10, that would make me upgrade and 16.04 is a LTS distributions which has longer support

---

### Post by changke on 2016-10-24
I received my XPS 9360 last week and wiped out the pre-installed 16.04 system because I don't like Dell's default partition schema.

I've tried installing Mint 18 (Kernel 4.4) but the result is miserable: no WiFi, no sound, no proper video acceleration. The hardware of Kaby lake is too new for 4.4 kernel.

By 16.10 however, everything works out-of-the-box.

---

### Post by Bucky Ball on 2016-10-24
> **RobGoss said:**
> If you have 16.04, on that machine I would stick with it there's not much of a difference in 16.10, that would make me upgrade and 16.04 is a LTS distributions which has longer support

Everything about this. If 16.04 LTS is working fine I'd think twice about upgrading to an interim release that has only been out a week or two just because you can. The latest is not always the greatest and I'd stay right there. 16.04 LTS is stable and has five years support. 16.10 has nine months (which equates to upgrading every six months basically) and is teething.

---

### Post by jmogey on 2016-10-24
One reason I thought about 16.10 is that like Changke I want to change the partition set-up. I have a 128 GB ssd set up as two partitions, one / and the other a 32 GB swap. I see no reason to have such a large swap for 8GB ram and want a dedicated /home. The LTS issue is not a big deal for me as I'm pretty careful of upgrades, usually waiting a month or so after a new version. I've been a long time Opensuse user on my main desktop so I'm used to an upgraded system every year or so.
 The issue of stock kernels and drivers is one of my main concerns. From the problems noted with Mint 18, this XPS 9360 16.04 system does not use stock drivers. So, I wondered is a stock 16.10 without special drivers would work.

I should have noted is that the first thing I did with this was to shrink the / partition and add a /home partition.

---

### Post by changke on 2016-10-24
> **jmogey said:**
> So, I wondered is a stock 16.10 without special drivers would work.

I am replying from my XPS 9360 with stock Ubuntu 16.10. And yes, it just works, no additional 3rd-party drivers / PPAs needed even in Live-Mode. The whole process is a breeze.

I don't think the pre-installed 16.04 used any special drivers, because the Dell people have stated they have upstreamed all patches for the 9360 hardware, I didn't test, but I assume the Mint 18 issue lies in the fact that it is based on 16.04 without SP1, so the kernel is outdated. I've seen people in Mint Forum saying after a kernel update the Intel video-card works but not the WiFi.

Anyway, I'm pretty ok with short-term-support system, all my works are in the cloud so reinstalling system is nothing bad for me.

---

### Post by Bucky Ball on 2016-10-24
In that case, boot to a live session (boot the install media and 'Try Ubuntu') then launch Gparted from a desktop and resize the partitions. Instead of a /home you could simply create a /data partition and symlink the folders in /home partition inside / to that. Just throwing up a perhaps less involved option.

(I have three installs all linked to the same data partition and all using the same /swap. And yes, 32Gb is WAY to big. You don't need much more than 2 or 4Gb.)

It goes without saying but I'll say it anyway: backup your valuables before proceeeding much further. ;)

---

