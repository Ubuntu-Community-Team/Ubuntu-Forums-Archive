---
title: "Installing GRUB2 on RAID root"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2010-10-26
I'm trying to install GRUB2 on root partition under RAID 5.  I tried using the alternate CD, but installation failed.  Now I'm trying under the live CD and grub-install ... but I'm being told it can't find the device even though /dev/sda2 (root partition) and /dev/sda are mounted.

I have 4 discs, each with a swap partition (/dev/sdX1) and a root partition (/dev/sdX2).

---

### Post by oldfred on 2010-10-26
I do not know raid but another with hardware raid.

Hardware Raid boot
[http://ubuntuforums.org/showthread.php?t=1564502](http://ubuntuforums.org/showthread.php?t=1564502)

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by psusi on 2010-10-26
You should have 4 disks, only one of which might have bogus partitions on it.  You need to ignore them all and use the raid device in /dev/mapper.

---

### Post by ronparent on 2010-10-26
I don't know for sure if it applies to a raid 5, but, when booting to a raid the boot loader has to be on the raid root. This is found usually as the first symbolic link listed after control in /dev/mapper. It can be fixed from a live cd following the instruction here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

The simplest way takes the form as follows from a terminal in a live cd session.

First mount the drive you have installed to:
> sudo mount /dev/mapper/<yourRAIDPartition> /mnt
Then perform the grub and grub boot loader install with:
> sudo grub-install --root-directory=/mnt/ /dev/mapper/<TheRAIDRoot>

As long as a fakeraid raid5 is bootable on the raid this should work. Post how you make out here.

---

### Post by BLaZuRE on 2010-10-26
Well, I'm getting a message saying that "/dev/mapper/control is not a block device" when I attempt to mount it.  control is the only thing under /dev/mapper.  I used sudo mount /dev/mapper/control /mnt

I'm using Ubuntu's software raid.

---

### Post by ronparent on 2010-10-26
Afraid of that. OK guys, this a pure software raid. BLaZuRE needs advice from one or the software raid mavens. There may be a need to install grub to a non raid drive.

---

### Post by psusi on 2010-10-26
Ohh, if it's software raid then it will be something like /dev/md0.  What does cat /proc/mdstat show?

---

### Post by BLaZuRE on 2010-10-26
Well, cat /proc/mdstat shows nothing (no personalities, no devices unused).  I assumed that was because I'm on the Desktop live CD (I used the alternate CD to install/partition).  Though the disk utility shows there aren't enough components to start the RAID array ...

Yes, I've tried mdX ... though they don't appear under /dev/

By the way, thanks for the help you guys are givin out :guitar:

---

### Post by BLaZuRE on 2010-10-28
Okay, I've repartitioned and I now have a /boot partition on each drive at 100 MB, since I realized there was no way I would be able to boot with software RAID5.  I now have /boot as a RAID-1.  I still can't get GRUB on there and I still can't get any of my mdX to show up though all the sdXX showup.

---

### Post by ronparent on 2010-10-28
I'll let someone correct me. I believe that with a true linux software raid your MBR has to be on the drive that is set as boot in bios. In a grub install the target for the grub install is whatever raid partition your OS is installed to. So by the instruction I gave you before, The partition with the OS is mounted (you can ls /mnt after mounting to verify it) and the boot reference is your boot drive (probably sda). Good luck.

---

### Post by BLaZuRE on 2010-10-28
Okay, so I now have /boot on sda1 as my boot partition (NOT on RAID).
I have 3 other partitions now (sdb1, sdc1, sdd1) of equal size, recognized as RAID partitions, though not under any mdX.

Is it possible to now migrate my /boot partition into RAID-1 with the other 3 partitions?  Will the MBR also transfer over to the other 3 discs or does it not fall under /boot?

Would there be any problem in me creating 4 separate /boot partitions?

---

### Post by psusi on 2010-10-28
You should be able to install with just one partition used as the md device.  There is no need for a separate /boot partition with grub2.

---

### Post by BLaZuRE on 2010-11-01
Well, I'd like to have recovery be as seamless as possible, so being able to boot on any other drive in case the first drive with the /boot partition fails would be nice.

---

