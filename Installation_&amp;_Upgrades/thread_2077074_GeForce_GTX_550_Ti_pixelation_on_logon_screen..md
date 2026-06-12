---
title: "GeForce GTX 550 Ti pixelation on logon screen."
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by stchman on 2012-10-27
Hello all.

I recently upgraded to a Z77 motherboard (Gigabyte GA-Z77X-D3H).  It is a great Ubuntu 12.04 motherboard as everything works OOB.

I have a GeForce GTX 550 Ti PCI-E video card and using the Nvidia 295.40 drivers.  When the computer boots to the login screen I get some pixelation and I have to hit enter.  The screen goes black and then I can enter my password.  I dual boot Windows 7 as well and there is no video problems whatsoever.  I am using a Core i7 3770 and the HD 4000 video does not do this if I remove the Nvidia card.

Once I on in Unity, the computer runs fine without issue.

Here is an lcpci listing of the hardware:

```

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.6 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
03:00.0 USB controller: VIA Technologies, Inc. Device 3432 (rev 03)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 30)
05:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
06:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
07:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)

```

Anyone have any ideas.  It is really a nuisance more than anything.

Thanks.

---

### Post by oldfred on 2012-10-27
I think the latest version of grub tries to use the video from the system. You can change this but then you get large type.

Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub

I have nvidia-current-updates and am at version 304.43 and synaptic shows experimental now at 310, you may want to try a newer verison of the nvidia driver?

---

### Post by stchman on 2012-10-27
> **oldfred said:**
> I think the latest version of grub tries to use the video from the system. You can change this but then you get large type.

Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub

I have nvidia-current-updates and am at version 304.43 and synaptic shows experimental now at 310, you may want to try a newer verison of the nvidia driver?

I did the following:

```
sudo apt-get install nvidia-current-updates
```

After that I went into the Additional Drivers under System Settings and activated the:

Nvidia accelerated graphics driver (post-release updates)(version current-updates)

The dialog asked me to reboot, after that when you go to nvidia-settings it reads that I have the 304.43 driver installed.

After a few reboots for test, the pixelation is not showing up any more.  I gathered I needed a more updated driver than the 295.40.

Thanks.

---

