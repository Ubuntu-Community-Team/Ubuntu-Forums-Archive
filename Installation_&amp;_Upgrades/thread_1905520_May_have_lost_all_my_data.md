---
title: "May have lost all my data"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Alphamonkey on 2012-01-07
Hi, I was going to install fedora on the partition of my hard drive that windows 7 was on but something went wrong. I backed up the most important files before doing anything just in case something went wrong, good thing I guess. Anyways I was using disk utility to erase my windows partition prior to installing fedora 15. Well I got an error while doing it. Not exactly sure what the error said. When I restarted my computer it would no longer boot into ubuntu or windows and grub wont show up either. I tried booting it with the Live USB to see if I could retrieve the rest of my files but the hard drive no longer shows up.     
root@root:/etc# cat mtab aufs / aufs rw 0 0 none /proc proc rw,noexec,nosuid,nodev 0 0 none /sys sysfs rw,noexec,nosuid,nodev 0 0 none /dev devtmpfs rw,mode=0755 0 0 none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0 /dev/sdb1 /cdrom vfat ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0 /dev/loop0 /rofs squashfs ro,noatime 0 0 none /sys/fs/fuse/connections fusectl rw 0 0 none /sys/kernel/debug debugfs rw 0 0 none /sys/kernel/security securityfs rw 0 0 none /dev/shm tmpfs rw,nosuid,nodev 0 0 tmpfs /tmp tmpfs rw,nosuid,nodev 0 0 none /var/run tmpfs rw,nosuid,mode=0755 0 0 none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0 none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0     
 root@root:/etc# cat fstab aufs / aufs rw 0 0 tmpfs /tmp tmpfs nosuid,nodev 0 0    
  theres the fstab and mtab I can't see my hard drive anywhere except in the bios. If anyone has any suggestions please let me know. Thanks.

---

### Post by darkod on 2012-01-07
You can't see the disk in Gparted or with:
sudo fdisk -l

Another option to recover partitions (if they are missing) is testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Alphamonkey on 2012-01-07
did fdisk and got  Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x00000000  Disk /dev/sda doesn't contain a valid partition table  Disk /dev/sdb: 4051 MB, 4051697664 bytes 125 heads, 62 sectors/track, 1021 cylinders Units = cylinders of 7750 * 512 = 3968000 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x00000000     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *           1        1021     3956344    c  W95 FAT32 (LBA) root@root:/etc# mount /dev/sda mount: can't find /dev/sda in /etc/fstab or /etc/mtab   going to install gparted and see what i can do

---

### Post by darkod on 2012-01-07
Please post results in code /code tags inside [ ] so it comes out better.

OK, the good thing is the disk is recognized, but not any partitions on it. Gparted can't help you.

Try testdisk, it should do the job.

---

### Post by Alphamonkey on 2012-01-07
Ok, so I have installed testdisk. First I did it by downloading the .tar and extracting it but I couldn't figure out how to execute it. I read on the website for testdisk that you do sudo "pathname"/linux/testdisk_static and that didn't work for me. I figured maybe there was something I was missing so I went to google and did some searching. Seems like everyone was recommending to download it using apt-get so I did. sudo apt-get testdisk. After downloading it every site I looked on said you could execute it using sudo testdisk. Well I tried that and am unable to execute it. It says that I need to install it however if I type apt-get install testdisk again it says the package is already install. Seems weird. I am going to keep trying to figure it out on my own but open to suggestions.

---

### Post by darkod on 2012-01-07
I just tested and sudo path/testdisk_static worked for me.

Be careful to specify the full path. For example, if you downloaded and extracted in Downloads it might have created a folder named testdisk-ver-number.

So the full path to execute would be:
sudo ~/Downloads/testdisk*/linux/testdisk_static

Also note that in live mode the downloads are not kept so if you rebooted then you need to download again.

The same applies for installing testdisk. It's not kept after reboot in live mode.

I guess the download method is better because you can double check where you have the file and what path to enter exactly. Also note that in linux capital letters are not the same as small letters, like in windows. In linux the path ~/downloads is not the same as ~/Downloads. Type exactly as you see.

---

### Post by d3v1150m471c on 2012-01-07
i can't really read your post so i'm gonna take a blind stab at suggesting foremost. it does a decent job at recovering most filetypes.

---

### Post by Alphamonkey on 2012-01-08
Well I guess there was a problem with the live boot media I was using getting testdisk to work. I used my other flash drive that had fedora 15 on it to do testdisk and it downloaded and worked (sort of). I used it the first time and "restored" the partitions, however there was a problem. When I booted up again it didn't go through grub and tried to go into windows but windows wasn't recognizing the partition correctly though it did actually see it this time. Well a couple more tries and I got annoyed because every time I had to restart to let the changes of testdisk take affect and found that it didn't work properly I had to redownload and install testdisk. This got annoying real fast because I am in a hotel in mexico with super slow internet. This lead me to just reinstall. I had backed up my most important stuff the rest I can get back eventually. Thanks everyone for the help.

---

