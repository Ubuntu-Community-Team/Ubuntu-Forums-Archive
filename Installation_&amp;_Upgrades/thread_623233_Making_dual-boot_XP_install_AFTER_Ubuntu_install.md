---
title: "Making dual-boot XP install AFTER Ubuntu install"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by tedrogers on 2007-11-25
For reasons I'm a little ashamed of, I want to install XP on my Gutsy system **after** my Ubuntu install, and for some reason I am unable to find posts which can help me here.

I want XP so I can run Explorer for all those web-shaits that don't work with Firefox, Opera or Swiftweasel etc.

I also want to play my old favourite games like Grim Fandango...which quite frankly are poor at best (if I can get them installed at all) under Wine on my paticular system. Not dissing anyone else's system there though...I'm sure some people have a lot of joy with it.

So far, I have 3 partitions:

/sda1 which is my main ubuntu disk
/sda2 which is my swap
/sda3 which is an extended partition
/sda5 which is a backup partition from the /sda3 extended one (I use this for partimage backups)

I shrunk /sda1 and created /sda4 which I have formatted to NTFS ready to install XP.

Here's the output from fdisk -l

```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3919    31479336   83  Linux
/dev/sda2            5731        5991     2096482+  82  Linux swap / Solaris
/dev/sda3            5992        7296    10482412+   5  Extended
/dev/sda4            3920        5730    14546857+   7  HPFS/NTFS
/dev/sda5            5992        7296    10482381   83  Linux

```

So, my questions are:

1. I know XP will overwrite my GRUB. Can I prevent this in any way or make a backup of my GRUB (menu.lst???) so I can easily restore it.

2. Assuming that I will have to restore my GRUB from system rescue, how do I go about getting XP to boot by adding it to my menu.lst??

I haven't gone any further than formatting the new partition (/sda4) as NTFS yet...and I'm hoping to get some advice before I proceed so I can avoid headaches and general banging of the head on the wall.

If you need to know anything then please ask. 

All help appreciated.

---

### Post by Pumalite on 2007-11-25
Installing XP after Ubuntu will create all sort of problems for you. The way it should be is XP first, then Ubuntu. You can run XP in Virtualbox in Ubuntu, especially if you need it for just one application.

---

### Post by tedrogers on 2007-11-25
Could you enlarge upon the **problems** you expect I could encounter? I don't quite understand what could happen.

Surely XP will be self-contained on a single partition, and any major issues can be resolved by wiping that partition and restoring the grub loader??

Please correct me where appropriate....I'm just trying to learn.

Also, assuming I wanted to abandon the XP install idea....do you recommend Vmware as well as Virtualbox?

Thank you.

---

### Post by ericartman on 2007-11-25
Found this when I hit the Vista second install wall

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Lotsa luck I ended up backing up Ubuntu and did a complete install of both systems Vista first. When I used to use Vista.

Cart

---

### Post by meierfra on 2007-11-25
> Surely XP will be self-contained on a single partition, and any major issues can be resolved by wiping that partition and restoring the grub loader??

You are 100% right. With your set-up you should have no problems installing Windows. 

After you installed Windows do the following.

1)  Reinstall Grub:

Boot from a Ubuntu Live CD or the LInux Rescue CD. Open a terminal and type

```
sudo grub
root (hd0,0)
setup (hd0)
quit 
```

(The  "sudo" probably is not needed on the Rescue CD)

Reboot into Ubuntu

2) Add Windows to the grub menu:

Open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```


Change "hiddenmenu" to "#hiddenmenu"

and add the following to the end of the file:

title Windows XP
root (hd0,3)
makeactive
chainloader +1

Save the file and you should be all set.

---

### Post by tedrogers on 2007-11-26
Great meirfra! That's what I thought. And thanks for the lines of code...really helpful.

How did you work out that my sda4 will be hd0,3? Is this because hd0,0 is the first disk (and because to computers a 0 counts as a digit) then 3 is actually the 4th partition along?

I have a complete image of my ubuntu install created with partimage anyway, so I can always go back to this.

Virtualisation is always going to be slower that the real thing. I really only want XP to run a few measily websites that aren't supported under Linux...4OD (channel 4 TV on demand - in the UK) for one! I moaned at them for not running a Linux version, but they just gave the old 'most users use XP' line. Tssk!

Am I right in thinking I can restore my MBR from my partimage disk image as well...which is effectively the same as reinstalling grub as your code will do?

Thanks.

---

### Post by MadMardigan on 2007-11-26
I too am having a similar problem, I'm booting on 2 HD's, the primary (with windows vista) is a SATA, the slave is IDE (with Ubuntu).

Here's my fdisk -l output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67e35894

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a11f15b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9587    77007546   83  Linux
/dev/hdd2            9588        9964     3028252+   5  Extended
/dev/hdd5            9588        9964     3028221   82  Linux swap / Solaris

```

And here's my menu.lst file:

```
title		Windows Vista
root		(sda1,0)
savedefault
makeactive
chainloader	+1


title		Ubuntu, kernel 2.6.20-15-generic
root		(hda1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=af7ee820-e53e-448f-9323-60f3a3754bbf ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet


title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hda1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=af7ee820-e53e-448f-9323-60f3a3754bbf ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hda1,1)
kernel		/boot/memtest86+.bin
quiet
```

I'm just not quite sure how to figure out the whole (sda1,0) and (hda1,0) labelling. If anyone can help, I'd appreciate it. I think this would also help to answer tedroger's question.

---

### Post by tedrogers on 2007-11-26
I know what you mean mate! My wlan0 is called eth1??? :confused:

I find this whole area quite confusing and it seems to change every so often with a new release. In feisty by HDDs were known as hda, now in gutsy they are sda?? :confused:

---

### Post by Therion on 2007-11-26
If I understand things correctly, sda indicates a SATA drive, while hda indicates a PATA drive.  

**MadMardigan:**

I was, at one point, doing exactly the same thing as you are now: Windows (XP) on a primary, SATA hard drive and Ubuntu on a secondary (slave) PATA drive.  That setup caused me all kinds of headaches.  What I did was backup all my existing Ubuntu data from the slave drive, used the gParted LiveCD to shrink the Windows partition on the SATA drive and then installed Ubuntu on the same SATA drive, using the existing free space not occupied by Windows for the Ubuntu partition/install, letting GRUB handle the dual booting options.  

I physically disconnected the slave drive to do this to prevent any possibility of overwriting the existing Ubuntu install on the slave drive, but also to allow me to test-drive the dual booting SATA drive before reformatting the slave drive (also using gParted) into one big, NTFS data-storage drive, accessible by both Window and Ubuntu.

Unless of course you have some compelling reason NOT to use one drive for both OS'es; but if not, this is the route I would suggest.  It's been perfect for my situation.

---

### Post by MadMardigan on 2007-11-26
That's what I thought of doing too. However, I need to get into windows first to do it so that I can partition it without erasing, correct?

---

### Post by Therion on 2007-11-26
> **MadMardigan said:**
> That's what I thought of doing too. However, I need to get into windows first to do it so that I can partition it without erasing, correct?
If you use the [gParted LiveCD]("http://gparted-livecd.tuxfamily.org/download.php"), you can boot directly into gParted.  From there you shrink the Windows partition.  Use your Gutsy LiveCD/DVD to partition/format the remaining free space and continue with the install.  *Voila!*  Your Windows partition is smaller, but unharmed.  GRUB will update the MBR during the install process and allow you to choose which OS to boot into.

---

### Post by meierfra on 2007-11-26
tedrogers:

> How did you work out that my sda4 will be hd0,3? Is this because hd0,0 is the first disk (and because to computers a 0 counts as a digit) then 3 is actually the 4th partition along?


Exactly right.  Grub starts counting at zero. (hd3) is the fourth hard drive. (hd3,5) is the sixth partition on the fourth hard drive.

Ubuntu uses hda, hdb, ... for the IDE drives and sda,sdb,.. for the Sata drives. But lately it started using sd  for all the drives. So sdd6 is the six partition on the fourth hard drive


> Am I right in thinking I can restore my MBR from my partimage disk image as well...which is effectively the same as reinstalling grub as your code will do?

Yes.

---

### Post by meierfra on 2007-11-26
MadMardigan:

Can you tell me more about your current situation? 
 What is your problem?  Are you able to boot into windows? Into Ubuntu?  
Does the Grub menu appear at boot up?  
Why are you thinking about reinstalling? 
How much did  you edit your menu.lst? (all the (hd?,?) seem to be wrong)

Ubuntu calls your drives sda and hdd. There is no "b" and no "c". That often means that your hard drives cables are plugged  in wrong.

---

