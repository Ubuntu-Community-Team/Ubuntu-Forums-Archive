---
title: "Problem in install/partitioning"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Ganymedes on 2008-03-17
I am trying to install Ubuntu 7.10 64 bit to a new computer. The specs are in the end. However, the partitioning phase in the install fails. First it just hangs in the point when it says 5% done (by hanging I mean that the mouse gets stuck and nothing happens in the next half hour).

When I then try again, there is a swap partition created. I then give the other partition mount point of "/" and filesystem type "ext3" and start it. Then it hangs again.

I can boot with the Live CD and starting the GParted in there. I am now trying to create an "ext3" filesystem for the "/dev/sda1" but it does not look good. It has tried that for an hour already. It feels that something is not right with this.

I have 6 SATA slots on my motherboard. I have only tried one red one. I think the red ones are for the boot. Then there are 4 black ones. Could it really make a difference what to use?

My system:
Asus M32A32-MVP Deluxe, AMD 790FX
Kingston HyperX,DDR2, 800 MHz, 4x1 Gb 
AMD Phenom 9600 2.3Ghz Boxed, 4 core
Club 3D 8500GT 512MB (Nvidia)
Seagate Barracuda 7200.11 500 GB SATA 3.0 Gbit/s

---

### Post by sandysandy on 2008-03-17
have a look at this link on installing ubuntu

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

regards

---

### Post by Ganymedes on 2008-03-17
Thanks Sandy!

Eh ... what part of that document your are referring to - it has links to everywhere. 

Are you perhaps saying that 4 core processor might be the problem ... even though it starts to install and live CD works?

---

### Post by sandysandy on 2008-03-17
its a general installation guide and covers issues from supported architecture, hardware support,  graphical install etc...

it even talks of Installation using the Alternate CD.

i could never install using the live CD, but the alternate CD installation worked flawlessly.

regards

---

### Post by prshah on 2008-03-17
> **Ganymedes said:**
> 
I have 6 SATA slots on my motherboard. I have only tried one red one. I think the red ones are for the boot. Then there are 4 black ones. Could it really make a difference what to use?

Seagate Barracuda 7200.11 500 GB SATA 3.0 Gbit/s

This particular board carries TWO SATA controllers, the red ones (Sil3132 chipset) and the Uli regular black ones; no difference which ones you use except that the Silicon Sil3132 chipset has a much better rating speedwise with true 3Gb/s performance.

Is there any virus protection preventing boot sector writes? Check the bios options.

Otherwise, boot from the liveCD and try creating the partitions manually using fdisk, then reboot and in the installer, choose manual partitioning and set up the mount points as required.

---

### Post by Ganymedes on 2008-03-17
Okay thanks both!

I tried now with the alternate CD and it did not help any. The partitioner in there (I chose "entire disk") hangs just the same.

Maybe my "ultra new and fast" hard disk is just not recognized by those partitioners? I will next try out the "fdisk" -approach.

---

### Post by Ganymedes on 2008-03-17
Eh, I just cannot get this to work.

First, there is no virus check on the motherboard. I also changed the hard disk to a Samsung 750 Gb disk to find out if that matters - it did not.

Alternate CD stucks just the same.

I can try to use fdisk and mkfs.ext3 on the Live disk, but they get stuck too.

I actually can create the /dev/sda1 ext3, bootable file system using Puppy Linux 2.17 fdisk. The Gparted in there gets stuck, too, but fdisk works.

However, when installing Ubuntu after that from the Live CD, using manual partitioning, changing the mount point to "/", if refuses to use it. Instead it says that it must be formatted. Not surprisingly, that stage gets stuck in the first 5% mark.

I am stuck, too with this install.

---

### Post by Ganymedes on 2008-03-18
No, does not work. I flashed a new BIOS to the motherboard and tried all partitionining/create filesystem scenarious that I could think of. I also tried another SATA driver (motherboard has two) and another disk type.

I am curious to know if somebody actually has got this motherboard to work with Ubuntu? It is Asus M32A32-MVP Deluxe, AMD 790FX  (see my first post for more details on my system.)

I guess it is not about the processor, because the Live CD does work. Should I just change to another Linux distro which would have a more recent support for this motherboard?

My goal is to use this 64-bit computer as a high end server for all kinds of Windows virtual computers that would ran under VMware workstation. I have a high end processor and motherboard combined with a lot of memory (planning to use  8Gb in the end), because I need to run several virtual computers at the same time. I know that VMware works under Ubuntu.

---

### Post by housam on 2008-03-18
Download and burn the [[COLOR="Red"]_newer version of Gparted _[/COLOR]]("http://gparted-livecd.tuxfamily.org/")and boot from this CD to partition your HDD manually . and during the installation process assign the partitions manually. ( you need at least 2 partitions - one as a root ( / ) ext3 format and the other is for the swap ( 1 to 2 GB is ok ))

---

### Post by Ganymedes on 2008-03-19
Thanks for all the help and tips in here. I did use the new version of GPart together with the alternate CD, which gave me new choices.

However, the real problem was not what was discussed. The problem manifested with Ubuntu so that creating the filesystem or when installing the packages (if the filesystem was created by other means), the system stuck. There were also slight boot problems.

Windows XP Pro installation worked OK.

Fedora 8 Linux behaved very erratically and the installation would get stuck in many different places.

The real problem was that the upper memory area slots were not working. When I removed chips from those two (there are 4 slots and you cannot use 3 of them, only 1, 2 or 4) everything started to work correctly. There was nothing wrong in the DIMMs themselves.

It was kind of against the odds that such a high level motherboard would have such a problem, but it did. 

Well, if I had used the memory test that comes with Ubuntu, I would not have struggled this long. The memory test tells the problem in no time.

Anyway, it now works with two chips and after the change withing the warranty, hopefully with all 4.

---

