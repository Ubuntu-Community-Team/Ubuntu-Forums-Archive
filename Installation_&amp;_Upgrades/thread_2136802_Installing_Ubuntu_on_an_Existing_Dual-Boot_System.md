---
title: "Installing Ubuntu on an Existing Dual-Boot System"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Prthm on 2013-04-18
Hello,

I have a dual boot system with Windows 7 and Debian Stable. I want to install Ubuntu 12.10 and get rid of Debian completely. I do not need any of the data that the Debian partition has but I need the Windows partition.

I plan to do this by following these steps:
1. Make a bootable USB and boot the system with it
2. When the installer asks for a partition for installing Ubuntu, I manually select the partition where I have Debian installed.

I'm guessing that the Ubuntu installer will now format that partition, install Ubuntu over it and I will have a working dual boot system with Windows 7 and Ubuntu. Is it as simple as this or am I missing something? I do not have a Windows recovery CD at hand in case anything goes wrong but I want to get this done as soon as possible.

Thank you for reading this.

---

### Post by sudodus on 2013-04-18
With a reasonable amount of luck, yes. But you should backup your Windows partition(s), because you need it. You can use Clonezilla to make an image of the whole drive or of the windows partition(s).

You should also test Ubuntu live, and maybe also Xubuntu, Lubuntu and Kubuntu to find which flavour of Ubuntu that will be the best for you in that computer. 'Try Ubuntu' without installing it. This can save a lot of work. If you specify the computer, or at least the CPU, RAM, and graphics card, it will be easier to help.

When you are ready to install, you can re-use the Debian partition and the swap partition. When you run the installer and arrive at the partitioning screen, select 'Something else', and mark that partition to be used with the ext4 file system, to mount it as the root partition '/', and mark it to be formatted. Finally install grub to the head of the drive (if only one internal drive, to **[FONT=courier new]/dev/sda[/FONT]**).

---

### Post by Prthm on 2013-04-18
Thank you for the reply.

> [COLOR=#000000]If you specify the computer, or at least the CPU, RAM, and graphics card, it will be easier to help.[/COLOR]
It's a low end netbook but I am going to use Ubuntu just for minor development work.

> [COLOR=#000000]When you are ready to install, you can re-use the Debian partition and the swap partition. When you run the installer and arrive at the partitioning screen, select 'Something else', and mark that partition to be used with the ext4 file system, to mount it as the root partition '/', and mark it to be formatted. Finally install grub to the head of the drive (if only one internal drive, to [/COLOR]**[FONT=courier new]/dev/sda[/FONT]).**
So, I have taken backup and created a Bootable USB with Ubuntu 12.10. I have only one internal drive. Should I boot from USB and install Ubuntu on the Debian partition (will mark the Debian partition after selecting the 'Something Else' option). Also, should I choose the already created swap partition for the Ubuntu swap partition?

---

### Post by sudodus on 2013-04-19
> **Prthm said:**
> It's a low end netbook but I am going to use Ubuntu just for minor development work.

Then I recommend that you try Lubuntu 12.10 or Xubuntu 12.04 LTS. It should work with Ubuntu too, but it will be slow and unresponsive compared to Lubuntu with the ultra light LXDE desktop environment and Xubuntu with the light desktop environment XFCE. So I suggest that you test 'try' these flavours live (without installing) before you decide what to use. It is your choice how to balance between speed and eye-candy.
> 

So, I have taken backup and created a Bootable USB with Ubuntu 12.10. I have only one internal drive. Should I boot from USB and install Ubuntu on the Debian partition (will mark the Debian partition after selecting the 'Something Else' option). Also, should I choose the already created swap partition for the Ubuntu swap partition?

Yes, install Ubuntu on the Debian partition! No, you need not specify the swap partition, it should be found automatically. And probably grub will be installed to the right place by default, but check that (at the bottom of the partitioning page).

---

### Post by darkod on 2013-04-19
Just note in the manual installation, in the partitioning step, you need to click the root partition and the button Change below. Then in the window it opens select Use As ext4, mount point / and tick the format box. Otherwise it will not format it.

That's all you should need to do. Make sure you install the bootloader to the MBR, /dev/sda, without any number in it. Numbers are partitions.

---

### Post by Prthm on 2013-04-23
[COLOR=#000000]sudodus and [/COLOR][COLOR=#000000]darkod, thank you for the help. I followed your instructions and Ubuntu is working great now.


[/COLOR]

---

### Post by sudodus on 2013-04-23
You are welcome :-)

---

