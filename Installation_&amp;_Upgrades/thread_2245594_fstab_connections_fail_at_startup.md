---
title: "fstab connections fail at startup"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2014-09-24
This being my third clean install of Xubuntu 14.04 in the past week. Of the three major problems related to the OS, this is the first I need to resolve. Using **sudo blkid** and **fdisk -l** I got the drives' info and edited fstab. then created a **/media/ntsf ** folder (owned by root which I tried to change but couldn't). I tried defining the connections using the UUID or the device name and got the same result. fstab connects to a single read only file on each drive. In the current list below the connections are blocked, and I am using Gigolo which only connects manually. During boot, I also get a message about the swap drive is slow to load, but then, the message disappears. The swap is about 15GB. Xubuntu is installed on a 95 GB drive.
What am I doing wrong?

For the other two problems , I will create a separate posts. One is Nvidia + monitor and resolutions, and then, Menu Libre. I am also considering the possibility tha the three may be related. Unfortunately, there is no end to the installation problems with Xubuntu  14.04. I am trying to establish a stable environment for my work and have no succes so, I am forced constantly to revert to Windows.

```

[FONT=Courier New]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=9233d68b-a7e5-4151-9ffc-a47ae6e941ea /	ext4    errors=remount-ro 0       1
/dev/sda8 		none			swap 	errors=remount-ro 0       0

# /dev/sda1	UUID=01CEAE900888CDB0
# UUID=01CEAE900888CDB0		/media/ntsf		ntfs	auto	 0	0
# /dev/sda2	UUID=01CEAEBA8E379340
# UUID=01CEAEBA8E379340		/media/ntsf		ntfs	auto	 0	0
# /dev/sda5	UUID=01CEAF44EAC92210
# UUID=01CEAF44EAC92210		/media/ntsf		ntfs	auto	 0	0
# /dev/sda6	UUID=01CEAF4576EC6090
# UUID=01CEAF4576EC6090		/media/ntsf		ntfs	auto	 0	0
# /dev/sda7	UUID=01CEAF2435F58790
# UUID=01CEAF2435F58790		/media/ntsf		ntfs	auto	 0	0
#/dev/sdb1	UUID=01CFB9B75B5CB5F0
# UUID=01CFB9B75B5CB5F0		/media/ntsf		ntfs	auto	 0	0
# /dev/sdb5	UUID=01CFB9B765C189D0
# UUID=01CFB9B765C189D0		/media/ntsf		ntfs	auto	 0	0
[/FONT]
```

---

### Post by ajgreeny on 2014-09-24
I think the lines you need in fstab should be more like
```
UUID=x#x#x#x#x#x#x /media/ntfs    ntfs-3g        auto,user,rw 0 0
``` rather than the way you show them, but I admit I have no ntfs partitions to use to check this out.

PS:  Interesting typo in your mountpoints, or is that purposeful?  [FONT=Courier New]/media/ntsf[/FONT] ?
By the way, you should definitely continue to use the UUIDs of partitions, not device names such as /dev/sda1, as these latter can change depending on the order they are mounted, or when one or more are perhaps removed for whatever reason; UUIDs always remain the same until formatted.

---

### Post by ineuw on 2014-09-24
Thanks for the info, I will try it immediately. As for the folder name ity was done on pupose because I wasn't comfortable with the actual name, but will probably change it to something else.

---

### Post by ineuw on 2014-09-24
I resolved it by using the following steps. I was curious to see what happens when a single drive is mounted.
1. Unchecked all drives in Gigolo so they won't mount. 
2 Edited fstab and blocked all drives except one (sda7).
3 Rebooted and the drive was mounted properly on boot - checked the connection on the desktop and it was as it should be.
4 Next, using Thunar, I looked at the **/media/win** folder (a new name **not ntsf**) to where the drive sda7 was assigned, and I saw the problem immediately. It held every folder of the drive and there is a lot of them!
5 Created seven new folders in /media as . . . . **/media/sda1, /media/sda2, etc.** one for each drive as it was indicated by fdisk and blkid. 
6 Edited fstab and assigned each drive a folder and now everything is connected without Gigolo.

```

[FONT=Courier New]# / was on /dev/sda9 during installation
UUID=9233d68b-a7e5-4151-9ffc-a47ae6e941ea /	ext4    	errors=remount-ro 		0       1
/dev/sda8					none		swap 	errors=remount-ro	0       0
# /dev/sda1	UUID=01CEAE900888CDB0
UUID=01CEAE900888CDB0				/media/sda1	ntfs-3g	defaults,user,rw	0	0
# /dev/sda2	UUID=01CEAEBA8E379340
UUID=01CEAEBA8E379340				/media/sda2	ntfs-3g	defaults,user,rw	0	0
# /dev/sda5	UUID=01CEAF44EAC92210
UUID=01CEAF44EAC92210				/media/sda5	ntfs-3g	defaults,user,rw	0	0
# /dev/sda6	UUID=01CEAF4576EC6090
UUID=01CEAF4576EC6090				/media/sda6	ntfs-3g	defaults,user,rw	0	0
#  /dev/sda7	UUID=01CEAF2435F58790
UUID=01CEAF2435F58790				/media/sda7	ntfs-3g	defaults,user,rw	0	0
# /dev/sdb1	UUID=01CFB9B75B5CB5F0
UUID=01CFB9B75B5CB5F0				/media/sdb1	ntfs-3g	defaults,user,rw	0	0
# /dev/sdb5	UUID=01CFB9B765C189D0
UUID=01CFB9B765C189D0				/media/sdb5	ntfs-3g	defaults,user,rw	0	0[/FONT]

```

ajgreeny, thanks for your input. Now on to the next major problem: the video.

---

### Post by ajgreeny on 2014-09-25
Stupid of me not to even notice that you were trying to mount all those partitions on the one /media/ntsf folder.

Never-mind; I'm glad you figured it out yourself.

---

### Post by ineuw on 2014-09-25
> **ajgreeny said:**
> Stupid of me not to even notice that you were trying to mount all those partitions on the one /media/ntsf folder.
Please don't call yourself stupid. Previously in Xubuntu 12.04, I had two 80GB drives, split into 4 x 40GB partitions, and distinctly remember that they showed up in **/media** (no subfolders) as four drive icons. This is what  I expected. But now, I have 1x80 and 1x500GB drives, seven ntfs partitions and when I click on the subfolders of /media they contain the folders of the drive, and not icons. I also don't understand why Gigolo doesn't make permanent connections. These, and other such issues keep users from installing Linux as their OS. Just consider the time you invested on learning and setting up your system to your comfort.

---

