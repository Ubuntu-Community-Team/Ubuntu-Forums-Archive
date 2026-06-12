---
title: "Cannot boot new install of Ubuntu 12.04 LTS with new HDD"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by Zahrn on 2012-07-09
Hello!
 
I purchased a new hard drive, and I wanted to install Ubuntu on it. I was able to complete the installation, but when I try to boot with the new hard drive, all I get is a black screen.
 
I used the Boot-Repair, and here is the url:
 
[http://paste.ubuntu.com/1083787](http://paste.ubuntu.com/1083787)
 
My Motherboard is five years old. I have an ASUS P5WDG2-WS PRO, and it was configured to use RAID0 with Windows Vista. When I installed the new hard drive,
I switched in the BIOS from RAID -> STANDARD IDE so I could see my new hard drive.
 
I am not worried about the RAID0 array. I am looking to make this machine linux only.
 
I have a feeling I did something wrong with the hard drive configuration in the BIOS which is why I am having issues with booting the new hard drive.
 
Thanks!
 
EDIT:
 
I found a solution to my issue of booting.  In the BIOS, I had to disable the onboard raid controller.  Once I did that, I was able to boot into ubuntu.
 
I have a new issue now.  Ubuntu is painfully slow.  I will mark this thread as solved.
 
Thanks for the help!

EDIT2:

I fixed the slowness.  It was due to nvidia drives with unity 3d.  I switched to unity 2d, and the slowness went away.

---

### Post by oldfred on 2012-07-09
Was drive ever part of the RAID?

It used to be that you could not install to a RAID drive as meta-data was still on the drive that gparted or the installer saw and then would not proceed as it was RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

I do not see anything wrong with boot info script results. Some have had issues with large drives but that solution was a smaller / or separate /boot at the beginning of the drive which you already have.

---

### Post by Zahrn on 2012-07-10
No; the new hard drive was never part of the raid.

Reviewing your first thread, 

ubuntu@ubuntu:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="549e1c40-94ab-46b1-9e0a-1c201a13e463" TYPE="ext4" 
/dev/sda5: UUID="b64f2440-fa1f-42d3-b174-e37ce515eb24" TYPE="ext4" 
/dev/sda6: UUID="47314eb0-7f49-4e47-bdc2-df7513ce2e86" TYPE="ext4" 
/dev/sda7: UUID="9eac62aa-1047-43e7-81f0-9faf48307c55" TYPE="swap" 
/dev/sdb1: LABEL="NBRT" UUID="CE29-02ED" TYPE="vfat" 


Reviewing your second thread, I didn't see anything that would point to the drive set as raid.

ubuntu@ubuntu:~$ cat file.txt | grep ID_FS_TYPE
E: ID_FS_TYPE=vfat
E: ID_FS_TYPE=ext4
E: ID_FS_TYPE=ext4
E: ID_FS_TYPE=ext4
E: ID_FS_TYPE=swap
E: ID_FS_TYPE=squashfs

With my first attempt to install ubuntu, I let the installation do the partitioning.  It wouldn't boot after installation - same problem I have now.  I used the boot-repair program, and it suggested that I make a /boot partition, so I started from scratch, and I manually partitioned /boot, root, /home, and swap during installation.

---

### Post by YannBuntu on 2012-07-10
> **Zahrn said:**
> I found a solution to my issue of booting.  In the BIOS, I had to disable the onboard raid controller.  Once I did that, I was able to boot into ubuntu.

Good job, and thanks for the feedback. Please could you indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") so that we can see exactly what changed?

---

### Post by oldfred on 2012-07-10
The RAID meta data is not shown in the normal file system as the RAID works differently. You have to use dmraid to see if it is there.

---

