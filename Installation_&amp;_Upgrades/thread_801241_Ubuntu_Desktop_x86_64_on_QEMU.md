---
title: "Ubuntu Desktop x86_64 on QEMU"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by tvynr on 2008-05-20
Hello, all.  I'm an avid Debian user, with installations of Etch on my firewall, desktop, and laptop.  The laptop will be replaced soon and, in the interests of fairness and curiosity, I thought I might give Ubuntu a try on it.  So, at the moment, I have obtained copies of the Ubuntu Desktop Edition installer for x86_64 machines and I am trying to install an instance on QEMU to get a feel for it.  If it seems to have a significant amount to offer over Etch, I may well install it on my laptop.  I'm su```

```re you all know how the distro trial goes.  :)

Well, I can't get it to install under QEMU at all.  The boot menu works fine initially; I select language and then "Install Ubuntu".  And I get the dialog message "Error reading boot CD."

Using the ISOLINUX console and booting the live-install configuration, I get a slightly more informative error message: "Loading isolinux: Disk error 0C, AX = 4200, drive E0".

The command line that I am using to launch QEMU is as follows:

```
qemu-system-x86_64 -hda hda.img -cdrom "/scratch/scratch/Disc Images/Ubuntu 8.04 Desktop Edition AMD64.iso" -m 1024m -boot d
```

Any thoughts?  It doesn't seem likely I'll be installing on real hardware if I can't get QEMU to work; I'm not sure I'm that motivated and I don't have a machine I'd be willing to put to the task at the moment.

---

