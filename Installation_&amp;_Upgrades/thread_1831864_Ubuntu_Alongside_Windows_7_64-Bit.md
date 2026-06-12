---
title: "Ubuntu Alongside Windows 7 64-Bit?"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by AdelaisAer on 2011-08-23
Hi.

I was wondering if I should install Ubuntu alongside my Windows 7 64-bit. I have a few options, I guess.

I could install it on my D: drive (apparently a Local Disc partition of my physical C: drive), install it in a partition on my C: drive, or just try and buy an external hard drive and install it on there.

My C: (main partition) has 225GB free space; my D: (Local Disc) has 7.87GB free space (out of 8.23GB).

What is best for me?

I also heard that installing it with Wubi can sometimes cause problems for Windows users and the best way to install Ubuntu is in an actual partition than with Wubi.

My specs:

**Laptop**
Windows 7 64-Bit Professional
256VRAM
4GB RAM
ATI Radeon Mobility HD 3470
Realtek HD Audio
-----------------------------------------------------------------------

I have previously installed Ubuntu on my older PC (which is crap, btw), and it worked fine on it, but I really liked it, so I got the idea to try and install it on my laptop, too.

---

### Post by lmarmisa on 2011-08-24
I think that Ubuntu with Wubi is a good option.

[http://www.youtube.com/watch?v=iW1V6TuZZmc](http://www.youtube.com/watch?v=iW1V6TuZZmc)

But considering that you have a very powerful machine, I recommend a virtualization solution with [VirtualBox]("http://www.virtualbox.org/").

[http://www.youtube.com/watch?v=utvM7Zu7zFg](http://www.youtube.com/watch?v=utvM7Zu7zFg)

---

### Post by AdelaisAer on 2011-08-24
> **lmarmisa said:**
> I think that Ubuntu with Wubi is a good option.

[http://www.youtube.com/watch?v=iW1V6TuZZmc](http://www.youtube.com/watch?v=iW1V6TuZZmc)

But considering that you have a very powerful machine, I recommend a virtualization solution with [VirtualBox]("http://www.virtualbox.org/").

[http://www.youtube.com/watch?v=utvM7Zu7zFg](http://www.youtube.com/watch?v=utvM7Zu7zFg)

But if I install it, should I install it on my C: drive or on my D: Local Disk partition?

Also, I have never used Virtualization before, but I could give VirtualBox a try, maybe.

---

### Post by lmarmisa on 2011-08-24
> **AdelaisAer said:**
> But if I install it, should I install it on my C: drive or on my D: Local Disk partition?

Also, I have never used Virtualization before, but I could give VirtualBox a try, maybe.

If you install Ubuntu with Wubi, the partitions for Ubuntu (root and swap) are created as files of Windows. I recommend to allocate about 10 to 15 GB for Ubuntu during installation. You have no such free space on your partition D:. So, you should use the unit C:.

VirtualBox is interesting because you can create as many virtual machines as you want. Each virtual machine can run a different operating system: windows, ubuntu, xubuntu, lubuntu, kubuntu, fedora, macos, etc. Of course you can create different virtual machines for different versions of Ubuntu. Virtualization is a very powerful tool.

The virtual machines have virtual disks. A virtual disk is stored as a file of Windows. If you decide to install VirtualBox, I recommened to define your own folder located at C:\VirtualBox for storing the data and files of your virtual machines. Define inside folders for VirtualMachines, ISORepository, shared, etc.

---

### Post by AdelaisAer on 2011-08-24
> **lmarmisa said:**
> If you install Ubuntu with Wubi, the partitions for Ubuntu (root and swap) are created as files of Windows. I recommend to allocate about 10 to 15 GB for Ubuntu during installation. You have no such free space on your partition D:. So, you should use the unit C:.

VirtualBox is interesting because you can create as many virtual machines as you want. Each virtual machine can run a different operating system: windows, ubuntu, xubuntu, lubuntu, kubuntu, fedora, macos, etc. Of course you can create different virtual machines for different versions of Ubuntu. Virtualization is a very powerful tool.

The virtual machines have virtual disks. A virtual disk is stored as a file of Windows. If you decide to install VirtualBox, I recommened to define your own folder located at C:\VirtualBox for storing the data and files of your virtual machines. Define inside folders for VirtualMachines, ISORepository, shared, etc.

Thank you! I'll install it on my C:, then, and allocate 17GB (since that's what the Wubi installer recommended). And if I ever see that I do not like it, I can just easily uninstall it.

---

### Post by lmarmisa on 2011-08-24
> **AdelaisAer said:**
> Thank you! I'll install it on my C:, then, and allocate 17GB (since that's what the Wubi installer recommended). And if I ever see that I do not like it, I can just easily uninstall it.

I wish you a successful installation. :D

Best regards,

Luis

---

### Post by JGMS on 2011-08-24
Hi All,

I have used Virtualbox in W7 64 bit, and I have decided to install Ubuntu alongside W7 just the way it does when you run the Ubuntu disk: making the system dualboot, using grub2. This gives you the best performance of Ubuntu, though it has the disadvantage that you have no Windows running, if you need it for any reason. I find it enoying to wait for Windows before starting up your computer in Ubuntu. Apart from that, I experienced problems with Virtualbox to recognise perifery equipment such as a camera. To be able to read usb-sticks is not just straightforward, as for instance. To load a CD you need to disconnect the VBoxGuestOptions and to redirect it to the drive. In addition to this, sometimes you find programs not to work: like making a screendump from with the assessoires tools in the menu. These kind of things just irritate. I do like it though, so I won't delete Virtualbox, but will likely only use it for testing (new) versions of operating systems of any kind. By the way, if you install Ubuntu as dual boot, you just can access your Windows maps and load your data (provided its format allows so, which is most often the case).

However, in doing so with W7 I found that the installation program of Ubuntu did not come with the option "Install alongside Windows". Instead it always seems to overwrite the W7 installation. In order to make space for Ubuntu I reduced the size of the data partition of Windows using GParted in Ubuntu (runnning from the CD). I let Windows run a disk check after restarting to Windows. Windows just runs OK. Thereafter, installing Ubuntu as dual boot still failed: the required option just did not appear in the respective installation screen. I hoped to see the option to install it in the "largest available block of free space".

Hopefully, some expert can tell how to deal with this in order to get the dual boot option installed.  

Regards, JGMS

---

### Post by Frogs Hair on 2011-08-24
I know four people using Wubi and Win 7 with great results . It is ideal for them because Ubuntu is not their main operating system and they like to check out the latest release.

If Windows is well cared for Wubi installations can work very well as a means to try out Ubuntu . Download the ISO of your choice and install via Wubi from the disk . If decide to dual boot you already have the disk .

---

### Post by Mark Phelps on 2011-08-24
> **JGMS said:**
> ... However, in doing so with W7 I found that the installation program of Ubuntu did not come with the option "Install alongside Windows". Instead it always seems to overwrite the W7 installation. 
It doesn't actually do that by default -- but, the installation sequence is so vague and confusing that it's real easy to accidentally overwrite the Win7 install.

> In order to make space for Ubuntu I reduced the size of the data partition of Windows using GParted in Ubuntu (runnning from the CD). I let Windows run a disk check after restarting to Windows. Windows just runs OK.
You're lucky -- this sort of fix does not always work.

>  Thereafter, installing Ubuntu as dual boot still failed: the required option just did not appear in the respective installation screen. I hoped to see the option to install it in the "largest available block of free space".


Canonical removed this much-used option from the Ubuntu installer, forcing folks to deal with Manual Partitioning -- which all too often, leads to the accidental overwrite that I mentioned above.  You will have to go through the manual partitioning step and be careful to select the unused space for Ubuntu.

Also, in  future, please don't hijack someone else's thread -- make your own thread.

---

