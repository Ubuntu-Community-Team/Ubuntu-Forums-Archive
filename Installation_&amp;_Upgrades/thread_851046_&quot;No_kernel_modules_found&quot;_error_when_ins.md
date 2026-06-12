---
title: "&quot;No kernel modules found&quot; error when installing from network"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by Shai Hulud on 2008-07-06
Hello, as my laptop (Asus EeePC) does not have CD and i don't have a external CD-ROM, i can't use the Alternative Installer ISO file.

I've tried to make a bootable USB stick from the alternative installer, but without any luck.

So in order to install the Command-line system, i went with the network install option.

I've extracted the Alternative ISO (ubuntu-8.04.1-alternate-i386.iso) in a folder in my apache root, and used [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz) this to make a bootable USB stick.

When the machine boots, i type "cli" for command-line installation and the install goes as normal. But when it gets to the Download installer components, this error pops up:

> [B]No kernel modules were found. This probably is due to a mismatch between the kernel used by this version of the installer and the kernel version available in the archive.

If you're installing from a mirror, you can work around this problem by choosing to install a different version of Ubuntu. The install will probably fail to work if you continue without kernel modules.[/B]

If i decide to continue without kernel modules, my SSD is not found, so i can't install.

It seems the problem is that the netboot image is older than the Alternative ISO i'm using. But where can i find a new one? Or how can i make one?

Thank you in advance for your responses.

---

