---
title: "MSI GT72 2QD Dominator G"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by dangerjunkie2002 on 2015-08-31
Hi,

After a very sub-standard support experience with Dell, I decided not to have another Alienware laptop and bought this [MSI GT72 2QD Dominator G]("http://www.msi.com/product/nb/GT72-2QD-Dominator.html#hero-specification") This machine is the variant with the i7-5700HQ CPU.

I must admit I'd been really spoiled by Ubuntu and didn't go into too much depth checking the hardware out as every machine I'd put it on in the last 5 years has "Just Worked(tm)." I did note that the machine has a new Broadwell i7 (instead of the Haswell from the old machine) but my quick delve into the internet informed me that Intel run a "tick-tock" hardware revision cycle and Broadwell is a "tock" and is therefore more of an evolution than a revolution so I wasn't expecting any real issues. The USB controller is a bit different (It's 10Gbps USB 3.1 rather than 3.0 and has no USB 2.0 ports at all.) I didn't think the nVidia GTX970m would be any great problem and the spec didn't mention Optimus video so I thought I was going to be in for a reasonably easy time. The machine appears to be pretty well constructed and Windows goes "like poop off a scoop" with my benchmark graphics-intensive application, Second Life, going from 34 FPS on the Alienware to 77FPS on the MSI.
 
After receiving the machine, I did find out that, whilst it seems to be correct that it doesn't have Optimus graphics, it does have an Intel GPU as well as the nVidia one. Switching between the Intel and nVidia GPUs is accomplished by pressing a hot key next to the keyboard which invokes some custom Windows applet that changes the GPU selection then prompts for a reboot. Which GPU is selected seems to be persistent across reboots but it's not possible to change the GPU over in the BIOS and, so far, it's not known how the Windows applet causes the change so, if you want to be able to switch between them, you have to keep Windows around.

The declared specification of the machine is that it comes with a 256GB SSD. This turned out to be incorrect and it really comes with a pair of 128GB M.2 SSD drives that are joined RAID0 to form a 256GB volume using the on-board Intel Rapid Storage Technology (RST) RAID controller. I found RST made the Ubuntu installer's life very hard and, as I wanted more storage for both OSes dual-boot, I replaced the 128GB drives with a pair of Samsung 850 EVO 500GB SSDs, changed the BIOS drive mode from RAID to AHCI and reinstalled Windows. There are now two discrete SSD drives, one for Windows, one for Linux.

Now down to the getting Ubuntu installed - This is where the pain really began.

[LIST]
[*]With the nVidia GPU selected, *nomodeset* is required otherwise there is no graphical output. This step is not required for the Intel GPU. I'm assuming this will go away when the binary nVidia driver is installed.
[*]Every boot displays the warnings "Ignoring BGRT: Invalid status 0 (expected 1)" and "ACPI PCC probe failed."
[*]I've tried the 15.04 desktop, 15.04 server and Saturday's 15.10 daily build discs - All are crashy and fail to make it through an install. The point of the crash is inconsistent, even with the same disc. Most of the crashes are kernel panics (flashing CAPS lock of death)
[*]Most of the time the machine locks up solid and no error is displayed.
[*]The two times I saw the kernel panic error, there were "Timeout synchronizing machine check over CPUs" and another one which I didn't catch which contained multiple lines referring to a timeout and microcode on CPU0.
[*]The one time I got the Ubuntu live CD to boot to the desktop, the "Additional drivers" application didn't identify the nVidia GPU as being a candidate for a proprietary driver but it did offer a "microcode" package, however it didn't say what the microcode was for but I assume it was the CPU.
[*]Wallpapering the boot options with the old "*nomodeset noacpi noapic nolapic*" didn't help.
[/LIST]

Here's the lspci with the Intel GPU active:
```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge - DMI (rev 0a)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 0a)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 0a)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
03:00.0 Network controller: Qualcomm Atheros Device 003e (rev 20)
04:00.0 USB controller: ASMedia Technology Inc. Device 1242
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader (rev 01)
```

I consider myself fairly competent with Linux; I've been an Ubuntu user since 2005 but this is beyond anything I've dealt with before. I would be really grateful for some help in getting this going. I'd also like to know what information I should capture and how to report it in order to get this fixed for everyone.

Many thanks,
Paul.

---

### Post by efflandt on 2015-09-01
Although, nomodeset is typically needed for live/install iso boot on a desktop, I read one post that someone had trouble installing on their hybrid Intel/Nvidia graphics laptop until they did NOT use nomodeset. So I did not use that for my older MSI GE60-2OE laptop and everything worked fine. But I bought my laptop while Win7 was still available, so it is using BIOS and msdos partitions, and I have not had to deal with UEFI and secure boot yet. Mine just came with 1 TB hard drive, so I installed 64-bit Ubuntu 14.04 to a Crucial 512 GB mSATA SSD and boot everything from grub there.

I seem to remember that Additional Drivers did not show anything for my laptop when booted using default Intel graphics. So I installed synaptic and used that to install nvidia-331-updates in my case which was the newest in 14.04. But my GTX 765M is older and I do not know which driver versions are available in 15.04. If you need a newer driver for your GTX 970M than is in normal repositories, xorg-edgers ppa has had **nvidia-352** for a while (using that on my desktop with Maxwell chip in its GTX 750 Ti) and now also has **nvidia-355**. Once you have a working nvidia driver you should be able to select whether to use Intel or Nvidia from **NVIDIA X Server Settings** (which for me requires relogging into X switching Nvidia to Intel or reboot after switching from Intel to Nvidia). Which ever you set it to sticks through a reboot.

It is strange that your Nvidia graphics does not show up in lspci. Mine shows up as a 3D device vs. VGA for Intel while using the Intel graphics```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev ff)
03:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
```

---

### Post by dangerjunkie2002 on 2015-09-01
Hi,

Thank you. That's filled in a couple of holes.

My biggest problem at the moment I think is the new Broadwell CPU. The machine won't stay running for long enough to get through the install without either locking up or kernel panicking. 

Thanks,
Paul.

---

### Post by noxo on 2016-01-04
Try turning of Intel SpeedStepping in BIOS. That worked for my Broadwell based GS 60, which was constantly freezing with 15.10.

---

### Post by RockFordGT on 2016-03-31
A little bit later but maybe someone will look for help:
My finding that may be useful: 

To start system and have it working (with all cores enabled) and pretty stable add these option to the kernel params:
```
 nomodeset nohz=off clocksource=tsc
```
I've tested this kernel params also on arch, and on few ubuntu kernels from 15.04 (even 4.4.0-040400-generic)

Nvidia works fine with binary packages.
Ethernet works very good.
Bluetooth works.
Camera works
Keyboard backlit ([https://github.com/markrileybot/python-msikeys](https://github.com/markrileybot/python-msikeys)) 


What does not work:
WiFi: I'm getting constant "Firmware crashed" - I've disabled build in WiFi by blacklisting driver
Switching Vido card

---

