---
title: "Unable to install Ubuntu 18.04 on 2018 HP Pavilion laptop"
date: 2018-10-28
forum: Installation &amp; Upgrades
---

### Post by mamboze on 2018-10-28
Hi,

I have been using Ubuntu on a laptop since 2010 and have installed all the versions since then up to 17.10, all on a Samsung RV11 laptop
I have now  encountered a problem trying to install Ubuntu 18.04 on a 2018 HP Pavilion laptop. 
So far, installation has proceeded as follows:
1. created a bootable USB flash drive from the Ubuntu 18.04 iso
2. booted into the Boot Manager via F9. this has 3 options:
OS Boot Manager (UEFI)
USB Hard Driver  (UEFI)
Boot from EPI fiile
3. I selected  USB Hard Drive (UEFI) option The installation process proceeded OK (including wifi connection and normal installation and download updates selected) until coming to the page where the laptop hard disk partitions are defined.
4. Here, in the upper area where the partitions are defined, /dev/sdb is shown as the device to be partitioned, but this is the flash drive. As I understand it, /dev/sda should be displayed here.
5. /dev/sda is shown in the small dropdown menu at the bottom of the page entitled "Device for boot loader installation"

I am at a loss as to what to do now. I am aware in a general way that UEFI might be a factor here, but my knowledge is limited. I also tried googling the problem but have been unable to turn up anything specific. I would very much appreciate any help. I am reluctant to take the very backward step of staying with the Windows 10 OS currently installed.

---

### Post by yancek on 2018-10-28
If you have windows 10 currently installed, the most frequent cause of this is leaving windows in the default hibernation state.  Anything related to hibernation/fastboot must be off or the Ubuntu installer will not mount the partition and you will then obviously, not see it.  Same with any other Linux system.  They will not mount any hibernated system as there is a serious possibility of data loss.

---

### Post by ajgreeny on 2018-10-28
HP makes life a bit more difficult for Linux users than it supposed to by not following the agreed standards for UEFI.

Look through the info detailed in post #2 by my colleague [COLOR="#FF0000"]oldfred[/COLOR] at [https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797) which hopefully will solve your problem.

---

### Post by mamboze on 2018-10-28
Thanks for your help. I ran **powercfg.exe /hibernate off**  in the Command Prompt (Run) dialog box, but this not fix the problem, the hard disk, /dev/sda  cannot be partitioned. /dev/sdb occupies the upper window as I described above.

---

### Post by mamboze on 2018-10-28
@ajgreeny,  thanks for your comments. I checked out the link. It refers to dual boot. I would very much prefer to have Ubuntu as the sole OS. Can this be achieved? I really hope so.

---

### Post by oldfred on 2018-10-28
Many are finding UEFI updates from vendor are required.
And if an SSD, firmware updates also are required.

Post these:
sudo parted -l
sudo gdisk -l /dev/sda

---

### Post by mamboze on 2018-10-28
@ajgreeny, sorry, I initially looked at BarryBKS post and missed the highly detailed post of old fred just below. Thanks very much for your help, it's much appreciated. I feel I'm getting close to a solution.

---

### Post by mamboze on 2018-10-28
@old fred, the HP Pavilion has 16 GB PCIe® NVMe&#8482; Intel® Optane&#8482; which is, I think, SSD. So does this preclude installing Linux?

---

### Post by mamboze on 2018-10-28
Where are sudo parted -l    sudo gdisk -l /dev/sda to be posted?

---

### Post by oldfred on 2018-10-28
You just copy & paste here. If longer use Code Tags.
You can easily add code tags with Forum's advanced editor and # icon.

That will be NVMe drive not sda. And almost all seen to need firmware updates.

---

