---
title: "Kernel updates? When, how, etc?"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by sgofferj on 2015-02-25
Hi,

although I'm a long years Linux user, I'm new to Ubuntu so please forgive if the question appears naive...
According to announcements, there's now 14.04.2 which includes kernel 3.16. Running kubuntu 14.04 (without any extra dots), I just today got an update for yet another 3.13 kernel. Now I'm wondering a bit how this "long term support" concept - which by the way was one of my primary reasons to come from Opensuse to Ubuntu - works.
To get the 3.16 kernel, do I have to download the installation media and do an update from DVD? Or will the 3.16 kernel eventually appear in the normal 14.04 repos and be installed by the system update agent?

-S

---

### Post by fantab on 2015-02-25
How are you updating or upgrading?

From command line I would:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

I don't think 14.04.2 is out for release yet, AFAIK its still being tested.
*buntu repositories will be same for 14.04 and or 14.04.2 and eventually you will get 3.16 kernel.

---

### Post by Topsiho on 2015-02-25
Ubuntu 14.04.2 is available for some days by now :).

The long term concept includes that updates of the kernels stick at the older numbers, to avoid breaking software, that might occur otherwise.

I don't know the exact numbers, but it may well be true that 14.04 uses 3.13 kernels, and 14.04.2 uses a 3.16 kernel.
If your computer runs OK with 3.13, and you have not the latest and greatest of hardware, there is no point replacing 3.13 with a 3.16 kernel, or even a release candidate of the 4.0 kernel (which is out too), unless you just WANT to, which is perfect, and if you don't mind breaking your system.

If you want the 3.16 kernel, you might consider a clean install of 14.04.2 (on my computer it would take 7 minutes + the time needed for downloading, burning, checking and answering some questions).

Topsiho

---

### Post by ajgreeny on 2015-02-25
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for all the info on these upgrades.

If you want to go ahead you need to run ```
sudo apt-get install linux-generic-lts-utopic xserver-xorg-lts-utopic libegl1-mesa-drivers-lts-utopic xserver-xorg-video-all-lts-utopic xserver-xorg-input-all-lts-utopic
```and if you use a 64bit system with UEFI you need the added ```
sudo apt-get install linux-signed-generic-lts-utopic 
```

---

### Post by grahammechanical on 2015-02-25
My advice is to stay where you are if you want long term support.

The Linux 3.13 kernels are supported with security fixes until 2019. Where as the Linux kernel 3.16 on 14.04 will only be supported until the August after 16.04 has been released. And that is twice as long as the 3.16 kernel in Ubuntu 14.10 will get.

This is why a normal update to 14.04 will bring in 14.04.2 but not what is called the hardware enablement stack which includes later kernels. We have to install the hardware enablement stack by running the above mentioned commands.

If you move on to the hardware enablement stack and kernel 3.16 that comes with a new install of 14.04.2 then you will have to move on to the enablement stack of 14.04.3 and 14.04.4 and 14.04.5 to get kernel support until April 2019.

Now, there is nothing wrong with doing that. But you should know that you will need to do that to get the full 14.04 LTS support period. Look at the charts at the bottom of this wiki page.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

