---
title: "Ubuntu Server 14.04 and RAID 1 Install Issues"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by TheHackMan on 2014-08-10
I am installing Ubuntu server on two brand new hard drives in a hardware based RAID 1 setup. I initially went with installing 12.04 since I had it on hand already. I got through the install alright but due to issues relating to the kernel version and the onboard NIC and crazy workarounds to get it working I decided to just download 14.04 LTS and install that version instead since all reports pointed to that being the solution. I deleted the RAID and recreated it and began to install 14.04. The install went smoothly however upon reboot I was presented with a blank screen and a flashing cursor which I could not get past. I assumed something went wrong during the install so I deleted the raid and files, recreated the raid, and then went through reinstalling Ubuntu Server 14.04 again but ran into the same issue of the blank screen and flashing cursor. After much trial and error the only way I could get things to work was by doing a software RAID on top of the hardware raid.

Doing it this way doesn't sit right with me and makes me thing I've done something else wrong along the way to cause these sorts of issues. Is the MBR/Grub not being deleted when I broke and recreated the RAID and is there a way to know for sure everything has been wiped? I was planning on running the following command:
```
dd if=/dev/zero of=/dev/sdc bs=512 count=1
```
to try and wipe everything and then trying the install one more time on a hardware only raid. Am I missing something along the way that would cause Ubuntu to have issues installing on a RAID 1 hardware based raid? The hardware raid is being created by the motherboard's onboard Intel raid system (MSI Z87 board) between two Samsung 840 Evos.

Another question, when installing does it matter if I choose to use 'Guided - Use Entire Disk' compared to 'Guided - Use Entire Disk and create LVM' with a RAID array?

---

### Post by TheHackMan on 2014-08-12
So after playing around with everything it would seem the motherboard doesn't actually do a hardware based raid like I had suspected which is what I believe lead to the issues. To fix everything I issued the
```
dd if=/dev/null of=/dev/sdX
```
command on both drives to wipe them completely and eliminated any possibility of GRUB hiding out somewhere to cause further issues.
I first removed the raid through the on-board Intel RAID BIOS, and then I then manually configured the RAID through the Ubuntu install disk and setup the partition with LVM after the raid was created.

Everything works as it should and I believe the problem originated from something with how the motherboard setup the software raid and how Ubuntu installed GRUB leading to issues when it would later try to boot. Wish things would have worked just using the motherboard RAID but weird issues crop up around every corner and with it all working well now I won't complain.

---

