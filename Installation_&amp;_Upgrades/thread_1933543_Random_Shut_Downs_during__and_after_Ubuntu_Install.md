---
title: "Random Shut Downs during  and after Ubuntu Install"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by GenericPlayer on 2012-02-29
I have been trying to install Ubuntu on my computer for 2 days now and the computer will shut off randomly during install.

Here is the chronology of the problem:

1) Used the 11.10 Desktop boot CD and it crashed randomly. Sometimes during installation or when I am selecting partitions, or sometimes even before I get that far.

2) One of the installation attempts goes through and Ubuntu is installed, but the random shut downs continue. After some reading, I go to system settings and add Nvidia drivers. However system will always crash before the download is complete.

3) I go to the Nvidia website and manually download the driver, and use Ubuntu recovery mode to install it (telinit 1). Recovery mode also had random shut downs and it took a few attempts before the computer stayed on long enough to install the Nvidia drivers

4) After the GPU driver update, X windows (or Unity in this case) won't start up

So I format the drive and try a fresh install. I tried both the Ubuntu Server and Ubuntu Alternate CDs with no luck, the random shut downs always happen before I get a chance to install. The stage at which they happen is random as well, it could be during partitioning, formating or even in earlier set up stages.

Here is what I have tried so far with no luck, same problem always happens:

1. Used f6 to run the install with nomodeset
2. Installing on a different HD while having the others disconnected.
3. Disconnecting my DVD drive and using a USB stick to boot.
4. Disabling USB 3.0 from the BIOS
5. Disabling the Ethernet ports
6. Upgraded to the latest BIOS for motherboard.

My computer runs Win 7 x64 with no issues. The CPU temperature LED display on my motherboard shows no indication of overheating, and I have an obscenely oversized heat sink on my CPU. I have not overclocked my CPU or RAM. I ran memtest and it found no errors

My specs are:-

Motherboard: EVGA Z68 LGA 1155 Model 130-SB-E685-KR
CPU: Intel Core i7-2600K
RAM: Corsair Vengeance 16GB (4x4GB DDR3)
GPU: EVGA Nvidia GTX 470
Hard Disks: Corsair Force GT 120GB, WD Caviar Blue 1TB, WD Caviar Green 2TB, Seagate Barracuda XT 3TB. Never used RAID on any of the disks

In all cases I am attempting a 64 bit installation of Ubuntu. I could try 32 bit, but it would defeat the purpose of what I will be using Ubuntu for (number crunching).

---

### Post by GenericPlayer on 2012-03-01
I appear to have solved the problem. In a last ditch effort I did the following

1. Disabled the BIOS "hotplug" option on my Corsair Force GT SSD. I had been using this to make sure the SSD does not 'sleep' after periods of inactivity. I do not use this drive at all for my Ubuntu installation in any way (either as a partition or boot sector) so I doubt this changed anything, its more of a hail mary

2. Installed from the Ubuntu Alternate CD, only this time I used the parameter 'noacpi' in addition to 'nomodeset'.

Ubuntu seems to be running smoothly. I managed to successfully install the Nvidia driver using the 'Additional Drivers; option in the system tools. It looks like clear sailing for now.

Any idea how I can mark this as solved?

---

