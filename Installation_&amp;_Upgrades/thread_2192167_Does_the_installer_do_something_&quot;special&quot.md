---
title: "Does the installer do something &quot;special&quot; depending on the hardware?"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by negora on 2013-12-06
Hello:

I want to customize an installation of Xubuntu and put it in several machines with different hardware configurations. For the last years I've used a virtual machine to make my customized installation and then I've cloned it into the physical machines with Clonezilla. After that, I've only needed to do some minor adjustments (changing the machine name, the fie system mount points, etc.) and everything has worked well, apparently.

I want to know if doing this I'm missing something "important" of the installation process that depends on the hardware recognition, apart of the installation of certain packages, which I can do by hand later (such as the proprietary nVidia drivers). I know that the initial RAM disk file (initrd) contains enough modules to boot on very different machines, but I mean some kind of change in system scripts, etc.

Thank you.

---

### Post by codenine75a on 2013-12-06
I know only this:
The operating system tries to recognize the hardware but not all hardware is supported.  I believe Ubuntu comes with some nVidia drivers but they may not be the from from the vendor.  Well I cannot say what you are doing is a solid guarantee, so I know the feeling.  It is like an experimental setup.  Your choice.  It is your choice.

---

### Post by negora on 2013-12-06
Hello codenine75a:

Thanks for your answer. If my memory serves me right, *buntu doesn't install the proprietary nVidia drivers by default, but the open source ones (Nouveau). But I can install them by hand after the cloning, in the computers that need them. The package also contains the necessary scripts to make the drivers work without my intervention.

That's why I'm asking if the installer does "something else" related to the hardware, not triggered by the packages their selves. Because as long as all the changes are made by the scripts of the packages, I can reproduce that behaviour installing them manually later. But if they aren't, there may be modifications that I'm missing.

PS: I believe that the installer simply installs a common set of packages and the packages configure what is necessary by their selves. But I may be wrong.

PS2: The kernel configures many things at boot time. I forgot to mention that this is what makes this approach work, compared to Windows, that use the configuration detected during the installation to boot.

---

### Post by coffeecat on 2013-12-06
Generally speaking, if the hardware is supported on the target machines for your cloned system, there will be no problems with booting the clone. I can think of only two caveats offhand, one of which you have already identified:

1 - **Proprietary video drivers**. If your target machines have different video devices, it's much safer to rely on the default open-source drivers when cloning, and install the proprietary drivers afterwards.

2 - **Network devices**. If you install and run the system on one machine and then clone from that, the MAC for the ethernet device on the original machine will be associated with "eth0". Once the clone is booted up on a different machine, its ethernet device will be designated eth1. If that bothers you, you can edit /etc/udev/rules.d/70-persistent-net.rules. There will be a similar story for wireless devices and you'll need to redo the WPA passkey for the new device if you already added the WPA key for the original wireless nic. Also, the Broadcom proprietary STA driver blacklists the open source broadcom driver, if I remember correctly, so you will want to forego installing the STA driver before cloning if the original machine has a Broadcom wireless device.

---

### Post by negora on 2013-12-06
**coffeecat:** First of all, thank you for your answer too ;) .

Yes, that's what I do. In my customized install I try not to add any proprietary driver. I upgrade the packages that are installed by default, get the software that I need and customize some basic features. Then, in the destination machines, I install the more specific packages: nVidia drivers, etc. In other words, I build a common "start point" and then I adapt the clones to the each machine.

However, I've to admit that I wasn't aware of the issue of the network adapter MACs. So I'm taking your advice and I'm going to edit that file, because I'm a little obsessive about that "silly" things, he he he. Thank you for your help.

---

