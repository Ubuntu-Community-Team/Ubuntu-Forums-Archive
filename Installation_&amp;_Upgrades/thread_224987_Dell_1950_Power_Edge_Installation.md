---
title: "Dell 1950 Power Edge Installation"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by cbschuld on 2006-07-28
Hello All:

Has anyone successfully installed Drapper on a Dell PowerEdge 1950?  

Two problems, the PERC (LSI) RAID SAS array appears to work through the installation but after GRUB launches it cannot find the device again (/dev/sda1) and drops into a shell.  Secondly, but less of a problem right now, the Broadcom NetXtremeII Adapters ( 5708 ) do not function (out of the box).

Anyone have any thoughts?  Dell had told me it would work with Ubuntu "no problem"

Thanks in advance,
Chris

---

### Post by ScislaC on 2006-07-29
Have you had any success with this? I have a 2950 and the exact same problem. It finds the raid fine when run from the LiveCD and seems to install w/o a hitch... it's just the booting into it issue.

---

### Post by cbschuld on 2006-07-29
No luck as of yet.  The install works but then on the reboot I get the error about VFS not locating the device /dev/sda1.  There appears to be a lot of chatter on this forum about the /dev/sda1 (or similar device) not being found on boot but I have not found a definite answer yet.  Dell support on Ubuntu (or anything other than Windows or their magic flavor of RedHat) has been bad (expensive and bad; an interesting combination).  I assume if I could get the thing to boot out of Grub right I could fix the NIC issues.  But no luck.  What do you see on the 2950?

Regards, Chris

---

### Post by ScislaC on 2006-07-29
As of this point, I've really only made it as far as you were in your initial post... but I'm seeing what I can figure out. I think one of my bigger issues at the moment is that the amount of utilities on the box at this point is so limited (due to it being "mid-install") that my normal methods to figure it out are useless.

---

### Post by ScislaC on 2006-07-31
I did want to let you know that I've tried both the server and desktop editions. The interesting thing is that the Live CD both installs fine, but the NIC also functions fine as well. This is too bizarre. I'm still trying to figure things out as well... my guess is that with a little hackery it can be fixed.

---

### Post by az on 2006-07-31
> **ScislaC said:**
> I did want to let you know that I've tried both the server and desktop editions. The interesting thing is that the Live CD both installs fine, but the NIC also functions fine as well. This is too bizarre. I'm still trying to figure things out as well... my guess is that with a little hackery it can be fixed.

Maybe it's the linux-server kernel.  What if you install the server version, but before you reboot, go to a virtual console and install linux-386; that's the kernel you get with the desktop version.

If that's the case, a bug report is in order.

---

### Post by cbschuld on 2006-07-31
I am definitely hungry for the right answer.  I attempted to install Server, Desktop and Alternate without any luck.  On a complete side note I installed Fedora Core 5 without any issues at all -- even grabbed the new BroadComm NICs.  I'd prefer to stay Ubuntu but due to business demands we may be stuck running FC 5.  

:confused: 

I believe the problem is in the mounting of the /dev/XXX device right after GRUB unscrews the boot image but I do not have enough low-level GRUB experience to finger the problem.

I am going to keep hunting!

--Chris

---

### Post by IanOKeeffe on 2006-08-02
Have you compared the initrd image from FC5 with that of Dapper? It sounds very similar to an issue I experienced using dmraid.  

My experience was that the distro (OpenSuSe 10) would install perfectly but fail to boot (sounds like the same problem you have).  The problem turned out to be that the initrd image didn't contain the binaries for the dmraid tool or the lines in the init script to load it.  Solution was to make a custom initrd image.  In your case, my guess would be that the driver for the SAS controller isn't being loaded by the initrd so the kernel fails to load.

I'm very interested in whether or not you solve you current problem, I will most likely be configuring a Poweredge 2900 in a week or two.  It has a SAS backplane like the 1950.

---

### Post by ScislaC on 2006-08-02
Got it to boot thanks to another post I found... It's all caused by an issue with the Debian installer. Anyway, install the server edition and when it's all done, but BEFORE you reboot, do the following:
-
Alt+F2
chroot /target
echo "megaraid_sas" >> /etc/mkinitramfs/modules
mkinitramfs -o /boot/initrd.img-2.6.15-23-server 2.6.15-23-server
exit
Alt+F1
-
After that you can choose to reboot, it will hang and you will need to use the power switch to get it to restart. After restart it will boot up fine. :)

(wrt the initrd.img, that's what I recall the name to be, but that may be slightly off)

Now I'm just trying to get the NIC stuff up and running.
-Josh

---

### Post by ScislaC on 2006-08-02
And networking is now up too... Once you get the install done and it boots, log in and do the following:

sudo nano /etc/network/interfaces

(add the following to the file)

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
auto eth1

(press Ctrl+X, hit Y to save)

Then you can do:

sudo ifup ethX

(X is either 0 or 1 depending on which you want to activate, or you can do them both individually)

Hope that helps! My server is doing well now... now to continue configuring it... :)
-Josh

---

### Post by ScislaC on 2006-08-02
Worth noting, I got all the juicy help from [http://ubuntuforums.org/showthread.php?t=226114](http://ubuntuforums.org/showthread.php?t=226114) (Thanks Grizzly_Adams!)

I just filled in a few details in my posts (to help out).

-Josh

---

### Post by simoon on 2006-09-14
> **ScislaC said:**
> Got it to boot thanks to another post I found... It's all caused by an issue with the Debian installer. Anyway, install the server edition and when it's all done, but BEFORE you reboot, do the following:
-
Alt+F2
chroot /target
echo "megaraid_sas" >> /etc/mkinitramfs/modules
mkinitramfs -o /boot/initrd.img-2.6.15-23-server 2.6.15-23-server
exit
Alt+F1
-
After that you can choose to reboot, it will hang and you will need to use the power switch to get it to restart. After restart it will boot up fine. :)

(wrt the initrd.img, that's what I recall the name to be, but that may be slightly off)

Now I'm just trying to get the NIC stuff up and running.
-Josh


Hi,
i got the same problem, but when i use this solution the grub returns error 21 at booting. Do you got raid running (i got raid 0) or does this work only without raid? I think the Problem is that the installation sees even the real hard disk sda sdb and not only the virtual sdc which should be used.
does anyone know how to fix it?

thanks
alex

---

### Post by Prelius on 2006-09-26
OK, I got the RAID working under 6.06.1. 
Step 1: Delete RAID Array config from BIOS
On server boot, press <CTRL><R>, and delete current logical disk, whatever config you have, RAID0/1
Step2: Install Ubuntu
Boot from install CD, and when get to the disk partitioning, use SW RAID to congigure disks. I did RAID1.
Step3. Update initrd.img
BEFORE system reboot, press <ALT><F2> to get to the console. Hit enter, then chroot to /target (chroot /target). add megaraid_sas to the list of modules:echo "megaraid_sas" >> /etc/mkinitramfs/modules. Now  update the existing initrd.img to include the RAID dirver by using using update-initramfs (update-initramfs -u). Exit from chroot and switch back to the installer. Reboot.
Step 4: Restore RAID config on controller
On server boot, press <CTRL><R>, and create a logical disk of the same type as your SW raid. Save config and reboot... Done...

---

### Post by schamane_ on 2006-09-28
Hi all,

i got small problems too in trying to install ubuntu server on an 1950 PE.

The Problem is it doesnt recognize the RAID as real RAID.

It`s an RAID1 but i see 3 disks.
the two disks an the raid-disk. if i install on sdc (wths is the RAID Controller) i cant boot, it gives me error 21 like simoon already said.

The problem depends on the megaraid_sas driver included in Kernel, in the next version this failure is fixed.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/57265](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/57265)

So it would be nice to get an customized installation disk or an pre-beta or something like this of 6.06.2 if the kernel changed, then i think this prob should be solved


@simoon

how many disks are build in in your server and how many are recognized by the installer.


@prelius
where have you installed grub? on which disk?
and how is your partitioning? i mean to remember there exists problems with mbr in software raid but i dont have you used software raid often.

any help will be appreciated


regards

Schamane_

---

### Post by schamane_ on 2006-09-28
Hi again,

i got it working now, but not really the way it should be.

Because if one disk fail, the fstab informations are wrong because sdc is not logner sdc it changes to sdb. 

So i can manually edit fstab, but its not a good solution.

it would be fine to get some answers
Thx

Schamane_

---

### Post by Prelius on 2006-10-05
@prelius
where have you installed grub? on which disk?
and how is your partitioning? i mean to remember there exists problems with mbr in software raid but i dont have you used software raid often.
any help will be appreciated

 Remember, the actual disks' partitioning is handled by the softraid, so I just specified that I needed 3 partitions total :/boot; / ; and swap. Then created three VDs, and assigned partitions to those VDs. (This is all done through a SoftRAID installer). the installer then does all disk slicing. The GRUB is installed into MBR of a RAID, so effectively, it is installed on each of the disks (in my case 2 drives). When I reassemble the hardware raid, only the first disk's MBR is available (and this is a problem, since there is no "true" redundancy from booting failures), but I can live with it until the next release. So, when my machine boots, grub sees what it thinks is the RAID MBR, and complains that the RAID is broken, but boots up fine.
  

regards

Schamane_[/QUOTE]

---

### Post by kam66be on 2006-10-29
anyone try Ubuntu 6.10 on Dell 1950? can it detect the raid hhd correct?

---

