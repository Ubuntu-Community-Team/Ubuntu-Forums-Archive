---
title: "Installing Windows to a Linux machine"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by kzu on 2005-08-14
So, I need few programs from Windows, so I have to install it. I have my laptop 100% ubuntu linux now, so how do I make some space for windows, like 50/50? And, after i've installed windows, I can't boot to linux, right? I found out from other threads how to make bootdisks, but then when i'm back in linux, how do I configure the computer so that I can choose in startup what OS to use? I'm a newbie so pretty  
specific advices please :)

---

### Post by bjweeks on 2005-08-14
You can use Partition Magic 8 but that 80$ not sure if there's an open source alternative

---

### Post by Slugger on 2005-08-14
You would need to make a dual partition on your hard drive put windows on one and  linux on the other

---

### Post by bjweeks on 2005-08-14
Yes that would work but if you dont waqnt to reformat Partition Magic is the way to go.

---

### Post by Slugger on 2005-08-14
But it would save you 80 dollars :)

---

### Post by bjweeks on 2005-08-14
Well Partition Magic would make a second Partition without destroying the one you already have.

---

### Post by Slugger on 2005-08-14
[QUOTE=bjweeks]Well Partition Magic would make a second Partition without destroying the one you already have.[/QUOTE]
 Ops it said with destoring the partition you allready have. I still suggest making a dual partition and saving 80 dollars

---

### Post by Jenda on 2005-08-21
[QUOTE=Slugger]Ops it said with destoring the partition you allready have. I still suggest making a dual partition and saving 80 dollars[/QUOTE]
 OK, I'm no expert, but my $0.02 is:
Windows NEEDS to be on the first sector of the hard drive. If you installed Ubuntu on your whole disk, then you'll have to move it. [GParted](http://ubuntuguide.org/#gparted) is a Free program, easy to install thx to jiyuu0. Another option is the Free clone of Partition Magic, QTParted. I think you can get it via Synaptic. Partition Magic, AFAIK, is Windows only.
You can list your partition table using ```
sudo fdisk -l
``` and disk space usage using```
df -T -h
``` . This would help me. I suppose your hda1 is your / (root filesystem) partition of a certain size and your hda2 is your /home partition of a bigger size. You should have some free space on hda2. I will suppose that hda1 is big enough for the average Windows installation. If not, this would be a little more complicated. (I will explain once you give me your partition table and space usage)
Now you can use GParted or QTParted to resize hda2 to leave space approx the size of your hda1, create a new partition hda3, copy ALL the contents of hda1 to hda3, mount hda3 as / (root), format hda1 as, say FAT32, and install the Windows version you want. I know for a fact that Windows 98 will format your whole drive, so you should first research on which versions offer a partition selection BEFORE installation. I made the mistake with win98, and it messed up my MBR, and that only because I had to hard reboot, otherwise I would've lost my whole system (The MS bitches just don't want you to use another OS).

---

### Post by AnythingBut on 2005-08-21
You'll have to use parted off a bootable floopy.  Also make sure you figure out how to get GRUB back so you can boot into Ubuntu.  Check out
[http://www.ubuntuforums.org/showthread.php?t=58560](http://www.ubuntuforums.org/showthread.php?t=58560)

---

### Post by Jenda on 2005-08-21
Fixing the Master Boot Record is easy. You just pop in the install CD, make it install (make sure you tell it NOT to format your partitions) just like you did when you really installed, ignore the errors, and quit right after the "install boot loader" step. Make sure you tell it to "install" with the proper / (root) mount point.

---

