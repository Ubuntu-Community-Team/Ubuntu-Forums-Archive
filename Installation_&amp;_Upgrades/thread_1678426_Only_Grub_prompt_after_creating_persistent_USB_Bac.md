---
title: "Only Grub prompt after creating persistent USB Backtrack 4 r2"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by PeterAlbers on 2011-01-30
Hi,
 
I have the following problem. I tried to make a persistent USB Backtrack 4 r2. 
 
I followed the steps according to the instructions and did not noticed any errors.
 
fdisk /dev/sdb
 
Command (m for help): d
Partition number (1-4): 1
 
Command (m for help): n
Command action
e   extended
p   primary partition (1-4)
p
 
Partition number (1-4): 1
First cylinder (1-522, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-522, default 522): +5120M
 
Command (m for help): n
Command action
e   extended
p   primary partition (1-4)
p
 
Partition number (1-4): 2
First cylinder (193-522, default 193): 
Using default value 193
Last cylinder, +cylinders or +size{K,M,G} (193-522, default 522): 
Using default value 522
 
Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): b
Changed system type of partition 1 to b (W95 FAT32)
 
Command (m for help): t 
Partition number (1-4): 2
Hex code (type L to list codes): 83
 
Command (m for help): a
Partition number (1-4): 1
 
Command (m for help): w
 
mkfs.vfat /dev/sdb1
mkfs.ext3 -b 4096 -L casper-rw /dev/sdb2mkdir /mnt/sdb1
 
mount /dev/sdb1 /mnt/sdb1cd /mnt/sdb1

rsync -r /media/BT4/* .
 
grub-install --no-floppy --root-directory=/mnt/sdb1 /dev/sdb

My problem is that when i boot from the USB i only get the Grub prompt?
 
I can boot from USB because when i use Unetbootin everything works fine. Although it'snot persistent in that situation.
 
I seachered the web but i can't find the solution. I have run a script which i ran into on Sourceforge.net. 
 
The results are in the attachement. But unfortunately i am real Newbie on linux so...I hope someone can help me out and can explain what i did wrong and how i can solve this :-)
 
Thanks!

---

### Post by oldfred on 2011-01-30
You installed grub2 to the MBR of sdb but BT uses grub legacy.

old 2006 instructions to reinstall grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdb1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
root (hd1,0)
setup (hd1)

Old grub counts partitions different so sdb1 is hd(1,0).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You may also need to remove this as it is part of grub2.
boot/grub/core.img

---

### Post by PeterAlbers on 2011-01-31
Hi,
 
First off all thanks for the quick reply. Unfortunately i was not succesfull. Offcourse this got all to do with my unsufficient knowledge of Linux :-)
 
This is what i tried so far:
 
I booted wit the Backtrack 4 r2 live cd
Startx
Plugged in my USB 
 
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdb1 /mnt/root

Then i got the error: Mount: special device /dev/sdb1 does not exists
 
So i ran:
 
Sudo dmesg | egrep hd.\|sd.
 
The 8gb USB is detected on: sda: Sda1 sda2
 
The two partitions are correct. The first is 5gb fat32 with the backtrack data on it. The second is the 3gb ext3 partition for persistent usage.
 
So i tried:
 
sudo mount -t ext3 /dev/sda1 /mnt/root
 
Then i get the message:
 
Mount: wrong fs type, bad option, bad superblock on /dev/sda1
 
And this is where my mission ends so far...... :-)
 
I hope you can help me? Lol. I am trying to solve this for 3 days. Learning a lot through trial and error..... but still a lack of knowledge :-)
 
Cheers.

---

### Post by oldfred on 2011-01-31
It is not ext3, I missed that. Since it is FAT you have to use vfat to mount it. I have never seen grub reinstalled with a vfat partition, but I have installed grub2 to my flash drive that was vfat, so it should work.

Use this to confirm which drive the flash gets mounted as. Some systems to promote the flash drive to sda like yours.
  
sudo fdisk-l 
sudo mount -t vfat /dev/sdb1 /mnt/root

---

### Post by PeterAlbers on 2011-02-01
Hi,
 
Thanks again.
 
This time i got a litte bit further :-)
 
Because /mnt/root/proc and /mnt/root/dev did not exists i created them with mkdir. Just like the /mnt/root.
 
I then could:
 
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
 
But after that:
 
sudo chroot /mnt/root /bin/bash 
 
the following error occured:
 
Chroot: Cannot run command 'bin/bash' : No such file or directory.
 
In the /bin directory there is a executable bash file. ???
 
I wonder if it's not a better option to follow: [http://www.backtrack-linux.org/wiki/index.php/Persistent_USB](http://www.backtrack-linux.org/wiki/index.php/Persistent_USB) these instructions, which i did in the first place, untill the 
[COLOR=#339966]grub-install --no-floppy --root-directory=/mnt/sdb1 /dev/sdb[/COLOR]Change these with something else to get grub legacy installed? I don't mind doing this all over again. It's not that much work. 
 
As you noticed, as long as the instructions works, i can handle. I am in deep trouble if they don't. So your help is very much appreciated. 
 
Thanks again.

---

### Post by oldfred on 2011-02-01
I would think you should be able to rerun these command.
[COLOR=#339966]mkdir /mnt/sdb1[/COLOR]
[COLOR=#339966]mount /dev/sdb1 /mnt/sdb1
[/COLOR][COLOR=#339966]grub-install --no-floppy --root-directory=/mnt/sdb1 /dev/sdb[/COLOR][FONT=Verdana]

I do not know why that did not work the first time, but if you manually typed even a space missing can cause issues.

I have become a fan of grub2 and use it for everything. I can just install grub2 to a drive and manually create a grub.cfg.

[/FONT][COLOR=#339966]grub-install --no-floppy --root-directory=/mnt/sdb1 /dev/sdb[/COLOR][FONT=Verdana]1
[/FONT][FONT=Verdana]You can install BT's grub legacy to the partition and chainboot to it. One other user who installed to his hard drive recently did that without any problem.

If the reinstall grub does not work, post this with the flash drive installed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

[/FONT]

---

### Post by PeterAlbers on 2011-02-02
YES!!!!
 
:p
 
It worked. Finally :-)
 
Now i do have a working USB persisent Backtrack r2 image. He he.
 
To be honoust, now the difficulty realy starts. But nevertheless... i can go on now.
 
Thanks a lot!!
 
Cheers,
Peter

---

