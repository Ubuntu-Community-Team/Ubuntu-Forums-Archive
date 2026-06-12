---
title: "Feisty x64 Install Problems on Core2 with 4GB RAM"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by bebaumax on 2007-04-19
Not sure where to start, but here's the list off the top of my head.

Motherboard is a Gigabyte motherboard, it has a Marvell Ethernet chipset on it. I have an ATI x800 PCI-E graphics card and a Realtek GigE PCI card installed. The disk configuration is 2 x Maxtor 80GB SATA150 drives.

Unable to properly boot Desktop_AMD64 CD
Boots Alternative_Desktop_AMD64 fine

Detects both Marvell and Realtek chipsets, not always in the same order, though. ETH0/1 is swapped randomly on reboots.

Cannot configure/use the Marvell chipset, no matter what I do.

Finally switched to the Realtek chipset, DHCP was configured in <1 second. Interestingly, in viewing my DHCP server logs, it looks as though the Marvell chipset was registering and receiving an IP from my DHCP server, but the Feisty install refused to use it. Feisty install also did not work with the Marvell chipset manually configured.

LVM is a nightmare. It continuously tells me it cannot update the kernel about changes to MD0P2. I am running Linux MD RAID with LVM on top of it. These were existing partitions (from a previous SUSE 10.2 install), so I think that could be the problem here. I am still working this one out.

There does not seem to be a way to "wipe" the partitions and just plain start altogether over again.

If anyone is interested in my continuing saga, let me know, and I'll continue to post and update everyone with work-arounds.

-Bill

---

### Post by bebaumax on 2007-04-19
Ok, the exact error in the paritioning is:

-------------
Error informing the kernel about modifications to partition /dev/md2p1 -- Invalid argument. This means Linux won't know about any changes you made to /dev/md2p1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

ERROR!!!
-------------

I'm going to select Ignore. I have already gone and deleted the partition and recreated it in the partition manager.

Feisty now tells me that existing Volume Groups are detected and asks me if I would like to activate them. I've said No to this previously and had to recreate the Volume Groups and Volumes in them. It didn't help. If I say yes, at least I don't have to redo my Volumes. There is a VERY long delay here. I think it's something like 3-4 minutes per Volume in each Volume Group to activate. It doesn't help if you say No and recreate, then you have to wait for each Volume to be created, same delay time.

How interested, I had to ignore another LVM read error, but after that the install is continuing (as it has several times already). The interesting thing here is this time it asked me if my system is set to UTC. Previous times it asked the time zone but never asked this question.

I have run through this install 6 times now (still not successfully), but every time I get asked different questions. The hardware isn't changing, but the software sure does. :)

Previous attempts didn't have network access, this one does. So I'm watching Alt-F4 and see that it's sucessfully downloading packages on the fly this time. Maybe this will help the installation along a bit. :)

I'm going to hit post and start a new message from here.

---

### Post by bebaumax on 2007-04-19
Ok, it's over. I finally made it all the way through the install, and upon first boot attempt, it just stops at a black screen.

I'm sure this has something to do with 1 of most likely 3 things, maye a combination.

4GB RAM
ATI Video Driver w/ the latest kernel and/or Core2Duo proc
Core2Duo Proc / 965P Chipset w/ current kernel

If anyone figures any of this out or feels like having someone else try something, let me know, I'm usually willing to work on things.

---

### Post by RawMustard on 2007-04-20
Yep I'm having troubles with 64bit on Core2Duo also. Asus P5N32-sli Premium, nVidia 8800GTX, 4gig DDR2-800mhz ram, two seperate sata drives.
Live cd boots then extracts kernel and the screen goes black and nothing happens :(
32bit desktop cd works fine!  I'm running Feisty 32bit beta at the moment without issue!

And Poo, I was looking forward to trying out 64bit on this mother :(

---

### Post by shirsch on 2007-04-20
I feel your pain regarding the 4GB memory issue.  If you can get the system up with PCI remap disabled in the BIOS, try this:

- Edit /etc/modprobe.d/blacklist and add the line:

  blacklist intel_agp

- Rebuild init ramdisk:

  update-initramfs -c -k <your_kernel_version>

Try restarting with 4GB remap enabled.  This problem has been reported by many folks over the past 8 months or so.  Rather depressing that the underlying kernel and driver issues have not been addressed (this isn't particular to Ubuntu, BTW, I picked up the hint on a Blog dealing with SuSE)

There are also some workarounds for the Marvell ethernet issue.  By some stroke of luck, the one on my ASUS P5B Deluxe "just works".

---

