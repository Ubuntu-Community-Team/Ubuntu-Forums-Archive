---
title: "Fresh install question"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by AstroLlama on 2015-05-30
Hi all, my computer is configured for dual boot. When I bought the machine in 2012 and installed ubuntu studio alongside windows 8, I was very nervous because the UEFI/secure boot issue new to me and I didn't know what I was doing. These past 3 years I've been in grad school so I've been rather negligent with upgrades, but now that I'm all through (Masters in classical guitar, \\:D/) it's time to upgrade.

My question is simple, if I do wipe the whole system clean, do I have to install in UEFI mode?

From what I understand if the BIOS requires secure boot and none is found, this risks turning the system into a brick! (I hope I'm wrong about that last sentence)
Ideally I'd like to have Ubuntu on the main partition and eventually experiment new distros alongside it. I believe my system BIOS have have secure boot disabled but in anycase, anything in particular that I should look out for?

Please allay my fears :p

---

### Post by Bucky Ball on 2015-05-30
> **AstroLlama said:**
> 

My question is simple, if I do wipe the whole system clean, do I have to install in UEFI mode?

No.

> **AstroLlama said:**
> ... if the BIOS requires secure boot and none is found, this risks turning the system into a brick!

The BIOS doesn't require secure boot. You can switch it off and on.

> **AstroLlama said:**
> Ideally I'd like to have Ubuntu on the main partition and eventually experiment new distros alongside it.

All good, go ahead. One thing to keep in mind is that if you are installing in legacy mode, you are limited to four partition per physical disk. This is easily overcome by creating an extended partition, like a container, into which you can put as many logical partitions as you like. The laptop I'm currently using is legacy and I have four installs and around 12 partitions. Linux will live happily on a logical partition inside the extended partition, Win will not.

EFI mode has its advantages, if you see them as advantages. You are not limited to having four partitions only. You can have as many primary or extended partitions as you like (to the capability of your hardware I guess, there may be a theoretical or actual limit).  

> **AstroLlama said:**
>  I believe my system BIOS have have secure boot disabled but in anycase, anything in particular that I should look out for?

Not that I can think of. Would need to be looking at your BIOS to see exactly how you go about switching off secure boot and making sure you're booting in legacy. 

I would wait for another poster to confirm my answers as I'm no EFI expert, but from what I've picked up in my travels and my experiences with just installing Ubuntu using UEFI for the first time, I'd be reasonably close. Hope that helps. 

(PS: I've started my Master of Philosophy (musicology/ethnomusicology) this year. Congratulations on your recent achievement. I know how much work is involved. Not braving the PhD or that comes later? ;))

---

### Post by grahammechanical on 2015-05-30
Here read the wiki page on UEFI

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

[/URL]> 
[LIST]
[*]if Ubuntu is the only operating system on your computer, then it  does not matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]
 

Ubuntu has had signed Linux kernels that meet the requirements for secure boot since the release of Ubuntu 12.10. 

Regards.

---

### Post by AstroLlama on 2015-05-31
Thanks for the info, I read through the links and feel more confident now! :)

---

