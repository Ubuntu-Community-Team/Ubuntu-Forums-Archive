---
title: "Dualboot Vista Raid0 and ubuntu on seperate drive"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by taco-man on 2008-05-08
I am trying to figure out how it is possible for me to dual boot vista and ubuntu.

Currently i have vista x64 installed on a raid0 set using the motherboards built in raid chipset (one of the nvidia nforce raid controllers.)

I installed ubuntu to its own seperate drive that is NOT a raid array, its just a single ide drive. The installation went fine all the way through however when the computer restarts it simply starts windows up. Grub never comes up and asks what os to use or anything. Also if i change the boot order so that the disk with ubuntu on it has first boot priority i get error loading os message (no bootloader comes up at all).

how do i make it so that i can boot in to windows or ubuntu? i dont care if i use grub or windows bootloader as long as it works so that i can use either OS. Currently i have no way of booting into the ubuntu install.

Any help would be great thanks!

---

### Post by garyedwardjohnston on 2008-05-09
Your first problem is that they are on different drives.

BIOS can only read one as the first boot device and if there is only one then it will boot to that OS.

Not sure why Ubuntu isnt booting though.  If what you said is true and installation went fine, if first boot device is IDE drive with Ubuntu on it it should boot fine.  Strange.

I think you should install them both on the same drive if you are set on dual boot.  I prefer seamless integration through Virtualbox myself.  Dual boot means choosing, VM means both at the same time.

---

### Post by taco-man on 2008-05-09
based on the advice of having them on the same disk drive i went ahead and used dmraid and installed linux on a seperate partition of my main raid 0 array following this guide [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644) but i cant get grub to install. 

after i chroot into the new install on the raid drive from the live cd i installed dmraid and grub.

i load grub and type the following

```
grub> device (hd0) /dev/mapper/nvidia_abagdjba
device (hd0) /dev/mapper/nvidia_abagdjba
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```


**Possibly useful information below:**

here is the output from dmraid -r i case it is helpful
```
root@ubuntu:/# dmraid -r
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sde: nvidia, "nvidia_abagdjba", stripe, ok, 781422766 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_abagdjba", stripe, ok, 781422766 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_abagdjba", stripe, ok, 781422766 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_cegddbjc", mirror, broken, 390721966 sectors, data@ 0
/dev/sda: nvidia, "nvidia_gbibfhee", mirror, broken, 390721966 sectors, data@ 0

```
nvidia_cegddbjc and gbibfhee are from a raid 1 array that is currently degraded, i am aware of the fact and will rebuild it later. I installed onto the "nvidia_abagdjba" raid 0 array of 3 400gb disks.

here is the output from fdisk showing the partitions of /dev/mapper/nvidia_abagdjba

```
root@ubuntu:/# fdisk /dev/mapper/nvidia_abagdjba

Command (m for help): p

Disk /dev/mapper/nvidia_abagdjba: 1200.2 GB, 1200265297920 bytes
255 heads, 63 sectors/track, 145923 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6591312

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_abagdjba1   *           1      143375  1151651836    7  HPFS/NTFS
/dev/mapper/nvidia_abagdjba2          143376      143630     2048287+  82  Linux swap / Solaris
/dev/mapper/nvidia_abagdjba3          143631      145923    18418522+  83  Linux

```

if there is other information i could provide please let me know, thanks.

---

### Post by Em-Buntu on 2008-05-09
You can do as you initially do and have Windows on one hard drive and Ubuntu on a second. The BIOS is irrelent to which drive you are booting.

My system has Windows XP-64 on HD0 and Ubuntu on HD1.
Grub allows you to tell the system which you'd like to boot.

If you already have Windows installed on HD0, just boot from the Ubuntu Live CD and in install select manual partitioning and check the option for installing on HD1.
Allow grub to install on HD0 and it will merge your Windows install with Ubuntu in grub menu.lst.

I much prefer this arrangement to installing on the same disk for reliability reasons. I.E. if Windows or Ubuntu should crash, it doesn't effect the other system.

---

### Post by taco-man on 2008-05-09
how would i get grub working though? i think this is my main problem. I have no issues getting Ubuntu to install, i am unable to get grub to come up at all.

---

### Post by Em-Buntu on 2008-05-09
I assume your windows install is on teh 1st HD?
This would be HD0.
When you install Ubuntu onto drive2 (hd1) select the advanced tab in the partion menu and it should say, "load grub in HD0". If not click the arrow and select HD0 from the list options. This will load grub on the same hd as your windows installation. Grub will/should detect your windows boot file and list your windows installation in menu.lst. 
When you reboot, grub should start and allow you to boot either Ubuntu or Windows.
Boom! Bob's your uncle. :guitar:

---

### Post by taco-man on 2008-05-09
I figured out why it would not work with installing to my main raid array that had vista on it. Grub cant read far enough in the disk to reach the partition i had installed ubuntu on. this was most likely due to the fact that the ubuntu partition was more than 1 terabyte in on the array. i discovered this when getting the geometry on the drive that vista is on **from within grub.** Grub could only read the first partition that had windows on it, the swap and ubuntu partitions returned "Error 18: Selected cylinder exceeds maximum supported by BIOS." Im assuming this could be solved by making a super small /boot partition at the beginning of the raid array.

I decided to go back to trying to get it working with ubuntu on a seperate drive from the raid array that had vista on it. i finally managed to get it working so i am going to describe what i did and the problems i ran into for anyone else trying to do this and perhaps there might be something useful in here. I am quite a noob when it comes to linux though so be careful with any of this i dont gurantee this wont mess up your system or whatever.

thanks to everyone who helped me.

in my bios i set my empty drive i wanted to install ubuntu on to as the primary boot hard drive. then i went ahead and installed ubuntu on it using the guided mode where it just uses the hard drive. after you choose what drive/partition settins at some point there should be an advanced button you can click and check to make sure that grub is installing the bootloader onto the same drive as the one you are installing linux on.

grub should start installing and finish and boot up. the first time i tried this windows just started up after the install, it was because i forgot to have grub install to the drive i was installing linux on.

at this point ubuntu should boot up and your windows wont boot up anymore.

i installed dmraid so that it can see my raid array that has vista on it.
see this guide for more info about installing dmraid [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)

since i needed grub to see the raid array with my windows installation on it and not try and just mess with one of the disks in the array i edited the device.map file for grub located at /boot/grub/device.map 
Its possible this file doesnt exist, if so you can simply create it.
**if someone else is using this you will need to change the contents of this file to fit your computer**
```
(hd0) /dev/sdf
(hd1) /dev/mapper/nvidia_abagdjba
```

the drive i had ubuntu installed on was /dev/sdf (sda-sde drives were drives that were part of raid sets). This is the drive i used for booting.

the name of my raid set with vista on it was nvidia_abagdjba which i found from the information given by ```
sudo dmraid -r
```again see the previously linked guide for more info about dmraid.

once that is done launch grub and tell it to use your device map you just made by running
```
sudo grub --device-map /boot/grub/device.map
```

make sure you re-set up grub after setting up device.map 
Grub doesn't use device.map when you are booting it just uses it for grubs console that you run you have to re-set it up from within grub after you make any changes to device.map by loading grub with the device.map file and then doing the whole root (hdx,x) and setup (hdx) process.

at this point its just like setting up grub for any normal 2 hard drives. hopefully this info might help someone in the same situation i was in.

**THANK YOU to everyone who help me/offered advice**

---

