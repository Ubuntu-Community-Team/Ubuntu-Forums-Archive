---
title: "Ubuntu 11.04 doesn't boot for me. Would like to know how to run 10.10"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by Pickles89 on 2011-05-10
I just want to know how to run an older version of Ubuntu. I had 10.10 running perfectly for me before, and I loved it. After installing 11.04 I get a screen which says 

* Starting --- [OK]

where --- are different things.

* stopping automatic crash report generation [fail]

always, but I don't really care. The issue is it will go down a list of "starting" lines and jst stop on one randoly, and not proceed to boot Ubuntu 11.04.

Which troubleshooting I managed to run 10.10 by loading th boot list, but I don't know what i did to access the boot list, and I can't find my way back into that menu.

So how do I run an older version of Ubuntu, and how do I set that version as the version which automatically loads upon start up?

---

### Post by jerrrys on 2011-05-11
you can upgrade to a newer version, but you can't degrade back to an older version.  you have to reinstall the older version

---

### Post by Rubi1200 on 2011-05-11
Hi,

please post the specifications for the computer, especially RAM and graphics card.

Also, run this diagnostic script and post the results:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ulysses768 on 2011-05-11
I'm having a very similar issue.  Natty had been running fine until last night.  Recovery mode also failed, freezing at the initial menu.  I was only able to login (no X) by adding rw init=/bin/bash to the grub entry.  I initially assumed that the cause was my re-configuring of xorg packages in an attempt to get HDMI output to work. 

The strange thing is that installation fails from both CD and usb.  There are no obvious errors, it simply hangs at random places while loading the image. There are no failures reported.

It could be a hardware issue with my graphics card, crunchbang runs just fine but dmesg spits this out:

[    3.785451] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM 

I have no idea if that was true before last night.  Unfortunately the bios has no options to disable the discrete GPU or the HDMI or VGA output.  Windows runs with no issues on both the discrete and integrated GPUs.

$lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

---

### Post by ulysses768 on 2011-05-11
Please ignore my previous post.  I wasn't aware of bug 775899.

---

### Post by Nara93 on 2011-05-11
Hey, guys. 

Hardly an expert on Ubuntu, but I found the answer to this one this morning, and thought I'd do the forums a favour for one. 

Had exactly the same issue as you! OK, here's how I fixed mine:

1. At the startup, hit "Shift" a lot. This will get you to the boot menu.
2. Select "Previous Linux Kernels" and go into the 3rd one down (or 10.10, if it's different for you).
3. While in 10.10, hook up your internet and go into Synaptic. Mark the following for reinstallation (or installation, if you're missing them): 

linux-image-2.6.38-8-generic-pae 
linux-generic-pae 
linux-headers-generic-pae 
linux-image-generic-pae 
linux-headers-2.6.38-8-generic-pae4. Once everything's finished, go to the power button and hit "Reboot to complete installation". 

If all goes to plan, this should fix everything for you. If not, it was worth a shot - this is just what worked for me. 

Good luck!

---

### Post by Pickles89 on 2011-05-12
> **Rubi1200 said:**
> Hi,

please post the specifications for the computer, especially RAM and graphics card.

Also, run this diagnostic script and post the results:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I'm fairly new to Ubuntu, and not good at programming. Only now while I troubleshoot this problem I find out I can run Ubuntu off a disk.
When you say boot the Ubuntu Live CD/USB, do you mean download Ubuntu 10.4 and set it up to run in the boot menu off a USB?

I'll try that when I get home, look for another reply in 2 hours.

I have a Dell Studio XPS with 4.0 GB DDR3 Ram, don't know the specs off hand.

---

### Post by Rubi1200 on 2011-05-12
First you need to download the image from the Ubuntu site:
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

Then burn it to either CD or USB:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Set BIOS to boot from the relevant drive by changing the boot device priority and then follow the instructions from the previous post.

---

