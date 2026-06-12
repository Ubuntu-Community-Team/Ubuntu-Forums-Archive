---
title: "Gutsy deleted my logical volumes!!!!!"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by jaywhy13 on 2007-10-16
I just dist-upgraded to Gutsy... Now when I reboot, my logical drives are all gone. They were under /dev/mapper/. My swap and home directory were logical drives. The only thing under /dev/mapper is control. Wot the hell is going on here? Please tell me I'm doing summin wrong... I REALLY DON'T WANT TO BLEEV that my home directory is gone!!!!

---

### Post by frodon on 2007-10-16
Check the output of "sudo fdisk -l" to see if your partitions are still there, they should be.

Then check your fstab file, if you are using /dev/... path to mount your partitions and not UUID then this surely why you parition are not mounted as /dev/... path might change but not UUID.

---

### Post by jimbo99 on 2007-10-16
UUID is cryptic and cumbersome making absolutely no sense to most people.  So, most people don't know what it means nor how to decipher it nor how to re-implement it.  Probably not a realistic thing to turn Linux into another clone of the windows registry farce.  Just a thought.

---

### Post by jaywhy13 on 2007-10-16
I get everything up to here:
> **frodon said:**
> Then check your fstab file, if you are using /dev/... path to mount your partitions and not UUID then this surely why you parition are not mounted as /dev/... path might change but not UUID.

In /etc/fstab it says that /dev/mapper/lv0-home is to be mounted at /home, and similarly /dev/mapper/lv1-swap to be mounted as /swap. The only thing left under the directory /dev/mapper is "control". Those 2 devices no longer exist. What are u saying I should do re the UUID and path changing

---

### Post by frodon on 2007-10-17
To all those who changed back UUID to logical path please don't blame UUID, if you have logical path in your fstab it is because you put them here. It has been said many times that this would cause problems to use logical path, anyway if you never modified you fstab you should already have UUID so those who nerver edited their fstab can ignore this.

jaywhy13, ok so all you have to do to solve your issue is to put UUID instead of your logical paths and you wil be done forever with this.
Boot your system or a live cd then open a terminal use the "ls -l /dev/disk/by-uuid/" or "blkid", it will list all your system partitions giving you the coresponding uuid for each. Then recognise your home, swap and other partitions and edit your fstab to use uuid, here an example of fstab line with uuid :
```
UUID=f0343b8c-1226-4f66-8b41-6a5c02c028dd /media/sos ext3 defaults 0 1
```Once you have done this either reboot or run a "sudo mount -a" if you are already running your ubuntu insttall.

---

### Post by jaywhy13 on 2007-10-17
There's only one problem with that. My drive is NOT listed under /dev/disk/by-uuid/. My home dir and swap directory aren't there. And I'll also throw in .... I NEVER changed fstab manually... Nope... Whatever's in there now is wot the previous install put in it.

---

### Post by jaywhy13 on 2007-10-17
All the other are listed though

---

### Post by louieb on 2007-10-17
> **frodon said:**
> To all those who changed back UUID to logical path please don't blame UUID,

Except  for some bugs that cause the uuid of a partition to change. I have had it happen in both Feisty and Gutsy (never used Edgy so don't know about that one). I'd agree. In one case I installed Gutsy in an existing partition on a pc that had Feisty installed on another partition. For some reason the uuid of my swap and the Gutsy partition changed.  That gave Feisty fits when I rebooted it. Had to correct the uuid of swap and the Gutsy partitions in Feisty's /etc/fstab. 

UUID  of swap also changed on my laptop. Could not trace the cause to anything in particular.  Just know I had to correct the uuid in a couple of places  [http://ubuntuforums.org/showthread.php?t=528306&highlight=hibernate+swap](http://ubuntuforums.org/showthread.php?t=528306&highlight=hibernate+swap)
       
Its a good idea in theory, but in practice using the UUID does lead to problems.

---

### Post by frodon on 2007-10-18
> **jaywhy13 said:**
> There's only one problem with that. My drive is NOT listed under /dev/disk/by-uuid/. My home dir and swap directory aren't there. And I'll also throw in .... I NEVER changed fstab manually... Nope... Whatever's in there now is wot the previous install put in it.That's why i asked you in my first post to do a "sudo fdisk -l" to check that all your drive are recognised.
So please run this command to check if your drive is recognised or not.

@louieb, this is a particular case (will never happen for most of us) as uuid is not supposed to change, all software has bug so as long as you can workaround them it is not an issue. However it is not because you had a bug that less than 1% of the persons have than the system is not good, that just mean that you're unlucky and that the system is not perfect.

---

### Post by jougs on 2007-10-18
I have a somehow similar problem. However, nothing has been deleted, the new kernel in Gutsy (2.6.22) is merely unable to read the devices somehow. Booting the old kernel (2.6.20) reveals that everything is where it should be. My /var/log/syslog contains a line like
```
Oct 18 23:52:34 localhost mountd[5899]: Caught signal 15, un-registering and exiting.

```
for every time I boot the new kernel. The old one works nicely. I will investigate further and eventually file a bug...

Greetings,
Jougs!

---

### Post by jaywhy13 on 2007-10-18
Here's the output of fdisk -l


Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7aac0fd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2639    21197736    7  HPFS/NTFS
/dev/sda2            2640        4463    14651280   83  Linux
/dev/sda3            4464        6165    13671315    5  Extended
/dev/sda4            6166        9546    27157882+  83  Linux
/dev/sda5            4464        6165    13671283+  8e  Linux LVM

Disk /dev/dm-0: 13.5 GB, 13526630400 bytes
255 heads, 63 sectors/track, 1644 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/dm-1: 469 MB, 469762048 bytes
255 heads, 63 sectors/track, 57 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table
Disk /dev/dm-1 doesn't contain a valid partition table

---

### Post by joe.turion64x2 on 2007-10-18
> **jaywhy13 said:**
> Here's the output of fdisk -l


Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7aac0fd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2639    21197736    7  HPFS/NTFS
/dev/sda2            2640        4463    14651280   83  Linux
/dev/sda3            4464        6165    13671315    5  Extended
/dev/sda4            6166        9546    27157882+  83  Linux
/dev/sda5            4464        6165    13671283+  8e  Linux LVM

Disk /dev/dm-0: 13.5 GB, 13526630400 bytes
255 heads, 63 sectors/track, 1644 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/dm-1: 469 MB, 469762048 bytes
255 heads, 63 sectors/track, 57 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table
Disk /dev/dm-1 doesn't contain a valid partition table
Seeing three Linux partitions there suggests the data is still there, though not recognized somehow. Have you tried to run Gparted: sudo gparted (you'll probably have to install it first)?

This Gparted will allow you to see your hard disk partitioning scheme and from there you might be able to 'mount' the partitions and retrieve your data. However, if it is true that two of your partitions don't have a valid partition table then it is possible that they won't even appear in Gparted.

---

### Post by jaywhy13 on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: Here is the file onw [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Turns out... using a lower kernel... my partition is still there... everything in tact. I'm using that login now. How do I rectify for the new kernel tho?

---

### Post by obaudys on 2007-10-19
Perhaps there is some sort of LVM version mismatch and you need to update the volume.  I  have my home partition on an LVM logical volume spread across three physical partitions, so if and when I come across this during my upgrade (in a few hours time) I will post a solution.

---

### Post by frodon on 2007-10-19
jaywhy13, do you recognise your partitions in the fdisk -l output ?

Are the partitions you miss under /dev/dm-1 ?

---

### Post by jougs on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				After more investigation I found that dmesg contained heaps of messages like
```
device-mapper: table: 254:0: linear: dm-linear: Device lookup failed
```
A solution that worked for me and brought back all my devices in kernel 2.6.20 is
described in the bug report linked above.

---

### Post by Creap on 2007-10-19
> **jougs said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				After more investigation I found that dmesg contained heaps of messages like
```
device-mapper: table: 254:0: linear: dm-linear: Device lookup failed
```
A solution that worked for me and brought back all my devices in kernel 2.6.20 is
described in the bug report linked above.
This solution, ```
aptitude remove evms
```, solved my problems as well. I got quite sweaty for a while when my home dir was not mounted, nothing worked :)

---

### Post by L0rd_D4rk on 2007-10-20
Thank you very much!!!

after deleting evms I was able to boot with the new kernel and get the nvidia acceleration back!

---

