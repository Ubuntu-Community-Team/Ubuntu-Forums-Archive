---
title: "Gutsy not detecting drive in docking station"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by a__l__a__n on 2007-11-12
I have a Thinkpad 600x and a Selectadock II docking station with an IDE drive in the docking station.  I have been using this setup for years, under Win2000, then Xandros, then Kanotix (several generations), and Sidux.  Recently I've installed Ubuntu 7.10 on the laptop.  But Ubuntu does not detect the docking station hard drive during boot.

I can boot the machine from an older live CD and mount partitions from the docking station drive, so I know the hardware is ok.  

Can someone give me pointers on how to debug this difficulty?

Thanks!

---

### Post by ddrichardson on 2007-11-12
Can you mount it from the command line? If so then it could be added to /etc/fstab

---

### Post by a__l__a__n on 2007-11-12
No, I cannot mount it because /dev/sdb is not detected.  

sudo fdisk -l

only shows the partitions on /dev/sda, which is the main drive inside the laptop.

---

### Post by ddrichardson on 2007-11-12
does lshw/lspci show the device as connected?

---

### Post by a__l__a__n on 2007-11-12
No, the docking station IDE is not shown in either lscpi nor lshw.    

The following from dmesg might provide a clue:

[   34.048079] PCI: Probing PCI hardware
[   34.048103] PCI: Probing PCI hardware (bus 00)
[   34.048825] PCI quirk: region ef00-ef3f claimed by PIIX4 ACPI
[   34.048839] PCI quirk: region efa0-efaf claimed by PIIX4 SMB
[   34.048853] PIIX4 devres C PIO at 15e8-15ef
[   34.048863] PIIX4 devres I PIO at 002e-002f
[   34.049623] PCI: Transparent bridge - 0000:00:04.0
[   34.053218] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   34.053354] PCI: Cannot allocate resource region 0 of device 0000:08:00.1
[   34.053416] PCI: Cannot allocate resource region 1 of device 0000:08:00.1
[   34.053472] PCI: Cannot allocate resource region 2 of device 0000:08:00.1
[   34.053527] PCI: Cannot allocate resource region 3 of device 0000:08:00.1

The last four lines appear on the screen early in the boot sequence when booting docked, but do not appear when booting undocked.

---

### Post by ddrichardson on 2007-11-12
Try passing the following to the kernel (by editing grub.lst)```
acpi=off
acpi=noirq
 pci=routeirq
```individually and let us know if any of them help - it will point us in the right direction.

---

### Post by a__l__a__n on 2007-11-12
Thanks for hanging in there with me.

Those boot options do not help. I've tried a long list of boot options I found in various online discussions but to no avail.  (noapic, noirqdebug, noacpi, nolapic, nosmp, irqfixup, acpi=noirq, pci=biosirq, lapic, acpi=force, pci=direct, irqpoll, pnpbios=off, pci=nobios ...

By the way, the Xubuntu 6.10 live cd detects the docking station drive just fine.  The Xubuntu 7.10 live cd does not (itseems to behave just like the installed 7.10).

---

### Post by a__l__a__n on 2007-11-12
Perhaps my problem is related to[ _**this one**_]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133666")
[URL="http://ubuntuforums.org/showthread.php?t=586894"]
_**Here is another thread on that problem**_[/URL]

Assuming that is the cause of my problem...  I am not eager to patch and compile the kernel to fix my problem.  Any idea whether an update will be pushed out to fix this?  Or will I have to wait for the next major release of Ubuntu? (and when would that be expected?)

---

### Post by ddrichardson on 2007-11-13
Kernel's have been known to break between releases, if patching the kernel will solve the problem, it's not that difficult, you just need to download a few development libraries and the kernel source, everything is selected using a menu.

The alternative is to register a bug and hope it gets fixed upstream - however kernel updates are not always released as frequently in Ubuntu as they are in the kernel project - because they often change something to fix a bug and break something else. You could wait for Heron but the bug may still be there. I'd patch the kernel personally.

---

### Post by a__l__a__n on 2007-11-13
Can you point me to instructions for patching the kernel?

---

### Post by ddrichardson on 2007-11-13
You could download and compile the [latest]("http://www.kernel.org/") kernel source in which this patch is now incorporated.

---

### Post by a__l__a__n on 2007-11-13
I don't know what configuration options to pick.  Also, I have installed Truecrypt using the deb package created for Gutsy.  I suspect I now need to build Truecrypt for the new kernel.  And I don't know what else I have on this machine with similar dependencies.  This looks like a mine field for someone who is not familiar with building Linux systems from source.  And I'm not even certain that doing all of this will fix my problem.

I installed Ubuntu because I thought it would "just work".  This is now expanding into a lot more than I bargained for.   I think I'll wait for the next release.

---

### Post by ddrichardson on 2007-11-13
Don't be put off. For some reason every one seems to thing kernel compilation is difficult. It isn't. If you don't know if you need it, build it as a module and it'll be loaded as needed. You can have multiple kernels installed and selected from grub so if it goes pete tong then you can get back in and recompile.

---

### Post by a__l__a__n on 2007-11-13
I do appreciate your help and encouragement.  

Maybe I am not looking at the right set of instructions.  Is this what you referred to in your earlier post (everything is picked from menus)?

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

And, should I wait until I boot into the new kernel to build Truecrypt for the new kernel?  Or do I need to insert steps in the above sequence?

Thanks again for your help.

---

### Post by ddrichardson on 2007-11-13
Yeah that seems a fairly good howto. If truecrypt is a kernel module, you can build it and insert either before or after.

---

### Post by a__l__a__n on 2007-11-14
I've spent the past day and a half compiling, and re-compiling, 2.6.23.1.  (at 6 hours per shot, on my 500Mhz laptop).  The deb package that results apparently has some problems.  First, there is no /lib/modules/2.6.23.1 folder created.  I eventually created that via "make modules_install" (found by browsing the Makefile).  Then, I was missing the /lib/firmware/2.6.23.1 folder.  I created a symlink to the existing 2.6.22-14 folder (I have no idea if that is legitimate).  Then, I found that the GrubEd tool does not include a link to the initrd.img file in the default boot option, which results in a kernel panic during boot.  

There were several other problems along the way which I forget right now.

At this point, the new kernel still fails to boot.  When I turn off the "quiet" and "splash" boot options, I see that it fails when trying to connect to the root filesystem.  

I really appreciate the help here, but at this point I've already invested a couple of days more than I intended. I didn't embark on the Ubuntu path to learn how to compile kernels and how to debug the boot process.  I'll just wait until Ubuntu releases 2.6.23.1 or later.

Thanks again

---

### Post by Tomosaur on 2007-11-15
> **a__l__a__n said:**
> I've spent the past day and a half compiling, and re-compiling, 2.6.23.1.  (at 6 hours per shot, on my 500Mhz laptop).  The deb package that results apparently has some problems.  First, there is no /lib/modules/2.6.23.1 folder created.  I eventually created that via "make modules_install" (found by browsing the Makefile).  Then, I was missing the /lib/firmware/2.6.23.1 folder.  I created a symlink to the existing 2.6.22-14 folder (I have no idea if that is legitimate).  Then, I found that the GrubEd tool does not include a link to the initrd.img file in the default boot option, which results in a kernel panic during boot.  

There were several other problems along the way which I forget right now.

At this point, the new kernel still fails to boot.  When I turn off the "quiet" and "splash" boot options, I see that it fails when trying to connect to the root filesystem.  

I really appreciate the help here, but at this point I've already invested a couple of days more than I intended. I didn't embark on the Ubuntu path to learn how to compile kernels and how to debug the boot process.  I'll just wait until Ubuntu releases 2.6.23.1 or later.

Thanks again

Just a quick reminder for everyone reading this - GrubEd is a not 'fix grub' tool - all it is, and all it is intended to be, is a nicer way of modifying an already working grub without forcing you to use the command-line.

---

