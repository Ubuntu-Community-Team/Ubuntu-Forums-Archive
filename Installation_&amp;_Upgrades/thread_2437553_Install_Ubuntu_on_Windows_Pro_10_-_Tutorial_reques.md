---
title: "Install Ubuntu on Windows Pro 10 - Tutorial request"
date: 2020-02-25
forum: Installation &amp; Upgrades
---

### Post by fabianaa on 2020-02-25
Hi all. I have windows 10 pro and I need to install Ubuntu on it (Not dual boot - Perhaps through some virtual machine??).  The final purpose is to install Docker on Ubuntu, as Docker keeps crashing on my Windows and I had to uninstall it.

I downloaded the Ubuntu shell from MS store, but I think this is not what I want. I would exteremely appreciate if someone could proivde me with a link or tutorial which states which version of the software I should install, how to, etc.

Many thanks

---

### Post by oldfred on 2020-02-25
I suggest you backup up your Windows.
We regularly get posts from users who go all in with just Ubuntu, but then find one game or application that only runs on Windows that they really must have.
You can start with dual booting buy shrinking the Windows NTFS partition using Windows tools and then install Ubuntu in unallocated space.

What brand/model system?
What video card/chip?
You may need boot parameters or UEFI settings depending on brands.

UEFI or BIOS install?
How you boot install media UEFI or BIOS is how it installs.
Microsoft has required vendors to install in UEFI boot mode since Windows 8 released in 2012. But upgrades from Windows 7 usually are BIOS based.

If UEFI see link in my signature, below.

---

### Post by Frogs Hair on 2020-02-25
There are many tutorials available on line. I have not used this tutorial, but am familiar with the source.
[https://itsfoss.com/install-linux-in-virtualbox/](https://itsfoss.com/install-linux-in-virtualbox/)

---

### Post by yancek on 2020-02-25
> (Not dual boot - Perhaps through some virtual machine?? 

If you do not want to dual boot or install Ubuntu as the only OS, the first step would be to download and install some virtual software such as VirtualBox, VMWare, etc. on your windows system.  There are countless tutorials available on the subject online and the same goes for installing Ubuntu in virtual software. The link below is to the VirtualBox site from which you can download it.  The 2nd link explains installing Ubuntu in VirtualBox.

 [https://www.virtualbox.org/wiki/Download_Old_Builds_6_0](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0)

[https://www.fofxacademy.com/install-ubuntu-linux-on-windows-10-using-virtualbox/](https://www.fofxacademy.com/install-ubuntu-linux-on-windows-10-using-virtualbox/)

---

