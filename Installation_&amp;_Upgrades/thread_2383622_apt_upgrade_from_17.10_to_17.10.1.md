---
title: "apt upgrade from 17.10 to 17.10.1?"
date: 2018-01-27
forum: Installation &amp; Upgrades
---

### Post by SeanOB on 2018-01-27
Can I use apt to upgrade from 17.10 to 17.10.1?
I have a thinkpad so want to be super cautious. Stopped using the machine as soon as the issue was announce - and I want to start using it again.

Thanks!
SeanOB

---

### Post by deadflowr on 2018-01-27
From the 17.10 [release notes]("https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Incompatibility_with_BIOS_in_certain_Lenovo.2C_Acer_systems"):
> If you have already installed Ubuntu 17.10 on an affected system, you may not immediately notice this problem because Ubuntu will continue to boot from disk. To verify whether your system has been affected by this bug, create a USB stick with the Ubuntu 16.04 desktop image and try to boot it. If you are able to boot it, your system has most likely not been impacted by this bug. 
Double check the bug as well to see if your machine was affected:[lpbug]1734147[/lpbug]

But running apt update/upgrade on an already installed system should turn the buggy driver off.
(or remove or disable the driver, which ever term you like best)

---

### Post by SeanOB on 2018-01-27
Thanks. I'll check.

Meanwhile - on another of my machines - it is currently 17.10 .. and I can't figure out how to get it to 17.10.1.
apt upgrade
apt-get dist-upgrade
do-release-upgrade
..
none yield 17.10.1

-SeanOB

---

### Post by deadflowr on 2018-01-27
I don't think the base-files changed so it should still show 17.10.
17.10.1 is not a typical point release, so the 17.10.1 designation seems to only reflects that the installer is 17.10.1 to differentiate from the original, broken, installer.
(Unfortunately I no longer have any 17.10 installs so I cannot verify that)

What kernel are you on now with it?
```
uname -r
```
i believe anything newer than -21 at the end is updated without the bug.

(And I think you really want to be on -32 or -31 as that has the latest patches for the Meltdown/Spectre bugs.)

Just some random thoughts

---

### Post by PaulW2U on 2018-01-27
> **SeanOB said:**
> 
none yield 17.10.1
Don't worry too much about version numbers.

As far as I am aware '17.10.1' referred to the install ISOs rather than the version of Ubuntu that is actually installed. I have two laptops which are both fully updated. Both identify as Ubuntu 17.10 using the 'lsb_release -a' command.

---

### Post by SeanOB on 2018-01-27
Ah..
Kernel is -32
lsb_release -a reports 17.10 (which is what confused me)

Ok - I'll just apt upgrade my thinkpad and hope for the best (but I'll check to see if it can boot from usb first ..)

---

