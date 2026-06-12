---
title: "Boot Repair - 'Close all package managers…' Dual Boot Installation - Dell XPS 14"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by soupdragon11 on 2013-12-19
After almost a week I've just about manged to install Ubuntu 12.04.3 LTS alongside Windows 8 on a Dell XPS 14 Ultrabook.

I have created a partition in Windows to store Ubuntu, rebooted from Windows Advanced Start Up options menu to an EFI USB containing Ubuntu. I've installed Ubuntu on my chosen partition with 4GB swap area also set aside.

During the install i get this error message:
[B]The 'grub-efi-amd64-signed' package failed to install into /target/. Without GRUB boot loader, the installed system will no boot.
[/B]
After some searching, i read that I should use Boot-Repair, which I've done.

However, after running Boot-Repair and choosing the auto diagnose and repair option, I get a message to

[B]'Please close all your package managers (Software Center, Update Manager, Synaptic, ...) Then try again.'
[/B]
Can someone please help me with what i need to do next as it's driving me mad!

Ubuntu has installed (if i try to reinstall on the same partition, my previous install is there) - it just seems i need to fix this problem.

Please help - Windows 8 is awful but I'm getting very tired of the endless pushing a big rock up a steep hill that installing Ubuntu is.

---

### Post by oldfred on 2013-12-19
You cannot create partitions with Windows for Linux, so I am not sure how you installed.

Have you turned off secure boot and fast boot or always on hibernation?

You cannot have multiple updates running. I have open synaptic and terminal at same time and get similar errors. But not sure why from Boot-Repair you would get that error as it should only be running its updates. Perhaps something with first error left something still open like a lock file to say it is running, so it thinks it is still running?

Can you post the link to a BootInfo report?
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)


 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by soupdragon11 on 2013-12-19
> **oldfred said:**
> You cannot create partitions with Windows for Linux, so I am not sure how you installed.

The first answer on [this post]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported") advised me to create the partition in Windows first - and it seems to have worked.

Secure Boot is turned off in BIOS. I don't have any updates running as far as I know - I'm just trying to install!

If i could turn off/close Package Managers I'd be there i think.

---

### Post by oldfred on 2013-12-19
I think those instructions just say to shrink Windows with Windows disk tools and leave unallocated space. Then the Ubuntu installer creates its partitions. I generally prefer to create partitions in advance with gparted, but most new users will just use the auto install.

Can you post bootinfo report link?

---

