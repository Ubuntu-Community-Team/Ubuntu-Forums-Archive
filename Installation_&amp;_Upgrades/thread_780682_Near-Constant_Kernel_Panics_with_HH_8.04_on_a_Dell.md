---
title: "Near-Constant Kernel Panics with HH 8.04 on a Dell Inspiron 1000"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by giddytrace on 2008-05-03
Hello all,

My wife recently received a stock Dell Inspiron 1000 laptop with 256MB RAM from a friend who was no longer using it. As it was running Windows XP very, very slowly, I convinced her to give Ubuntu a try. While I have never used Ubuntu before, my primary computer for three years was a desktop running Mandrake (now Mandriva) Linux so I have a fair bit of experience with the operating system. The only thing that I installed in the computer in terms of hardware was an extra 256MB of RAM and a Cardbus wi-fi card (EDIMAX|EW-7108PCG 54M).

Anyhow, I downloaded a Hardy 8.04 iso, matched the MD5checksum and burned the disc at 4x. Installation went very smoothly, but once we started running the operating system we had the kernel (2.6.24-16-generic) panicking almost constantly (within 15 minutes of startup). I altered my GRUB file to add the "noapic" parameter and the problem seemed to go away for a few days. 

Then we started getting "failure to suspend" notices after bringing the laptop out of suspend and the kernel panics returned. They now happen within a half-hour of the computer being booted and occur during normal activities (simple web browsing, word processing, downloading and installing software). I tried adding the "nolapic" parameter to my GRUB menu as well, but that hasn't done anything that I can tell.

Does anyone out there have any advice? I'm going to try to compile a new kernel, and I'm also going to download Gutsy at a friend's house tonight. But I am willing to hear any and all suggestions.

---

### Post by Pumalite on 2008-05-03
Make sure all your RAM is in use.

---

### Post by Pumalite on 2008-05-03
I dug this up FYI:
[http://www.ubuntu1501.com/2008/02/hardy-heron-alpha-4-on-dell-1501.html](http://www.ubuntu1501.com/2008/02/hardy-heron-alpha-4-on-dell-1501.html)

---

### Post by giddytrace on 2008-05-04
> **Pumalite said:**
> Make sure all your RAM is in use.

Both my bios and sysinfo recognize that all the RAM is there and available for use. I compiled a new kernel with kernelcheck and I have yet to have a panic, but now my wifi and sound are not working and unfortunately, I have limited bandwidth so recompiling is not an option at this point. I did download Gutsy yesterday, so I am going to give that a go. I figure that the worst thing that can happen is I have to reinstall Hardy.

---

