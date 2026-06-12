---
title: "Ubuntu distros on an old P3"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by r6mile on 2006-10-16
I have a Pentium III 450, and I have just upgraded it to 384 MB of SDRAM PC100. The graphic card is an integrated ATI Rage Pro 4 MB.
Which Ubuntu distro would work better on my sistem?

---

### Post by K.Mandla on 2006-10-16
Probably [Xubuntu]("https://wiki.ubuntu.com/Xubuntu/Releases"), unless you're willing to tinker with Openbox, Fluxbox, Blackbox or IceWM. If you're just getting started with Linux, try Xubuntu first. It should run well, but might be a little sluggish. Good luck!

---

### Post by r6mile on 2006-10-16
Ok thank you, I'll try Xubuntu (it's downloading at this moment).
Another question about the installation:
I actually have Windows 2000 installed in that computer, and my hard drive has only one NFTS partition. I want to have both Windows 2000 and Xubuntu installed at the same time. Is there any change that I could install Xubuntu without having to delete my actual installation of Windows 2000?

---

### Post by Lin-X on 2006-10-16
You partition your hard drive, install Xubuntu, which installs the Grub bootloader in your boot sector. When you boot your system, Grub will show you a menu that lets you choose which operating system you want to boot into.

By the way, I recommend that you partition your drive first, then install; don't partition from inside the installation, even though it tells you that you can. Quite a few of us had trouble with this. When the installer gets to the partition part, just choose one of the partitions as the one you want to install to. You might want to make a swap drive too --- that's a mini partition that is about twice the size of your RAM. This helps Linux run faster.

---

