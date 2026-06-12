---
title: "New install won't boot.."
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Eaty2k on 2007-03-06
I just installed ubuntu on a separate hd then my xp install.  I can't see grub and my windows boots up like normal.  Here is what my fdisk -l looks like:

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17546   140938213+   7  HPFS/NTFS
/dev/sdb2           17547       19396    14860125   83  Linux
/dev/sdb3           19397       19457      489982+  82  Linux swap / Solaris


Now the first one hdb1 is a 80g IDE that I use for windows as backup.  The sda1 is my primary windows install all 250g of it.  It is setup in my bios as a sd0.  My second SATA drive is sd1 in bios and it setup with 140g being used for windows then the rest is my linux partition.  I have tried to jumble the hd around in the bios to see if any of them would boot, but no dice.  

I have used grub -> root (hd2, 1) -> setup (hd0) but no dice.  I tried using setup (sd0) but it returned a error 23 parsing number error.  Please help me as I am out of options ;(

---

### Post by bernied on 2007-03-06
This sort of thing seems to be happening a lot with SATA drives lately. Grub doesn't seem to agree on the disk numbering that is assigned by the installer.

See if this thread helps at all:
[http://www.ubuntuforums.org/showthread.php?t=376858](http://www.ubuntuforums.org/showthread.php?t=376858)

---

### Post by bulldog on 2007-03-06
Grub only counts you hdd's with a number like (hd0),(hd1) and so on,not (sd0).
To find out how ubuntu sees your hdd's order type in a terminal,```
cat /boot/grub/device.map
```
You can see which one is (hd0).
On this disk is probably Grub installed by default.
To change the Grub install to another disk like your sda drive,you'll have to notice how it's listed in your device.map.
I think your sda is (hd1) and in if that's the disk were you're booting from,you need to install Grub to that disk.
Use the live cd to install Grub to your sda1 disk.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)<------probably (hd1) see your device.map command
```
Exit the grub shell
```
quit
```

---

### Post by Eaty2k on 2007-03-06
Good to know about the the SATA drives not being sd0,1 and so on.  When I boot from Live CD I can not see any dir after /boot.  There is no grub dir or anything in there.  Is there another way to see the device map?

---

### Post by bulldog on 2007-03-06
Yes there is,but I presume you boot from your sda disk with the windows installed?
If yes I'm pretty sure it's the (hd1) you need to install to.

IDE disk is always before sata so your IDE is hd0 and sda is hd1 and sdb is hd2.

You can put GRUB on the sdb disk [hd2] and leave the windows disk with it's own boot loader.
The only thing you have to do is change the boot order in your BIOS and set sdb as your first boot device.

In case of troubles you can always boot windows by changing this disk back as first boot device in the BIOS.

If you do so you need a little modifying to your menu.lst but that's a minor thing to do,and I can help you with that if you want.
Let me know what your decision is.

---

### Post by bernied on 2007-03-06
It is not necessary to do the setup command.
Grub is already loading and the menu.lst is found if windows is bootable. The problem will be with the entries in the menu.lst file.

Does the live CD give you access to your ubuntu install? - you should get a disk icon on the desktop. If you can find the file /boot/grub/menu.lst you need to edit it.

But first you need to work out how grub sees your disks. If you mess about in the grub command line, using tab-completion, you will work it out.

Try [this](http://users.bigpond.net.au/hermanzone/p15.htm) page for some more info.

---

### Post by bernied on 2007-03-06
Oooops, my apologies, I just re-read your first post and maybe I misunderstood.
So grub is not loading at all?? No boot menu?

Please ignore my posts. My apologies again.

---

### Post by bulldog on 2007-03-06
> **bernied said:**
> It is not necessary to do the setup command.
Grub is already loading and the menu.lst is found if windows is bootable. The problem will be with the entries in the menu.lst file.

Does the live CD give you access to your ubuntu install? - you should get a disk icon on the desktop. If you can find the file /boot/grub/menu.lst you need to edit it.

But first you need to work out how grub sees your disks. If you mess about in the grub command line, using tab-completion, you will work it out.

Try [this](http://users.bigpond.net.au/hermanzone/p15.htm) page for some more info.

Grub is installed on (hd0) by default and I presume TS is booting from his sata disk into windows,without ever seeing GRUB.
So it's installed on the wrong hard disk.

I'm aware that there is more than one way to solve this problem.
But to keep it simple,it's the best thing to install Grub to the disk were TS is booting from.
Now he has the choice to choose sda or sdb,I only give him a choice to keep his windows install completely outside Ubuntu,in case he ever gets trouble with Grub,he always can boot into windows with it's own boot loader.

---

### Post by bernied on 2007-03-06
> **bulldog said:**
> Now he has the choice to choose sda or sdb,I only give him a choice to keep his windows install completely outside Ubuntu,in case he ever gets trouble with Grub,he always can boot into windows with it's own boot loader.I agree, with two disks it's a good idea to keep the windows mbr on the windows disk, then if you ever remove the linux disk (as if) windows will happily resume its ignorant life.

I misunderstood the nature of the problem from the beginning. 

Did it work?

---

### Post by Eaty2k on 2007-03-07
sorry for the delay... just got home from work.  I tried and used setup (hd2) and the grub menu came up!!  But when I tried to boot it gives me an Error 22 and says no such partition.  I tried to edit the menu by using root (hd1,2) and (hd2,2) and was getting nothing.  Please lay some more of that good ole knowledge :)

---

### Post by bernied on 2007-03-07
If your linux install is on /dev/sdb2 then the grub equivalent will probably be (hd2,1). 

Grub starts counting partitions from 0, unlike linux which starts from 1. Normally /dev/hda1 would be (hd0,0), /dev/hdb3 would be (hd1,2) etc. Your setup is a little different with your mixed ide and sata drives so the disk numbers/letters don't match up between linux and grub, but the partition numbers should match up, just subtract one when converting from linux to grub.

Now is the time when my earlier posts might become useful, especially that link to Herman's dual-booting site. It's very useful knowledge to have if you're going to be messing about with multiple disks and multiple operating systems.

---

### Post by Eaty2k on 2007-03-07
Well that makes sense, because my linux partition is on hd2,1, But I am still getting Error 22.  I don't really know if there is a way to edit the menu.lst without being able to boot into ubuntu.  I can use the live CD, but I can not boot into the hd2, 1 partition where I installed ubuntu.  If there is a way to edit the menu.lst let me know...

---

### Post by bulldog on 2007-03-07
Of course there is a method :) 
You have to mount your ubuntu to read and modify menu.lst.

Boot the live cd and open a terminal.
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sdb2 /mnt/ubuntu
```

To open your menu.lst [please copy it here]
```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

I think you should have a look at your fstab too.
```
gksudo gedit /mnt/ubuntu/etc/fstab
```

Keep in mind your opening this files as a root,so be very careful with your modifying please.
Better to make a copy of both before opening them.
```
sudo cp /mnt/ubuntu/boot/grub/menu.lst /mnt/ubuntu/boot/grub/menu.lst_backup
sudo cp /mnt/ubuntu/etc/fstab /mnt/ubuntu/etc/fstab_backup
```

---

### Post by Eaty2k on 2007-03-07
Thank you SOOO much bulldog for the help.  I found out what I did wrong, so  operator error here.  I changed the boot sequence in the bios to boot the Linux drive first and that made it hd0 as a opposed to hd2.  When I did hd0,1 Ubuntu booted in all its glory.  Thanks again for all you help.

---

### Post by lakamsani on 2007-03-11
bulldog, 

Do you have anyt thoughts on this post of mine. I have a much simpler setup (/boot/grub/device.map has a single mapping of hd0 to sda) but Ubuntu 6.10 won't boot. 
 
[http://www.ubuntuforums.org/showpost.php?p=2281917&postcount=14]("http://www.ubuntuforums.org/showpost.php?p=2281917&postcount=14")

---

### Post by lakamsani on 2007-03-11
bulldog, 

Do you have any thoughts on this post of mine. I have a much simpler setup (/boot/grub/device.map has a single mapping of hd0 to sda) but Ubuntu 6.10 won't boot. 
 
[http://www.ubuntuforums.org/showpost.php?p=2281917&postcount=14]("http://www.ubuntuforums.org/showpost.php?p=2281917&postcount=14")

---

### Post by bulldog on 2007-03-11
> **lakamsani said:**
> bulldog, 

Do you have anyt thoughts on this post of mine. I have a much simpler setup (/boot/grub/device.map has a single mapping of hd0 to sda) but Ubuntu 6.10 won't boot. 
 
[http://www.ubuntuforums.org/showpost.php?p=2281917&postcount=14]("http://www.ubuntuforums.org/showpost.php?p=2281917&postcount=14")

Can you post the output of ```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
```

Maybe we can see what's wrong with the set up.

---

### Post by lakamsani on 2007-03-13
> **bulldog said:**
> Can you post the output of ```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
```

Maybe we can see what's wrong with the set up.

Thanks for your suggestion. I managed to figue this out by some trial and error. This box now has XP running on one of the partitions and Linux Mint Bianca running on another on the same 120GB SATA drive.  This is a Dell Dimension 8300 box. Following are the issues and workarounds.

1. When it goes into this boot loop, if I power off the machine, leave it alone for a minute or so and then power it on then it boots fine via the Grub menu (into either Windows or into Linux Mint).

2. The Linux Mint CD that I used for 2 successful laptop installs developed some defects which got in the way of  installation in this Dell desktop. This is why I tried Ubuntu server which then led me to the boot loop issue.

The boot loop issue was observed following a successful install of  Ubuntu Server 6.10, Linux Mint as well as pclos 2007. So it probably has to do with the BIOS on the Dell box.  In the end I decided to keep Mint as I developed some familiarity with it as my Windows replacement.
For dual boot Windows first and then Linux next install seems to work well (this is probably a well tested order and common knowledge but I 'm new to this).

---

