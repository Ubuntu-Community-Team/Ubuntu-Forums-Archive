---
title: "A newbie : parittion scheme info"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by cbalasubramanian on 2011-08-25
Friends,
I want to try ubuntu and this is my first attempt with it. I have just downloaded the lastest 11.04 version.
My system is 32 bit asus laptop with vista already installed in it. The hard disk is partionted in the following way.
 
/sda1- 10 GB - ntfs - windows recover - primary 
/sda2- 60 GB - ntfs - vista os - primary
/sda3- 56 GB - ntfs - primay ( where i want to put ubuntu )
/sda5 -106 GB - logical drive.
 
I want to put ubuntu in /sda3. I have several questions regardin the partitioning scheme.
 
1) my ram is 4GB, how much swap i can give. Just a 2GB is okay or is it mandatory to have swap as twice the size of ram
2) do i need to have a seperate /boot
3) is this scheme optimal: swap , / and / home -> just three logical volumes inside /sda3. or is there any necessaity that one of the parition should be as primary
4) In case /boot is necessary, should it be made as primary and rest as logical drives. 
 
thanks,
Bala

---

### Post by Hakunka-Matata on 2011-08-25
> **cbalasubramanian said:**
> Friends,
I want to try ubuntu and this is my first attempt with it. I have just downloaded the lastest 11.04 version.
My system is 32 bit asus laptop with vista already installed in it. The hard disk is partionted in the following way.
 
/sda1- 10 GB - ntfs - windows recover - primary 
/sda2- 60 GB - ntfs - vista os - primary
/sda3- 56 GB - ntfs - primay ( where i want to put ubuntu )
/sda5 -106 GB - logical drive.
 
I want to put ubuntu in /sda3. I have several questions regardin the partitioning scheme.
 
1) my ram is 4GB, how much swap i can give. Just a 2GB is okay or is it mandatory to have swap as twice the size of ram
2) do i need to have a seperate /boot
3) is this scheme optimal: swap , / and / home -> just three logical volumes inside /sda3. or is there any necessaity that one of the parition should be as primary
4) In case /boot is necessary, should it be made as primary and rest as logical drives. 
 
thanks,
Bala

Welcome to the forums.

Where did you get the partition information you list?  I ask because sda6 is a logical partition; logical partitions reside within an Extended partition, and there is no Extended partition listed.

[LIST=1]
[*]2GB is enough, unless you want to 'hibernate'.  To hibernate use 4GB swap
[*]No
[*]Three logical partitions work well:
[LIST=1]
[*]/ (root), 15-20 GB
[*]/home - all your data and settings, bigger is better - a personal decision
[*]/Swap - 2GB
[/LIST]
 
[*]/boot is not necessary.
[/LIST]
Backup your windows data and make sure you have Vista Recovery or Install disks available.

---

### Post by cbalasubramanian on 2011-08-25
Thank you. I have successfully installed. But i want to check if nvidia graphics card is installed. How to check it by command line. Because when i go system- admin - additoinal driver. Nothing appears. Is there any way to check which driver is installed for my nvidia card

---

### Post by Hakunka-Matata on 2011-08-25
```
sudo lshw -C display
```

---

### Post by fdrake on 2011-08-25
> **cbalasubramanian said:**
> Thank you. I have successfully installed. But i want to check if nvidia graphics card is installed. How to check it by command line. Because when i go system- admin - additoinal driver. Nothing appears. Is there any way to check which driver is installed for my nvidia card

you can check with
```

lspci -vvv | grep nvidia
lsmod | grep nvidia

```

---

### Post by cbalasubramanian on 2011-08-25
The outputs are below. It seems ubuntu has installed nouveau.
**sudo lshw -C display**
*-display               
     description: VGA compatible controller
     product: G86 [GeForce 9300M G]
     vendor: nVidia Corporation
     physical id: 0
     bus info: pci@0000:01:00.0
     version: a1
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
     configuration: driver=nouveau latency=0
     resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:fa000000-fbffffff ioport:bc00(size=128) memory:fcfe0000-fcffffff

[B]
lspci -vvv |grep nvidia[/B]
Kernel modules: nouveau, nvidiafb

By why sys-admin- additional driver doesnt open when i click additional driver. How can i now install the driver ?

---

### Post by Hakunka-Matata on 2011-08-25
> **lspci -vvv |grep nvidia**
Kernel modules: nouveau, nvidiafb
**EDIT:  I missed your point, the Additional Drivers app should open and run, even if there are no additional drivers available.  I've done that and had a result of 'no additional drivers found', but which Release, I don't know.**
A 'more - or - less' explanation, I'm surely no expert on this.  But it looks like the Linux Kernel has drivers for your nvidia card already bundled with it.  System > Admin > Additional Drivers is for available drivers that Ubuntu is not licensed to include with GNU/LINUX licensing.   If Nvidia has other drivers available for your card, I guess you download them and install them.  Comments accepted.  das

---

