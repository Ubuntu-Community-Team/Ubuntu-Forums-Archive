---
title: "Need help navigating UEFI setup for dual-boot install"
date: 2024-03-31
forum: Installation &amp; Upgrades
---

### Post by schwim-dandy on 2024-03-31
Hi there everyone,

I haven't installed linux dual boot since UEFI was introduced but need to now and I'm having a problem figuring out what to do here. 

The PC: Dell XPS 8930
Drives: Windows on NVME, Linux will go on newly installed SSD .  I'd like to have the PC choose the SSD first by default unless chosen otherwise to boot into Windows.

Could someone tell me what I need to change here to get the boot scenario I'd like?

 Here's the menu I'm presented with.
[IMG]https://i.imgur.com/P8mIh6g.jpeg[/IMG]

---

### Post by oldfred on 2024-03-31
Please attach screen shots, not post in line. Not everyone has high speed Internet.
You can easily attach with Forum's Go Advanced editor & paper clip icon.

Dells typically work well, but often need settings & updates.
Make sure UEFI firmware & SSD firmware are latest versions.

UEFI install to one drive using same ESP works well. Issue starts with two drives and version of installer/version of Ubuntu.
The standard (now older) Ubquity installer would show option to choose drive for boot files, but it did not work. It only installed into first drive's ESP.
Many users with two drives and those users with an external second drive needed to have ESP on second drive, so work arounds created.
Newer Subiquity installer used with servers since 22.04 and with Ubuntu (but not flavors) 23.10 supposedly works.
Lubuntu and Kubuntu starting with 24.04 use Calmares installer which works, I have used Calmares with Kubuntu 24.04 and it installed to my sda drive where NVMe drive is first drive and default when I used.

So what version/flavor of Ubuntu?

Also proprietary drives often nVidia and a few WiFi drivers cause issues. If you have nVidia be sure to boot in Safe Mode & install optional restricted drivers to get correct nVidia driver installed as part of install. It can be installed after Ubuntu install, but then a bit of a hassle.

Some general info on UEFI install in link in my signature & links to even more info.

I have a newer 11th gen Intel Dell 3510 that uses Intel video. I forgot to make any of the changes I suggest to others & it just worked. But one drive, so install to first ESP was ok.

---

### Post by tea for one on 2024-03-31
Legacy Boot Disabled is perfect.
This will ensure that you boot the Ubuntu USB installer in UEFI mode.

However, under Boot Option Priorities, I would expect to see:-
Your destination disk SSD
Ubuntu installer USB device

You only have Windows Boot Manager available.

---

### Post by grahammechanical on 2024-03-31
May I say something? Have you installed Ubuntu on the SSD? If you have not the UEFI will not recognise the SSD as having an OS on it.

I am test installing 24.04 on to an external SATA drive in an enclosure. Once Ubuntu is installed the UEFI will see the SATA drive as SDA and boot from it if I select it.

If I switch off the power to the external drive exclosure then the UEFI does not show the SATA drive.

It might be helpful if you loaded Try Ubuntu session and used GParted to give that SSD drive a partition table (GPT) and a format of EXT4. If you want you can also create partitions. Otherwise, you are left with the "Erase disc and install Ubuntu" option.

Regards

---

### Post by oldfred on 2024-03-31
If partitioning from scratch, I recommend using gpt, I think gparted still defaults to old MBR(msdos).
Than add an ESP and at minimum a partition for /(root). Normal default for / is ext4.
If very large drive, very large / is not normally recommended. You can have separate partition for /home (normally in /) or add data partition(s) later.

During install - Something Else, then you select ESP as ESP with esp,boot flags, & ext4 as /. If using separate /home select that also.
Do not mix up which partition is which. I once had a larger drive with multiple partitions and put / in larger one meant for /home. 

If using Ubuntu, it defaults to using snaps for many applications. Those are larger & it will keep several copies, so grows.
I use Kubuntu with no snaps and all data in separate data partition and currently use 14GB of  30GB I allocated for /. But have seen users with 20GB just for snapes, so allow extra room, depending.

---

