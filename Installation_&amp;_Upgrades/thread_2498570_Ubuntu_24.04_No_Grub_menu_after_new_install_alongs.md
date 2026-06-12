---
title: "Ubuntu 24.04 No Grub menu after new install alongside Window 10"
date: 2024-06-19
forum: Installation &amp; Upgrades
---

### Post by garthkh on 2024-06-19
Hi I'm relatively new to Ubuntu having tried live installs a few times in the past but never needing to sort problems out. I have run OpenSuse as a dual boot alongside Windows for many years but have decided to change across to Ubuntu as new OpenSuse installs are not easy to follow.
I have a Dell Optiplex 7050 micro desktop computer with a 1TB M.2 Nvme drive installed
I decided to clear both the old Windows and OpenSuse partitions. Reformat the drive and Installed my Windows 10 pro software. 
I shrunk the Windows drive partition by 600000 Mb allowing this unallocated space for Ubuntu.
I disabled the fast startup for Windows.
Secure boot is disabled in the BIOS
I ran the Ubuntu install from USB and when it displayed the option of Installing alongside Windows I was very happy that it was doing this automatically.
The install went through perfectly BUT the boot only loads Ubuntu. I have no Grub menu to choose Windows.
Windows is still there as I can access the files from Ubuntu.
Booting with F12 doesn't give any options either. 
Is there a way of repairing the Grub boot loader from within Ubuntu, or, must I reinstall in a different way?
In OpenSuse I had the YAST setup control panel where quite a lot of settings could be done.  Is there a similar tool in Ubuntu?
I see a lot of instructions given to use the terminal command code.  I do know a little of this but need handholding.

---

### Post by nicolasdentremont on 2024-06-21
/etc/default/grub has settings on how long the Grub menu is displayed.

GRUB_TIMEOUT sets the countdown in seconds, if it's set to 0 I believe the menu won't show at all and will just boot the default OS.

Can you still boot Windows if you change the boot order in your BIOS?

---

### Post by oldfred on 2024-06-21
Are all installs UEFI?
Grub can only boot other installs in same boot mode. Systems since 2012 are UEFI, but many can be booted in BIOS creating confusion if multiple systems not installed in same boot mode.

What brand/model system? What video card/chip?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by garthkh on 2024-06-21
> **nicolasdentremont said:**
> /etc/default/grub has settings on how long the Grub menu is displayed.

GRUB_TIMEOUT sets the countdown in seconds, if it's set to 0 I believe the menu won't show at all and will just boot the default OS.

Can you still boot Windows if you change the boot order in your BIOS?

Yes, It's zero - thank you

---

