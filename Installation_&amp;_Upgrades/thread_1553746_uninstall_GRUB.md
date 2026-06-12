---
title: "uninstall GRUB?"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by wolf99 on 2010-08-15
Hi folks

I have a laptop that I want to ultimately install ubuntu on, it is an emachines e510 that originally had vista home basic on it, someone since has put dreamlinux and GRUB on it.

Can GRUB be uninstalled and dreamlinux still be booted?

How best to go about this? There are of course steps shown on other sites, but none that actually explains In a way i understand what this will do for the laptop so the first Q is really the main one..

Basically I want to clean away all the unnecessary cruft before I install the ubuntu over the dreamlinux.

thanks for any pointers

EDIT just to say i realise this isn't a dreamlinux site but I thought folks here might have experience with GRUB on a linux machine and I was here for the ubuntu anyway :)

---

### Post by Rubi1200 on 2010-08-15
> **wolf99 said:**
> Hi folks

I have a laptop that I want to ultimately install ubuntu on, it is an emachines e510 that originally had vista home basic on it, someone since has put dreamlinux and GRUB on it.

Can GRUB be uninstalled and dreamlinux still be booted?

How best to go about this? There are of course steps shown on other sites, but none that actually explains In a way i understand what this will do for the laptop so the first Q is really the main one..

Basically I want to clean away all the unnecessary cruft before I install the ubuntu over the dreamlinux.

thanks for any pointers

EDIT just to say i realise this isn't a dreamlinux site but I thought folks here might have experience with GRUB on a linux machine and I was here for the ubuntu anyway :)

> Can GRUB be uninstalled and dreamlinux still be booted?
As far as I am aware, the answer is no. If you take away the function required to boot a system it will no longer be able to boot.

> Basically I want to clean away all the unnecessary cruft before I install the ubuntu over the dreamlinux.
This is unnecessary; either install Ubuntu over what you currently have or prepare the drive beforehand using a tool like GParted (available on the Ubuntu CD).

Some links I hope will help you:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Good luck!

---

### Post by wolf99 on 2010-08-15
Do you mean the ubuntu install will overwrite the GRUB and take care of booting itself or do I *have* to use a boot loader with this machine?

What I'm getting at is that Ive seen machines that just boot -nix after the bios just the same as a windows machine. 

Is it in these cases that bootloading is done hidden? Can I revert to this if grub if I uninstall GRUB or do I need to put *some* type of bootloader on there if I get rid of GRUB???

thanks for answering.

The main prob I have is I know next to nothing about GRUB or bootloaders either for that matter :) 

Ta again

---

### Post by Herman on 2010-08-16
All operating systems need a boot loader to get them started, but if you have a computer with only one operating system in it the boot loader remains hidden and does its work silently.
There is no point showing a boot menu if there is no choice about which operating system to boot, so it's quicker to just skip it. For that reason many people are not even aware that there is such a thing as a boot loader.

When you set up a dual boot, the boot loader menu shows up and gives you a chance to select which operating system you want to boot into.
It is possible to install more than one Windows installation, and if you did that you would get a boot menu from the Windows boot loader.
If you installed just one Ubuntu installation in a computer, you wouldn't see the GRUB menu. Then when you add a second Ubuntu operating system, the GRUB Menu will show up.

When Dream Linux was installed, it installed a little code in the hard disk's MBR, which directs the boot to the GRUB files inside the Ubuntu partition, and from there you see the GRUB Menu and choose which operating system to boot, Ubuntu or Windows.
If you delete Dream Linux, you will be deleting your GRUB along with it, which means your MBR will be pointing to an empty sector in your hard disk, and you'll get an error message.
You could run a command from a Windows Live CD to make the MBR point to your Windows boot sector again, and then you would be able to boot Windows.
There would be little point in doing so though, because if you're planning on installing Ubuntu over the top of Dream Linux, it will automatically install Ubuntu's GRUB to MBR at the same time and automatically scan your computer for other operating systems and add them to the new boot menu. That would be the easiest way to do things.

---

