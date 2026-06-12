---
title: "Kernel upgrade problem"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Phil Doomen on 2010-07-12
I tried to run an upgrade of VirtualBox but it failed as it couldn't find the build files for 2.6.31-20-generic.  After that it went downhill and I went into a bit of a decline....

When I run uname -r I get 2.6.31-20-generic
When I ls the modules directory I get

philip@philip-portege:/lib/modules$ ls
2.6.24-23-generic  2.6.28-17-generic  2.6.32-22-generic
2.6.27-11-generic  2.6.31-20-generic  2.6.32-23-generic
2.6.27-14-generic  2.6.32-21-generic  2.6.32-23-generic-pae

Which indicates to me that kernel updates have been run as part of Update Manager but the system still thinks its on 2.6.31-20-generic. There is a symbolic link to the Build directory in the recent ones but not the older ones.

How can I run/re-run a kernel update or tell the kernel it is running 2.6.32-23-generic so that I can get VirtualBox running again?

Thanks for your time
Phil

---

### Post by pytheas22 on 2010-07-13
Did you reboot after updating the kernel?  Unlike most other updates, kernel updates can't take effect until the system is fully rebooted.

I've never heard of uname being wrong, so if it says you're running 2.6.31-20-generic, that's what you're running.

---

### Post by Phil Doomen on 2010-07-13
Could be right I suppose.  Yes I have re-booted many times.  I only realised I had a problem when I tried the VirtualBox upgrade.  Any ideas on where to get the build files for my version?  That will get me going again and not have to worry about whether uname is right or not.  I can't find any reference to them searching the net.

---

### Post by pytheas22 on 2010-07-13
Running:
```

sudo apt-get install build-essential
```

should install all of the build dependencies you need for making the vboxdrv modules, I think.  If this package is already installed but you still don't seem to have kernel headers for your currently running kernel, you could try reinstalling the package with:

```
sudo apt-get install --reinstall build-essential
```

Also, this isn't a custom-compiled kernel that you built yourself or anything like that, is it?  It's just a kernel that you got through normal Ubuntu updates?

---

### Post by drs305 on 2010-07-13
Sometimes when I'm switching around with various kernels I have to ensure the linux-headers for the new kernel are installed.

---

### Post by Phil Doomen on 2010-07-14
Solved it!  For some reason my grub menu.lst was not updating so I have been running the old kernel instead of the new one.  I found somewhere a thread for something similar that said to run update-grub and I figured it couldn't hurt.  It found the other kernels but when I rebooted none of them showed in the grub menu.  By running sudo gedit /boot/grub/menu.lst I manually edited the kernel to load and voila!  VirtualBox loaded like a charm because I had the build files for this kernel and life is good again :-)

Thanks for your help

---

