---
title: "Best stable relese for 32-bit"
date: 2023-07-03
forum: Installation &amp; Upgrades
---

### Post by esarratt on 2023-07-03
Thank you for the help.

I have been using 14.04 LTS for years and it has worked well, but I need to upgrade.

I am having difficulty figuring out what the latest release is that will work on my 32-bit computer (computer works just fine).

Memory 3.8 GiB
Processor Intel Core 2 Duo CPU P8400 @ 2.26GHz x2
Graphics Mobile Intel GM45 Express Chipset x86/MMX/SSE2
Disk 85.4 GB

Thank you for your help!

---

### Post by Dennis N on 2023-07-03
Debian has a 32 bit release. So does MX Linux, I believe. Of these two, Debian is most like Ubuntu.

---

### Post by esarratt on 2023-07-03
I'd rather stick with Ubuntu.

It looks to me like:Ubuntu 17.10 (Artful Aardvark) is an old Ubuntu release that still works with 32-bit.

What are the problems I will encounter if I just upgrade to this?

---

### Post by guiverc on 2023-07-03
> **esarratt said:**
> Thank you for the help.

I have been using 14.04 LTS for years and it has worked well, but I need to upgrade.

I am having difficulty figuring out what the latest release is that will work on my 32-bit computer (computer works just fine).

Memory 3.8 GiB
Processor Intel Core 2 Duo CPU P8400 @ 2.26GHz x2
Graphics Mobile Intel GM45 Express Chipset x86/MMX/SSE2
Disk 85.4 GB

Thank you for your help!

Please check what machine you're actually using, and its capabilities.

for example, your CPU matches the following I use in QA

```

hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

```

and it's *amd64* and capable of running all current Ubuntu products, including up to *mantic*, though I actually use it mostly in QA-testing of the *lighter* flavors.

Your machine I don't believe is 32-bit, but may have used a 32-bit version of windows, as 32-bit windows was $5 cheaper than 64-bits, and consumers (buyers) understood $5 far more than 32 vs 64 bits.. thus 32-bit windows was sold on lower-end hardware.

---

### Post by Rubi1200 on 2023-07-03
If you post the results of the following command we will be a lot clearer on which architecture you have:
```
uname -m
```

---

### Post by Impavidus on 2023-07-03
Ubuntu 14.04 still has 9 months of Extended Security Maintenance support left – if you signed up for it. Standard support ended 4 years ago. Ubuntu 17.10 has no support whatsoever (it ended 5 years ago) so it's definitely worse than your current system. Please get a supported release. I don't want your computer to get hijacked into a bot network that mounts a DoS-attack on my bank. It looks like that CPU is 64-bit capable.

---

### Post by ActionParsnip on 2023-07-03
It's a 64bit CPU so you can run any modern distribution without issue.

---

### Post by MAFoElffen on 2023-07-03
+1 with ActionParship...

In post #1:
```

Processor Intel Core 2 Duo CPU P8400 @ 2.26GHz x2

```
I have an A1181 MacBook that has an Intel Core Duo T7500 2.2 GHz running Ubuntu 22.04 LTS (amd64). I originally picked it up to do testing for my scripts.

EDIT: What I would do, is backup your user installed applications, data and settings. Then install new OS. Install your user installed applications, restore your configuration settings.

Be aware that some things will not carry forward to current from 14.04. I originally had the Ama-Gi Project based on 12.04 LTS and had not updated anything for a very long time. When my interests saw a need for it again, I decided to pick it back up again, for the, at the time, current LTS, 20.04... Lots of things changed between those versions.

Systemd, Snaps, Python3, GTK2, what was included as the default application suite... Some user installed applications from back then did not survive through the years. So I don't think that the restoration of the configs are as important going that far of a jump in releases. It was too far of a jump, so I just reconfigured things within the new fresh system.

---

### Post by Tadaen_Sylvermane on 2023-07-03
> **esarratt said:**
> I'd rather stick with Ubuntu.

It looks to me like:Ubuntu 17.10 (Artful Aardvark) is an old Ubuntu release that still works with 32-bit.

What are the problems I will encounter if I just upgrade to this?

I'm sure you would but you would be better of sticking with a supported OS release instead of one that is dead and the proper repos are offline. Debian is the better choice here. Changing from 14.04 to 17.10 doesn't help you in the slightest. It will still not get updates and such.

That being said if you could possibly get flatpak backported to 14.04 then it may work fine. Just use flatpaks instead of repo software as needed. Hardly ideal but it could work. Then you don't need to upgrade anything. System still won't be the safest in the world though.

---

### Post by esarratt on 2023-07-03
> **Rubi1200 said:**
> If you post the results of the following command we will be a lot clearer on which architecture you have:
```
uname -m
```

i686

It is 32 bit.

---

### Post by MAFoElffen on 2023-07-04
@ esaratt ---> Oldfred, ActionParship and I confirmed that you can run current amd64 version  Ubuntu or it's flavors. I have about the same cpu in one of my notebooks and it runs just fine.

---

### Post by Impavidus on 2023-07-04
> **Rubi1200 said:**
> If you post the results of the following command we will be a lot clearer on which architecture you have:
```
uname -m
```

> **esarratt said:**
> i686

It is 32 bit.

That only proves that the currently running OS is 32 bit. Better look at```
lscpu
```

---

### Post by esarratt on 2023-07-04
> **Impavidus said:**
> That only proves that the currently running OS is 32 bit. Better look at```
lscpu
```

Wow!  You guys are great!

That command gave me:

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               800.000
BogoMIPS:              4521.96
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K

---

### Post by esarratt on 2023-07-04
> **MAFoElffen said:**
> @ esaratt ---> Oldfred, ActionParship and I confirmed that you can run current amd64 version  Ubuntu or it's flavors. I have about the same cpu in one of my notebooks and it runs just fine.

Excellent!  I was worried I needed to upgrade to a new computer.

---

### Post by MAFoElffen on 2023-07-04
Quick way to test and confirm for yourself: Burn a USB Flash Drive with 22.04.2 amd64. Try to boot it up and do a test drive in the Live Environment.

Mine being a quark, has 32 bit EFI, instead of 64bit EFI, but is a quark. But made it work. Yours is newer than 2007 (that one of mine), so should need not the creativity I went through. LOL

---

