---
title: "Installed lubuntu latest, then Ubuntu 18.04. No choice on boot - boots into lubuntu"
date: 2022-04-17
forum: Installation &amp; Upgrades
---

### Post by testingwithfire on 2022-04-17
Hi all,

Returning to the Ubuntu world after several years away.

I have an Intel NUC with an SSD and an attached USB drive that serves as /dev/sdb. The boot drive is on /dev/sda.

The other day I first installed the latest release of lubuntu and it went well. 

Unfortunately my job requires Amazon WorkSpaces, which runs only on Ubuntu 18.04. So I prepared a new USB stick with Ubuntu 18.04 LTS. 

The Ubuntu 18.04 installer recognized that lubuntu was present and appeared to install successfully alongside it.

When I rebooted, I didn't even get the grub text boot screen that I'm used to: it booted right into lubuntu. 

Not sure how to proceed? Mount /dev/sda from the USB stick and edit the bootloader?

---

### Post by TheFu on 2022-04-17
Something to research - how new is the NUC hardware?  18.04 HWE kernels stop at 5.4.x, so if the NUC is too new, the hardware may not work.  The good news is that you can run 18.04 inside a 20.04 virtual machine for whatever Amazon WorkSpaces is. Heck, might be able to run it in an 18.04 lxd container to be faster and use 1/10th the resources that a VM needs.

I truly hope you didn't install into sda or sdb directly. OSes need to be installed into partitions.

BTW, "Lubuntu latest" doesn't exactly tell anyone the release.  We don't know what you think the latest is.  The latest LTS is 20.04.  The latest short-support is 21.10.  The latest beta is 22.04b.  Each of those are very different.  When posting, it is most helpful to be very clear on the releaase and if it is a GUI issue, which DE/WM are being used.  Most of the time, **lsb_release -d** will provide the release number. As for the DE and WM, I'd use **inxi** to get that, but there must be another way.

When people say "Ubuntu 18.04" we're supposed to assume the Gnome3 DE as default. I think it is the only 18.04 desktop that is still supported. The other flavors lost support about a year ago.  I just checked and Xubuntu and Lubuntu 18.04 support both ended in Apr 2021.

As for providing more information, there's a system info script here: [https://github.com/UbuntuForums](https://github.com/UbuntuForums)   Get that and run it, then someone else can look at the output to explain what's on the system and what isn't.  Hopefully.

MSFT really screwed over so many people by calling "partitions", "drives."  That really is too bad.  On Windows, a drive letter is actually a partition, but only MSFT uses that term. No other OS does.

---

### Post by grahammechanical on 2022-04-17
From Lubuntu try this command and see if the print out includes Ubuntu as an option.

```
sudo update-grub
```

The second installed Linux (Ubuntu) should have put its version of Grub in charge of the boot process with Ubuntu at the top of the list of OS to boot. But your system boots into Lubuntu. If Ubuntu shows up in the print out of update-grub then run this command:

```
sudo grub-install /dev/sda
```

See if that improves things.

Regards

---

