---
title: "RAID problem with GA-X58-usb r1 motherboard"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by chipppy on 2011-05-16
Good Evening

I am trying  to install Mythbuntu 11.04 on a new build PC
The mother board is a gigabyte GA-X58-USB3 mobo.
I have installed 5 2TB HDD's and tried to install as RAID5.  I followed the instruction in the manual to setup the RAID and all looked good.
Tried to install Mythbuntu but it failed as it cannot install the bootloader.
I tried removing the RAID and just installing on one HDD that worked fine.

I tried the RAID again and noticed that when i set it up it becomes initalise and bootable = no.  I cannot find anyway to change it to bootable.

I tried using windows 7 and doing a RAId setup that way using the driver supplied.  installed the driver during windows install but windows wont install due to the drive not being bootable.

Anyone with any ideas of how to get the RAId working???

Cheers
chipppy

---

### Post by chipppy on 2011-05-17
bump
anyone able to help?

Cheers 
chipppy

---

### Post by chipppy on 2011-05-19
bump

---

### Post by tasaif09 on 2011-05-22
I'm going to buy this motherboard soon. Have you tried installing other flavors of Linux? If you can get it working in other flavors, you would at least have narrowed the problem, if even slightly. I'm very interested to hear how this goes for you, as it may apply to me in the near future.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Did you check your hardcopy manual that came with the MB and your BIOS settings?  You may need to set it up in BIOS first and save.

---

### Post by chipppy on 2011-05-24
Good Afternoon
After much stuffing around, including being stuffed around by mobo 'help' section I think ?I have found the answer.

This mobo has the ICH10R chipset for the southbridge.  this is the fake RAID controller.  this is an Intel chip which the mobo manufacture dosent appear to have the full code to run fully.  What does this mean

Only RAID <2TB will be bootable.  Anything > 2TB will automagically be set to non-bootable and this cannot be changed.

Therefore solution is
Make 2 RAID partitions
1 for the OS (I used 250GB in my case)
2 for storage and mount it into the OS partition somewhere as per normal.

Some helpful hints from pain I have suffered

When trying to format a partition > 2TB set the partition table to GPT as all other cannot handle such big drives.

When trying to mount use ```
sudo lshw -l disk
``` to find your RAID disks names.
They will appear as /dev/dm-0, /dev/dm-1 llok at the sizes to work it all out
the individual drives will appear at the top /dev/sda, /dev/sdb, /dev/sd* etc so it can look like a lot of infurmation

Mounting the RAID drive is as per normal though from the command line

GParted can be used to format the RAID drive just us the advance option when setting the partition table type (GPT)

Useful links
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

Hope this helps a little

Cheers 
chipppy

---

