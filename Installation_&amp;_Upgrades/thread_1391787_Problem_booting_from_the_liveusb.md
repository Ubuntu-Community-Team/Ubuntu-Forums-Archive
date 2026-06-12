---
title: "Problem booting from the liveusb"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Xtyn on 2010-01-27
My liveusb's don't boot on my intel d510mo motherboard. It gives the message: boot error.

If I install a full OS on the USB stick, with GRUB on the MBR, it works fine, so I think the problem is with the MBR. The BIOS seems to require an active MBR to boot from the device. I've installed a MBR on the USB stick by "sudo install-mbr /dev/sdb" and now the boot error is "MBR:" I've also tried to activate the MBR through "sudo fdisk /dev/sdb" and "a" but nothing changed.

It's not a problem with the USB stick, I've tried two USB sticks, same problem and on other PC's they boot fine. I don't have an ODD on this PC. I've updated the BIOS but the problem persists.

[This guy]("http://communities.intel.com/message/79535;jsessionid=77416460D2E52B4D197F26E1AF9D9727.node5COMS") has the same problem.

---

### Post by drbubbles on 2010-02-13
I think you might need to update the d510mo bios. I had a problem  booting Ubuntu off a usb and I think that fixed it. You don't need a bootable USB to update the bios (even though the manual makes it look like you do). Just put the bios file on a USB stick and boot selecting bios update. (Might have been PXE boot that needed the bios update; can't remember which it was now, but it is worth a try if you haven't got it going yet).

---

### Post by drbubbles on 2010-02-13
Sorry, I should have read that you already updated the bios. In that case, you could try PXE booting from a NAS or similar if you have one. I am able to boot mine from USB and PXE.

---

### Post by m95lah on 2010-05-22
For anyone who has this problem and stumbles across this conversation:

I had the same problem with my d510mo, with usb sticks created with both unetbootin and imagewriter.
But a usb memory with ubuntu installed with "usb-creator" worked!

So go with usb-creator if you're experiencing "Boot Error" problems on this M/B.

---

### Post by Rmantingh on 2010-10-09
I have the same problem but nothing seems to work for me.
I have tried creating several bootable USB sticks using usb-creator-gtk (I'm using Ubuntu 10.04). No luck. None of them boot.
I've updating the BIOS on the D510MO board from 0175 to 0311 but that didn't help either.
I'm now trying to see if I can install Ubuntu using PXE network boot.
All the instructions however that I can find online are very confusing and mostly refer to older versions of Ubuntu.
I have a LAN with a router as DHCP server handing out IP addresses.
The intention is to set up my desktop PC (running Ubuntu 10.04) as a PXE server and have my D510MO machine boot/install from that.
Any help is much appreciated.

---

### Post by and.dmitry on 2010-11-13
> **Rmantingh said:**
> I have the same problem but nothing seems to work for me.
I have tried creating several bootable USB sticks using usb-creator-gtk (I'm using Ubuntu 10.04). No luck. None of them boot.
I've updating the BIOS on the D510MO board from 0175 to 0311 but that didn't help either.
I'm now trying to see if I can install Ubuntu using PXE network boot.
All the instructions however that I can find online are very confusing and mostly refer to older versions of Ubuntu.
I have a LAN with a router as DHCP server handing out IP addresses.
The intention is to set up my desktop PC (running Ubuntu 10.04) as a PXE server and have my D510MO machine boot/install from that.
Any help is much appreciated.

Set BIOS option "USB Mass Storage Emulation Type" to "All Fixed Disc". Tested on a few boards with BIOS version 0175.

---

