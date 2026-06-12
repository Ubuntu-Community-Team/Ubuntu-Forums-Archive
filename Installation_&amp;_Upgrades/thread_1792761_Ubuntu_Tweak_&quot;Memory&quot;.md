---
title: "Ubuntu Tweak &quot;Memory&quot;"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by EmmeVi on 2011-06-28
Hi! :)

I'm a newbie in Ubuntu World, so I have a lot of doubts...
Anyway my actual problem is to change my pictures, download and music folders, since my files are in another HDD partition; I can make it with Ubuntu Tweak, but at the first reboot folders are resetted. Which is the problem? Does this application conflicts with another one (as "compiz fusion icon")? :confused:

Please, help me! ):P

---

### Post by Frogs Hair on 2011-06-28
The Compiz fusion Icon : [http://wiki.compiz.org/CompizFusionIcon](http://wiki.compiz.org/CompizFusionIcon)

---

### Post by tekkidd on 2011-06-28
Hmmm. It looks like you are just trying to make a link from the partition folder to your home directory. In that case go to the terminal and type in: 
```
cd /media/<partition name>/
```
This will get you to the partition. Now assuming the folder you are trying to link is on the root of the partition enter this in the terminal: 
```
ln -s <folder> /home/<username>/
```

Another reason why it might not be working is because you dont "own" the partition. In that case: 
```
cd /media/
```
And 
```
sudo chown <username> <partition name>
```

Hope all of this wasnt too complicated. Email me if you need more help: [email]sonny@tekkidd.com[/email]

---

### Post by e79 on 2011-06-28
> **EmmeVi said:**
> Hi! :)

I'm a newbie in Ubuntu World, so I have a lot of doubts...
Anyway my actual problem is to change my pictures, download and music folders, since my files are in another HDD partition; I can make it with Ubuntu Tweak, but at the first reboot folders are resetted. Which is the problem? Does this application conflicts with another one (as "compiz fusion icon")? :confused:

Please, help me! ):P

At the reboot, try and open '**user-dirs.dirs**' file located in your home folder, using any Text Editor of your choice; are the paths defined in Ubuntu tweak still there ?

Make a copy first to make sure you can revert to it if anything changes that you don't like
```
cp ~/.config/user-dirs.dirs ~/.config/user-dirs.dirs_FRESH
```

Then open the file and try to change the paths
```
gedit ~/.config/user-dirs.dirs
```

Reboot your machine and see how it goes.

---

### Post by dFlyer on 2011-06-28
> **EmmeVi said:**
> Hi! :)

I'm a newbie in Ubuntu World, so I have a lot of doubts...
Anyway my actual problem is to change my pictures, download and music folders, since my files are in another HDD partition; I can make it with Ubuntu Tweak, but at the first reboot folders are resetted. Which is the problem? Does this application conflicts with another one (as "compiz fusion icon")? :confused:

Please, help me! ):P

Keep an open mind. Go slow and have fun, that is the only way to learn linux. When you have problems ask questions being as specific as possible about your problem, hardware and error messages. Remember Ubuntu is not windows and doesn't work like windows. Give linux time to grow on you and maybe you will discover that it's even easier than windows to use.

---

### Post by EmmeVi on 2011-06-29
> **dFlyer said:**
> Keep an open mind. Go slow and have fun, that is the only way to learn linux. When you have problems ask questions being as specific as possible about your problem, hardware and error messages. Remember Ubuntu is not windows and doesn't work like windows. Give linux time to grow on you and maybe you will discover that it's even easier than windows to use.

I totally agree with you!:p It's a month I started using Ubuntu and I understood that, if I want to make everything in a few moments, I can't until I become a real Ubuntuer! :D
And I'm sorry if my bad english make me appear like nervous or something similar...

However Tekkidd understood which is my problem (@e79: I tried that file, but I didn't find it...) but maybe I can't use very well the terminal...

Now I look at your suggestions and I'll say to you as soon as possible.

Thanks all :)

---

### Post by EmmeVi on 2011-06-30
> **e79 said:**
> Reboot your machine and see how it goes.
At the reboot that file returns as before my modifications... :confused:

---

### Post by oldos2er on 2011-06-30
If you're linking to partitions that aren't automounted at system start, that would explain why the links are broken. Can you tell us how your hard disk(s) are setup by running these commands and posting their output? ```
sudo fdisk -l

mount
```

---

### Post by EmmeVi on 2011-07-02
> **oldos2er said:**
> If you're linking to partitions that aren't automounted at system startYou're right, but I don't know how to make it... :lolflag:

> **oldos2er said:**
> Can you tell us how your hard disk(s) are setup by running these commands and posting their output?
Sure! Here we are:

```
Disco /dev/sda: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xb8498fee

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781    7  HPFS/NTFS
/dev/sda2              26        4487    35841015    7  HPFS/NTFS
/dev/sda3           30389       30402      105656    c  W95 FAT32 (LBA)
/dev/sda4            4488       30388   208049752    5  Esteso
/dev/sda5            4488        8949    35840983+  83  Linux
/dev/sda6            8950        9459     4096543+  82  Linux swap / Solaris
/dev/sda7           15834       30388   116913006    7  HPFS/NTFS
/dev/sda8            9460       15833    51199123+   7  HPFS/NTFS

Le voci nella tabella delle partizioni non sono nello stesso ordine del disco 
```

---

### Post by dino99 on 2011-07-02
set your nautilus preference to select the partition/folder where you want your data/download, that's all.

---

### Post by oldos2er on 2011-07-02
> **EmmeVi said:**
> You're right, but I don't know how to make it...

You need to edit your /etc/fstab file to add the partitions you want to automount.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Make a backup copy of your fstab first: ```
sudo cp /etc/fstab /etc/fstab.backup
```Open fstab in gedit: ```
gksu gedit /etc/fstab
``` and add a line 
```
/dev/sda1 /media/sda1 ntfs-3g defaults,user,locale=en_US.utf8 0 0
```You will need to create the mount point /media/sda1 if it doesn't exist. This is just an example, you can mount it wherever you wish. Of course you'll need to repeat the process if you want to mount your other NTFS partitions.

---

### Post by EmmeVi on 2011-07-06
What can I say? THANK YOU! :)

My problem is now solved, thank you all :D

---

### Post by oldos2er on 2011-07-06
You're welcome!

---

