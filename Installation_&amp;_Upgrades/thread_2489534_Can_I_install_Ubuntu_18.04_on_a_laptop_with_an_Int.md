---
title: "Can I install Ubuntu 18.04 on a laptop with an Intel Core i9 Gen 13 ?"
date: 2023-08-01
forum: Installation &amp; Upgrades
---

### Post by fiwz789 on 2023-08-01
Can I install and use Ubuntu 18.04 on a laptop with an Intel Core i9 Gen 13. Because I concern about performance or bug from old OS with new hardware.

PS. I want to use  Ubuntu 18.04 with specific software.

---

### Post by guiverc on 2023-08-01
You're asking about a release from 2018-April (thus 18.04 using the *year.month* format of Ubuntu releases), which for some ISOs that's the age of the included stack (*some ISOs include later stacks up to 2020-April*).

Server ISOs do not change the kernel stack by default; they use the most *stable* option which is also the oldest, Desktop ISOs upgrade the stack over the first two years which is why a later option exists; either way it stops with the 20.04 GA stack.

Regardless, you're asking about [a release that ended it's *standard support*]("https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/"), thus no longer receives security patches (*though parts of the system do have ESM security options*). You weren't specific as to what 18.04; thus if you're asking about the 2018-April or 2020-April kernel stack; but either way neither are very modern.

You're using it offline I assume too.

---

### Post by fiwz789 on 2023-08-01
Yes, I will using it offline. I just use AMR's study and development (in-house).

I'm just worried that once the Ubuntu is installed, it can be used normally or not ???

---

### Post by guiverc on 2023-08-01
All releases can be used[I] if you hardware can cope with the installed stack

[/I]There is  Ubuntu 18.04 media available using initial 4.15 kernel (2018-Aprl), 4.18 (2018-October), 5.0 (2019-April), 5.3 (2019-October) or 5.4 (2020-April; two ISOs were created with this stack; the second because of *boothole *vulnerability).

I have no knowledge about your hardware, and given 18.04 is **EOSS** (*end of standard support*) I have no intention of looking for you (*it's unsupported though paid support options exist*). 

FYI:  I still have a *bionic* or 18.04 system I've yet to deal with, if I was to turn it on it'll work, but I'll be re-installing a different system over it next time it's turned on I suspect (*its not high priority thus why its still got 18.04 on it; I've used it three times thus far since EOSS, ie. it didn't explode when EOSS was reached!*).

If your system is *patched* for *boothole* (*likely*) and you're using Secure-uEFI you're limited though to only the GA (4.15) or *latest* HWE stack (5.4) anyway.

You are aware less resources are available for the EOSS release; ie. many PPAs people rely on only support the *standard support* LTS releases (*20.04 & 22.04 currently*); thus resources that **existed** for 18.04/*bionic* when it was fully supported have been dropped; but you can of course compile that code yourself (*instead of downloading per-compiled binaries) *, but I'm talking about 3rd party software here.

---

### Post by ActionParsnip on 2023-08-02
Why such an old release?

---

### Post by MAFoElffen on 2023-08-02
My workstation is i9-13900K, with Z790 chipset. I run 22.04.2 with the HWE Stack.

The problem you will face is the kernel series not only supporting the CPU, but the Chipset that supports the CPU, which affects how it deals with the memory, the PCI buss, which then extends to the your storage, network, and USB controllers.

Release 22.02.2 Desktop works out of the box with that Gen iCore. Which is more than I can say for Windows 10/11. For that, I have to load the Motherboard's drivers for Windows to recognize the hardware at all.On a fresh Win install, the device manger has a very long list of what isn't recognized. So yes, Linux was much more compatible, with my (new) hardware than Windows was.

I would doubt that 18.04, even if you went with 18.04 Desktop with the HWE stack, and converted it to Server Edition, is going to support the hardware. It would be a challenge, even with 20.04. 

As a test, later today, I could boot some older Server & Desktop ISO's and see if they boot/run on it.

---

### Post by mIk3_08 on 2023-08-03
> **fiwz789 said:**
> Can I install and use Ubuntu 18.04 on a laptop with an Intel Core i9 Gen 13. Because I concern about performance or bug from old OS with new hardware.

PS. I want to use  Ubuntu 18.04 with specific software.
In my opinion. I prefer to use the latest release of Ubuntu or the 22.04 LTS. As a user of 22.04 LTS so far so good. It didn't give me any headache so far. Performance, it was best so far. Fast and stable. No problem with any of my attached devices like, printer/scanner, usb extended storage, mic, sounds and etc. Hope you will like it when using it. Regards and cheers.

---

### Post by MAFoElffen on 2023-08-03
> **fiwz789 said:**
> Yes, I will using it offline. I just use AMR's study and development (in-house).

I'm just worried that once the Ubuntu is installed, it can be used normally or not ???
I have another solution for you.. 

Run 22.04 on your hardware.

Run KVM to host your AMR study and research development suite. <-- On whatever it requires in a VM Guest...

KVM will let you tweak the Guest's hardware to older or even to other platforms. That way is also isolated and in a sandbox.

I am not familiar with that software suite and the requirements of what it will run on, but with KVM, you have a lot more options opened up to you.

18.04 is Systemd, and Python3. If an application runs on 18.04, it may run on later. With KVM, you could test that easily, and not lose what you have if it doesn't. That is part of the reason I "test things" inside of KVM Guests. That 'and' the i9 has 20 cores, that can provide 20 vCPU's. It is perfect for hosting virtualization.

I have some programs that only run on DOS, OS2, Windows 95, or Ubuntu 8.04 installed and running safely on VM Guests in KVM.

---

