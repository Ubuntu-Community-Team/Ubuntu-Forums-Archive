---
title: "Trying to install 22.04 Xubuntu"
date: 2022-12-04
forum: Installation &amp; Upgrades
---

### Post by Autodave on 2022-12-04
inxi:
CPU: 12-core AMD Ryzen 9 7900X (-MT MCP-) speed/min/max: 3119/400/5733 MHz
Kernel: 5.15.0-56-generic x86_64 Up: 8m Mem: 1873.5/31208.1 MiB (6.0%)
Storage: 4.42 TiB (0.4% used) Procs: 392 Shell: Bash inxi: 3.3.13

Trying to install on this new machine.  Not much luck yet.  I have a NVME and a rotating 4 TB.  I am trying to install on the a 1 TB section of the spinner, but I end up with a lot of errors.  One that jumps out is err19......something about a hub with no ports.  Also, I pulled my old SSD with Ubuntu on it and connected it to the motherboard, but even the BIOS doesn't see it.  I would LOVE to get that working.  Any help will be greatly appreciated.  I can't wait to see how fast Linux will be on this machine.

---

### Post by Autodave on 2022-12-04
So, I made it worse.  I went onto the 4TB disk and deleted 2 parttions using Win11 and now when I boot the machine I come up to  grub>  .  What do I do now to get past that?  I would really love to delete grub and start over.

---

### Post by ActionParsnip on 2022-12-05
If you have Linux on the system then you can manually boot the system
[https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux)

---

### Post by DuckHook on 2022-12-05
It's easy to start over… you just:

[LIST=1]
[*]Run gparted on a LiveUSB,
[*]Delete all of your old partitions,
[*]Create new ones based on your desired partition layout,
[*]Install the system into your partitions of choice.
[/LIST]
You may wish to use LVM to give you some post&#8209;install flexibility, but that involves some initial complexity and may not be worth it.

Be sure that you create the partition layout with UEFI in mind, but given that you are an old Linux hand, I'm sure you already know about that.

If your BIOS doesn't see your SSD, check HW causes like cables and power. Make sure you are using the cables that come with your new PSU, NOT old ones salvaged from an old PSU. I burned out four disks, both HDDs and SSDs, by hooking them up to a new PSU using old cables. Modular PSUs have pinouts that are unique to each manufacturer and will burn out a disk that is connected with the wrong cable. That was a bad, sad mistake that caused me lost data and much gnashing of teeth.

If oldfred sees this thread, he could give you better advice on what settings are needed on new MOBOs and their BIOSes. I rarely work on new HW, so my knowledge there is limited.

---

### Post by Autodave on 2022-12-05
Never did get the SSD swap to work....have no idea why.  The BIOS would see it, Windows would see it, but could not get the PC to boot to it even though it worked in the previous machine as a bootable drive.  But, I got Linux instaled in a 1TB partition on the 4TB spinner.  Worked just fine AFTER removing the nVidia 525 OPEN driver (recommended) and replacing it with the 525 driver!  The OPEN driver would not allow 2 screens to function at the same time no matter how much I tried.  Saw on another forum about switching to the 525 driver and everything worked instantly.

---

