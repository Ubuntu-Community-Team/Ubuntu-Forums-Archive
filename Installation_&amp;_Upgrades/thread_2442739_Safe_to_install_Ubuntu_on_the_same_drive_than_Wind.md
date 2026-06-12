---
title: "Safe to install Ubuntu on the same drive than Windows?"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by wastefulmouth on 2020-05-07
Hi, I'm not completely new to Linux, I've installed Ubuntu a couple of times with the latest installation being some months ago (probably 2 years?) and used it. But every time I've installed it I have done it in a separate hard drive than Windows. Now my question is: is it safe (and it is possible) to install Ubuntu or whatever GNULinux distribution together in the same drive where Windows is installed? Of course I'm talking about different partitions but I was wondering knowing how Microsoft is and how Windows is, maybe with the latest Windows this is not possible or at the very least not recommended to do. I have read people calling for help because somehow their Linux or Windows installation has gone from GRUB or something along those lines.

I would love to use Ubuntu again but I don't have a drive where to install it except the one I'm using for Windows so this is why I'm asking this.

Thank you.

---

### Post by Impavidus on 2020-05-07
Yes, you can install both on the same hard drive. I did that the first time I ever installed Ubuntu, back in 2006. Since the change to UEFI (for preinstalled Windows that happened in 2012) it has become more reliable, as now the Windows and Ubuntu boot loaders can live side by side in the EFI partition. On the other hand, for Windows 8 and later on non-UEFI systems it's a bit risky. If you do have multiple harddrives of similar performance, it may still be a good idea to put Ubuntu and Windows on separate drives.

---

### Post by CatKiller on 2020-05-07
Yes, it's possible. Lots of people do so with no problems. With any operation where you're fiddling with things, things can go wrong, so backing up anything important before you start is a very sensible precaution.

Ubuntu needs the drive to be in AHCI mode (rather than RAID or anything else) to be able to use it, but Windows needs a driver to be installed (before you do it) to be able to use a drive that's in AHCI mode.

Windows also doesn't shut down properly. It simply hibernates to mask its long boot up time. They call this Fast Startup, and it leaves the partitions marked dirty. Ubuntu won't touch the partitions while they're in this state, since doing so would break them. So you need to turn off Fast Startup in Windows, being aware that Windows updates will sometimes silently turn it back on.

You'll also need to know whether your Windows install is done in BIOS mode or UEFI mode, so that you can install Ubuntu in the same mode (which will also need to be the same mode that you boot your USB stick or DVD in). If your Windows was pre-installed it'll be UEFI, but if you did it yourself it could be either. UEFI is preferable, but either can be made to work. 

Once you've done those things, resizing your existing Windows partition and installing Ubuntu alongside it is simply one of the standard options in the Ubuntu installer.

---

### Post by yancek on 2020-05-07
Ubuntu documentation on dual booting with windows 10 (guessing that is what you have as you do not indicate which release?) at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by scriber on 2020-05-07
> **CatKiller said:**
> Windows also doesn't shut down properly. It simply hibernates to mask its long boot up time. They call this Fast Startup, and it leaves the partitions marked dirty. Ubuntu won't touch the partitions while they're in this state, since doing so would break them. So you need to turn off Fast Startup in Windows, being aware that Windows updates will sometimes silently turn it back on.

I've noticed you post this before, and it really irks me then way you word it.

Windows 10 boots in less than 10 seconds with Fast Startup disabled.

The way you word it implies that Windows will take a long time to boot when Fast Startup is disabled.

---

### Post by CatKiller on 2020-05-07
> **scriber said:**
> I've noticed you post this before, and it really irks me then way you word it.

Windows 10 boots in less than 10 seconds with Fast Startup disabled.

The way you word it implies that Windows will take a long time to boot when Fast Startup is disabled.

That *is* why they do it. How you or I would class Windows' boot time is irrelevant.

---

### Post by wastefulmouth on 2020-05-07
> **Impavidus said:**
> Yes, you can install both on the same hard drive. I did that the first time I ever installed Ubuntu, back in 2006. Since the change to UEFI (for preinstalled Windows that happened in 2012) it has become more reliable, as now the Windows and Ubuntu boot loaders can live side by side in the EFI partition. On the other hand, for Windows 8 and later on non-UEFI systems it's a bit risky. If you do have multiple harddrives of similar performance, it may still be a good idea to put Ubuntu and Windows on separate drives.

> **CatKiller said:**
> Yes, it's possible. Lots of people do so with  no problems. With any operation where you're fiddling with things,  things can go wrong, so backing up anything important before you start  is a very sensible precaution.

Ubuntu needs the drive to be in AHCI mode (rather than RAID or anything  else) to be able to use it, but Windows needs a driver to be installed  (before you do it) to be able to use a drive that's in AHCI mode.

Windows also doesn't shut down properly. It simply hibernates to mask  its long boot up time. They call this Fast Startup, and it leaves the  partitions marked dirty. Ubuntu won't touch the partitions while they're  in this state, since doing so would break them. So you need to turn off  Fast Startup in Windows, being aware that Windows updates will  sometimes silently turn it back on.

You'll also need to know whether your Windows install is done in BIOS  mode or UEFI mode, so that you can install Ubuntu in the same mode  (which will also need to be the same mode that you boot your USB stick  or DVD in). If your Windows was pre-installed it'll be UEFI, but if you  did it yourself it could be either. UEFI is preferable, but either can  be made to work. 

Once you've done those things, resizing your existing Windows partition  and installing Ubuntu alongside it is simply one of the standard options  in the Ubuntu installer.

Thanks you both for the information!

One of the first things I always do when  I reinstall Windows is disable Fast Startup, so for that part I'm good  to go. I've also checked on msinfo32 just to be completely sure and my installation  is in fact in UEFI mode. So, check and check. Now, about the AHCI mode, it is  set in the BIOS (UEFI) right? I remember I have it set in AHCI but I  better check first.

And last question: Does that feature about not touching the partitions if the machine has been hibernated from Windows is kinda new? Because I remember once when I had Ubuntu (or maybe it was another distro) and Windows in dual boot and I hibernated the computer, the next time I activated it the GRUB showed up and asked me what I wanted to boot to.

---

### Post by CelticWarrior on 2020-05-07
If it was in AHCI when you installed Windows then it installed with the proper support for AHCI. No other change is required.

Yes, Fast Startup is a new thing.

---

