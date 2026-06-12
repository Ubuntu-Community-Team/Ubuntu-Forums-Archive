---
title: "Problems with 13.04 (xubuntu and ubuntu)"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by Krupski on 2013-07-05
Hi all,

I've been using Linux (Ubuntu) since 2008 and know my way around it rather well.

Now, for my problem. I tried to install XUBUNTU 13.04 (64 bit) on the same machine that has run almost all previous versions. I had a wide range of problems (and different ones each time). Either the install would not complete, or it would complete but not finish booting, or it would seem to work, but lock up shortly after starting.

Here's the hardware I'm having trouble with:

Intel DQ45GB motherboard
Intel Q9650 Quad core 3.00 GHz. LGA775 cpu
NVidia GTX560Ti video card
8 GB memory (4X2 gb) DDR2 - PC6400 - 800 MHz - 6-6-6-18 timing, 1.8v (running at 2.1v)
SATA hard drives and SATA DVD/BD read/writer

Now, before anyone suggests checking ram or anything else, be aware that the machine runs PERFECTLY FINE with 12.10 64 bit (as well as every version previous to that).

I tried XUBUNTU 64 bit and UBUNTU 64 bit (version 13.04) and both had the same problems.

I also tried installing from a DVD burned from an ISO and from a USB stick.

I tried re-downloading the ISO files. The MD5 sums were correct.

I even took the XUBUNTU disk that I burned and made an ISO back out of it. The MD5 was the same (i.e. the disk is not flawed).

Anyone have any ideas on what to do or what to try? I would like to keep current with Ubuntu (XUbuntu), but for now I'm "stuck" with 12.10 because 13.04 doesn't work on my machine.

Any help will be appreciated!

-- Roger

---

### Post by Bashing-om on 2013-07-05
Krupski; Hi ...

Here is a thought... 13.04 does not have the graphics drivers for that Nvidia card readily available...
what results when attempting to boot from the boot menu with "nomodeset" as a paramater ?
(installing 13.04 -Lubuntu -> Nvidia graphics, I had to use the "nomodeset" option to get it to install)

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by Krupski on 2013-07-05
> **Bashing-om said:**
> Krupski; Hi ...

Here is a thought... 13.04 does not have the graphics drivers for that Nvidia card readily available...
what results when attempting to boot from the boot menu with "nomodeset" as a paramater ?
(installing 13.04 -Lubuntu -> Nvidia graphics, I had to use the "nomodeset" option to get it to install)

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

Well this is strange. I thought I had replied to you concerning this post, but it doesn't seem to be here. I must have done something stupid like logged off before sending the reply.

Anyway, thank you for the suggestion. I tried it and it didn't work, but today I had lots of time and I was determined to find the problem.

I think I've found the problem (at least what I did resulted in a stable install!).

The darn "nouveau" video seemed to be the problem... and more specifically the errors pointed to HD audio (the onboard audio of the MOBO, not the HDMI audio capability of my NVidia card).

How I finally got the install to work well was as follows:

* Boot a 13.04 ISO image on a USB stick, choose "Try Xubuntu" rather than "Install Xubuntu"
* Install to a blank hard drive (490gb data, 10gb swap)
* **_Before rebooting_**, blacklist the "nouveau" driver in /etc/modprobe.d/disable-nouveau.conf (got the idea from NVIDIA):
```

# disable nouveau
blacklist nouveau
## 07/05/13 is this the same as "nomodeset"?
options nouveau modeset=0

```

* Reboot. The system reboots into a super low res (maybe 640 x 480) graphics mode. Barely usable
* CTRL-ALT-F1 to log into a CLI
* Turn off the "lightdm" service: service lightdm stop
* Run the NVIDIA driver package, answer all the prompts.
* This one is critical: **_SYNC_**!!! I tried just typing "reboot" figuring it would sync first. WRONG! I corrupted my first attempt and had to re-install it again. Now I type SYNC several times just to be sure!  :)
* Reboot again

Tada!!! The machine boots up in a few seconds (rather than struggling for 3 to 5 minutes, only to partially boot up, then lock up).

So, it seems that something changed from 12.10 -> 13.04 concerning the NVidia card and/or the HD audio and/or the "nouveau" driver.

One downside is that any update that rebuilds a new ramdisk image (like a new kernel release) requires me to re-install the NVidia driver (which isn't really much trouble at all).

Attached is a camera snapshot of the typical error I was getting. Maybe this will ring bells with someone?

-- Roger

---

### Post by Krupski on 2013-07-06
OK, did more investigating. The problem seems to be a conflict with nouveau and the Intel HD audio hardware on the motherboard.

Blacklisting nouveau (as described in the previous post) stops the hardware conflicts. Whether or not the NVIDIA driver is loaded or not makes no difference (errors-wise).

Also, disabling the motherboard sound hardware in the BIOS allows nouveau to be used (i.e. not blacklisted) without errors.

Now I wonder if it's just one bit of hardware or a whole line of Intel audio devices.

For what it's worth, here's my "lspci" listing:

[FONT=Courier New]rogerk@michael:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
[COLOR="#FF0000"]00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
[/FONT]

(the one shown in red is the culprit)

---

### Post by Bashing-om on 2013-07-06
Krupski; Morning !

That is to say the least, strange....I can not see a relationship between the graphics driver "nouveau" and the sound driver - I expect "alsa". I would rather accept a conflict in graphics cards. Do you have a hybrid graphics setup as in Intel AND Nvidia grahics components ? To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

And in respect to the Nvidia driver... Nvidia may now be instaledl with DKMS enabled :
> 
What's DKMS? It's dynamic kernel module support, and it looks like something <I've> wanted for a LONG time
Now, I noticed one nice new option in the 304.43 NVidia driver:

    Would you like to register the kernel module sources with DKMS?
    This will allow DKMS to automatically build a new module, if you install a different kernel later.
    [default: (N)o]:


It is great in that you are up and running, you have made a lot of progress and learned a lot in the process.

[INDENT][INDENT]it is all a learning experience
[/INDENT][/INDENT]

---

### Post by Krupski on 2013-07-06
> **Bashing-om said:**
> Krupski; Morning !

That is to say the least, strange....I can not see a relationship between the graphics driver "nouveau" and the sound driver - I expect "alsa". I would rather accept a conflict in graphics cards. Do you have a hybrid graphics setup as in Intel AND Nvidia grahics components ? To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

And in respect to the Nvidia driver... Nvidia may now be instaledl with DKMS enabled :


It is great in that you are up and running, you have made a lot of progress and learned a lot in the process.

[INDENT][INDENT]it is all a learning experience
[/INDENT][/INDENT]

I've found that by disabling the HD Audio on my motherboard (in BIOS), I can install "plain" without using any option switches or blacklist entries.

As you requested, here is the hardware info:

_**lshw -C display:**_
[FONT=monospace]
root@michael:/# lshw -C display
  *-display               
       description: VGA compatible controller
       product: GF114 [GeForce GTX 560 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:ec000000-edffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:ee000000-ee07ffff
[/FONT]

_**lspci -nnk | grep -iA3 vga:**_
[FONT=monospace]
root@michael:/# lspci -nnk | grep -iA3 vga
[COLOR="#FF0000"]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] [10de:1200] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2089]
	Kernel driver in use: nouveau[/COLOR]
01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2089]
	Kernel driver in use: snd_hda_intel
03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
	Subsystem: Western Digital USB 3.0 PCIe Card [1b96:0001]
[/FONT]

I'm guessing that the part in red is what you were after? I think the part about the USB 3.0 controller board is just an "overflow" from the -A3 option which in turn got caught by "eVga.com" matching "vga".

Currently, I have the Intel HD audio disabled, a fresh Xubuntu 13.04 64 bit installed and still using "nouveau" (have not installed the NVidia video driver yet).

The machine is running flawlessly.

I still need to figure out WHY I can't use the HD audio on the motherboard. I could always use the HDMI audio capability of the NVidia card (I have an HDMI cable to the monitor and the monitor has an audio output which comes from the SPDIF signal from the video card).

I still do, however, want to find and squash the bug that's keeping the HD audio from being used.... :)

Thanks again for all your help!

-- Roger

---

### Post by Bashing-om on 2013-07-06
Krupski; Sheesshhh;
I do not know, but I will commiserate with you !

All does indeed look good in the graphics department...And I am a bit stumped... this being the first time I have encountered that an audio situation prevents booting... First time for anything huh ??
On audio ..I have no knowledge or experience with it ... While waiting others input ... and mine when I get back here ... here is the basic troubleshooting guide on sound that might lead to something:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[INDENT][INDENT]when all else fails read the instructions ?[/INDENT][/INDENT]

---

