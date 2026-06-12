---
title: "&quot;suspend&quot; not working in ubuntu 8.04"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by hardy113 on 2009-11-28
I've just installed ubuntu 8.04 LTS on my HP nc6320 (Intel 945GM Express chipset / GMA 950 graphics).

Everything works fine except suspending. The computer suspends but the wakeup is not working correctly (results in a black screen) - however hibernating works fine!

I tried a couple of things to get it working although i cannot describe myself as an experienced ubuntu user.

What i did so far:

- installed a package called hibernate (didn't change anything)
- made some changes to /etc/default/acpi-support (found it with google, didn't help)

My google research led to users with similar problems but mostly related to "special" chipsets graphics cards.

If someone could help me to solve this that would be much appreciated.

Thank you in advance!

---

### Post by hardy113 on 2009-11-28
Ok, looks like i've found the answer to this problem... in the form of a known bug in 8.04 which hasn't been solved yet:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219657)

Workarounds and ideas are still welcome.

---

### Post by presence1960 on 2009-11-28
> **hardy113 said:**
> Ok, looks like i've found the answer to this problem... in the form of a known bug in 8.04 which hasn't been solved yet:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219657)

Workarounds and ideas are still welcome.

In BIOS if you have suspend settings enable S1 & S3

---

### Post by hardy113 on 2009-11-29
> **presence1960 said:**
> In BIOS if you have suspend settings enable S1 & S3
It's not BIOS-related, I have windows on the same laptop and S3 standby works very well. It must be the bug mentioned in this error report, however an official patch obviously doesn't exist (yet).

---

### Post by presence1960 on 2009-11-29
> **hardy113 said:**
> It's not BIOS-related, I have windows on the same laptop and S3 standby works very well. It must be the bug mentioned in this error report, however an official patch obviously doesn't exist (yet).

just checking, mine did not work until I enabled S1 & S3 in my BIOS.

---

### Post by hardy113 on 2009-11-30
> **presence1960 said:**
> just checking, mine did not work until I enabled S1 & S3 in my BIOS.
I've already checked it but i don't have any options in the bios to configure the standby mode. I've only a few settings that can be configured in my bios, but almost no ACPI settings (only wakeup events).

---

