---
title: "Kernel upgrade failed"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by steelaz on 2008-06-23
Today my Update Manager among other updates offered to upgrade kernel to 2.6.24-19. I thought it was  strange, since I already was running 2.6.24-19, but I chose to upgrade  anyway.

While installing new kernel, Update Manager stopped (failed) and an error message saying something about dependencies.

It didn't ask me to reboot, but I did so anyway. After booting up, Ubuntu warned that it will use "Low graphics mode", sound was gone too etc.

Now I booted into 2.6.24-18 and everything works fine.

Should I just wait for 2.6.24-20 and upgrade then or do something about this?

---

### Post by onero on 2008-06-23
> **steelaz said:**
> Today my Update Manager among other updates offered to upgrade kernel to 2.6.24-19. I thought it was  strange, since I already was running 2.6.24-19, but I chose to upgrade  anyway.

While installing new kernel, Update Manager stopped (failed) and an error message saying something about dependencies.

It didn't ask me to reboot, but I did so anyway. After booting up, Ubuntu warned that it will use "Low graphics mode", sound was gone too etc.

Now I booted into 2.6.24-18 and everything works fine.

Should I just wait for 2.6.24-20 and upgrade then or do something about this?

well, you can try dropping into -18 and reinstalling the -19 kernels from there, since they might not have installed correctly. Try removing all the -19 packages completely, and then upgrade again.

Regarding low graphics mode, what video drivers do you use? Usually when you upgrade the kernel while using binary drivers, you have to reinstall the drivers as well. If 2.6.24.18 works fine, you can use that in the meantime, it shouldn't be a problem. If you want to use the latest kernel and are using an NVIDIA card, you can try downloading and installing the latest drivers from the Nvidia site. You have to just download them, reboot into the Recovery Mode for the latest kernel, and run sh <your downloaded driver>.

The downside of manually installed drivers is that you have to reinstall them with every kernel upgrade; [this]("http://ubuntuforums.org/showthread.php?t=835573") post, however, helps to automate the process.

If you're not using an Nvidia card, there are similar instructions on the forums for them, just look around :)

---

### Post by steelaz on 2008-06-23
Thanks onero,

yes, I'm using nVidia card, and Ubuntu was upgrading drivers automatically. I don't necessarily need latest kernel, so if you're saying that it's ok to go back o 2.6.24.18 and use it, I'll do just that.

Thanks for your help.

---

### Post by betto2000 on 2008-06-23
Hi, I am having a similar problem with these updates. I can't boot any more using kernel: 2.6.24-19

These are the updated that were applied last night:

Commit Log for Mon Jun 23 03:13:49 2008  (Ubuntu Hardy 8.04 64 bits)

Upgraded the following packages:
compiz (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
compiz-core (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
compiz-gnome (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
compiz-plugins (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
libdecoration0 (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
libldap-2.4-2 (2.4.7-6ubuntu4.2) to 2.4.9-0ubuntu0.8.04
libpoppler-glib2 (0.6.4-1ubuntu1) to 0.6.4-1ubuntu2
libpoppler2 (0.6.4-1ubuntu1) to 0.6.4-1ubuntu2
linux-headers-2.6.24-19 (2.6.24-19.33) to 2.6.24-19.34
linux-headers-2.6.24-19-generic (2.6.24-19.33) to 2.6.24-19.34
linux-image-2.6.24-19-generic (2.6.24-19.33) to 2.6.24-19.34
linux-libc-dev (2.6.24-19.33) to 2.6.24-19.34
linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.27) to 2.6.24-19.28
poppler-utils (0.6.4-1ubuntu1) to 0.6.4-1ubuntu2
rhythmbox (0.11.5-0ubuntu7) to 0.11.5-0ubuntu8
transmission-common (1.06-0ubuntu5) to 1.06-0ubuntu6
transmission-gtk (1.06-0ubuntu5) to 1.06-0ubuntu6


Everything seemed normal, It just took more time than usual when it was trying to start the kernel upgrade but I didn't see any errors and when finished it asked to reboot as usual. After reboot my sad surprise was that the booting process of Ubuntu remained stall in the beginning just after the message of no resume image found and loading init image..(something like that I can't recall the exact message now).. 

I can boot using the previous kernel 2.6.24-18 however many programs don't work with it now, like VmWare, Openoffice, and trackered as far as I noticed.

Any kind of help will be very appreciated.

Thanks.

---

