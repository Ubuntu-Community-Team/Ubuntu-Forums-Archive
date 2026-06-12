---
title: "raid 1 software side."
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by choppyfireballs on 2012-05-11
I installed Ubuntu server on my computer with two 1TB hdd's running RAID1 software, sda1 and 2 and sdb 1 and 2 the ubuntu guide recommended that I pull one hdd after installing the os, well I came to find out that that destroyed my raid settings. i have tried doing mdadm --add and both sda1 and sdb1 are saying they're already in the md0 and cannot be readded and I have tried removing them though i do not remember what the error was i was trying to use -- incremental. how can i get the raid mirror back up and running.

---

### Post by darkod on 2012-05-11
Hold on, with both disks connected and without running any mdadm command, what does:
cat /proc/mdstat

show?

---

### Post by choppyfireballs on 2012-05-11
md1: active raid1 sda2[1]
         4104180 blocks super 1.2 [2/1] [_U]

md0: acitve raid 1 sda1[1]
         972654456 blocks super 1.2[2/1][_U]

i know that means taht a drive has "malfunctioned" but when i try to readd or remove the drive that is malfunctioned because i know that it is perfectly fine it won't let me.

BTW thank you for the quick reply

---

### Post by darkod on 2012-05-11
I am not raid expert (yet) but I can try until someone else jumps in.

This is the output with both disks present?

As you can see, the partitions from /dev/sdb are not specified as part of the raid devices. Only /dev/sda.

Can you try reassembling it with:
sudo mdadm --assemble --scan

That should scan for all partitions of type raid and assemble the correct devices. Lets see if it helps.

---

### Post by choppyfireballs on 2012-05-11
i ran the command sudo mdadm --assemble --scan 

this is the output mdadm :/dev/md/0 is already in use
mdadm /dev/md/1 is already in use


and yes both drives are plugged in and they are both brand new, i can unplug either and it will boot just fine also it's always booting in degraded mode, despite that I turned degraded mode off.

---

### Post by darkod on 2012-05-11
But after the first try to pull a disk out, did you lets it sync when you connected it back?

Or you connected disk2 back and immediately disconnected disk1? You have to give it time to sync. You can see this status with cat /proc/mdstat.

Somehow they have lost the connection between them, especially if both work when only disk.

EDIT PS: On another note, is there data on the array worth saving or you just want to know why this happened and learn? If everything fails, can you simply reinstall again?

---

### Post by choppyfireballs on 2012-05-11
There was nothing to sync i installed os and never made any changed and it's not sycing in /proc/mdstat to my knowledge. and both disks are plugged in. to my knowledge because i am not a raid expert either, but when you unplug a raid disk when running raid 1 doesn't it essentially destroy the raid.

---

### Post by darkod on 2012-05-11
Even if there is no much data to move, it does need to resync. I am asking because it will probably lose itself if you connect one disk and immediately disconnect the other one. It has happened to me with hardware raid. :)

It doesn't destroy the riad1 when one disk goes, but in your tests you must never unplug one disk to try, then plug it back and unplug the other immediately. Let it realize the first disk is back, and do it's thing. Only then unplug the second disk to see if it will continue working.

What do you have in your mdadm.conf, I think the path was:
cat /etc/mdadm/mdadm.conf

---

### Post by choppyfireballs on 2012-05-11
the onl yline in the config file is boot_degraded variable = false i dno't really remember what exactly it said and both disks are plugged in so  i left it for the weekend but i can remote in and check i plan on checking it tomorrow at noon and seeing what is going on the problem if i didn't make clear is that it's booting to the degraded or secondary drive so i'm assuming that it will sync and do it's thing on it;s own. based on what you're telling me

---

### Post by darkod on 2012-05-12
But if it's syncing, the /proc/mdstat would show that. From the one you posted earlier it is not even considering the partitions on /dev/sdb as part of the array any more, so there is nothing to sync.

And the mdadm.conf should look something like this:
[http://ubuntuforums.org/showpost.php?p=11811355&postcount=7](http://ubuntuforums.org/showpost.php?p=11811355&postcount=7)

Note that few differences might be possible. And you should have two md devices there.

---

### Post by choppyfireballs on 2012-05-14
Well that's why i jumped on the forums because I did not see it syncing and i was confused as to what md devices are reading this is what my mdadm.conf reads.

#ato create devices with Debian standard permissions
CREATE owner = root group=disk node=0660 auto=yes

#automatically tag new arrays as belonging to the local system 
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays 
ARRAY /dev/md/0 metadata=1.2 UUID=49a4eb6e:ca1bed6f:473a04f0:b579cdec name=Fileserv:0
ARRAY /dev/md1  metadata=1.2 UUID=0ecdde16:742ebe8c:d0701166:50b1f529 name=Fileserv:0

then just the auto create time.

---

### Post by darkod on 2012-05-14
Is it ARRAY /dev/md/0?

It should be /dev/md0.

But I am not sure that is the only problem. Double check if it's /dev/md0 and correct it if it isn't.

---

### Post by choppyfireballs on 2012-05-14
It is indeed array md/0

---

### Post by choppyfireballs on 2012-05-14
and I don't know how to change it to device /md0

---

### Post by choppyfireballs on 2012-05-14
also this was on the degraded drive i'm force booting into the main drive now to check it

---

### Post by darkod on 2012-05-14
> **choppyfireballs said:**
> and I don't know how to change it to device /md0

From live mode can't you simply open that partition, open the file, and edit it. Save and close. Try to boot from the hdd, not in live mode.

---

### Post by choppyfireballs on 2012-05-14
> **choppyfireballs said:**
> also this was on the degraded drive i'm force booting into the main drive now to check it


it is array md/0 on the main drive as well.

---

### Post by darkod on 2012-05-14
> **choppyfireballs said:**
> it is array md/0 on the main drive as well.

Hm, so maybe it was created like that although that's very strange.

---

### Post by choppyfireballs on 2012-05-14
i am booting to the hdd

---

### Post by darkod on 2012-05-14
With all the disks connected, what if you try to stop the arrays and assemble them again:
sudo mdadm --stop /dev/md0
sudo mdadm --stop /dev/md1

sudo mdadm --assemble --force /dev/md0 /dev/sd[ab]1
sudo mdadm --assemble --force /dev/md1 /dev/sd[ab]2

---

### Post by choppyfireballs on 2012-05-14
> **darkod said:**
> Hm, so maybe it was created like that although that's very strange.

I don't know all i know was that it was working then i pulled out the hdd1 and it's been booting into degraded mode since. also i tried removing sdb2 from the md/0 array it would not let me, it said it did not exist sdb2 rather.

---

### Post by darkod on 2012-05-14
Try working for a while from live mode. In most cases it will not allow you to touch system files while you are running it from hdd.

---

### Post by choppyfireballs on 2012-05-14
ok and by live i assume you mean like live cd

---

### Post by darkod on 2012-05-14
> **choppyfireballs said:**
> ok and by live i assume you mean like live cd

Yeah. And sorry, I forgot to mention, to manipulate mdadm from live mode you will need to install the package first because it's not on the cd:
sudo apt-get install mdadm

You need to do that after every reboot into live mode because it doesn't keep the changes.

After the package is present, you can manipulate arrays.

---

### Post by choppyfireballs on 2012-05-14
> **darkod said:**
> Yeah. And sorry, I forgot to mention, to manipulate mdadm from live mode you will need to install the package first because it's not on the cd:
sudo apt-get install mdadm

You need to do that after every reboot into live mode because it doesn't keep the changes.

After the package is present, you can manipulate arrays.


ok thanks ill poke at that for a while at least it's a direction now

---

### Post by darkod on 2012-05-14
Also it wouldn't hurt double checking that all partitions are still of linux raid type. You can do that with:
sudo fdisk -l

All four partition included in the array need to have Linux RAID type.

---

### Post by choppyfireballs on 2012-05-14
Ok so here's where I'm at in the live cd, I installed mdadm and opened up disk utility because mdadm command line was not seeing any raids. disk utility can see the raid array but is showing it as offline, when i try to turn it on it says "not enough components available to start the RAID array. If i boot back onto the hdd i can see that both raid arrays are up and that sdb1 & 2 are online health but not attached. when i try to attach it is says "error adding spare: mdadm exited with exit code 1:mdadm:/dev/sda2 reports being an active member for /dev/md1 but a --re--add fails.  if i go into boot order and I try to boot to sata0 which is disk 1 raid says to me on startup that there is one or more degraded drives and boots in degraded mode.

---

### Post by darkod on 2012-05-14
OK, hold on. You are trying too much at the same time. Lets take it slow.

Boot from the hdd, and first check if all partitions are linux raid type, as I already said:
sudo fdisk -l

Then, check the arrays:
cat /proc/mdstat

After that we will see what to do. We can consider disk /dev/sdb as failed and faulty, and act like we are replacing it with a new one.

---

### Post by choppyfireballs on 2012-05-14
> **darkod said:**
> OK, hold on. You are trying too much at the same time. Lets take it slow.

Boot from the hdd, and first check if all partitions are linux raid type, as I already said:
sudo fdisk -l

Then, check the arrays:
cat /proc/mdstat

After that we will see what to do. We can consider disk /dev/sdb as failed and faulty, and act like we are replacing it with a new one.

Ok I ran fdisk and for /dev/md0 & 1 it says that "/dev/md0 (or 1) doesn't contain a vlid partition table" everything else looks ok there. 

cat /proc/mdstat ouputs this

md1: active raid1 sdb2[1]
         4104180 blocks super 1.2 [2/1][_U]
md0: active raid1 sdb1 [1]
         972654456 blocks super 1.2 [2/1] [_U]

---

### Post by darkod on 2012-05-14
OK. It shows only /dev/sdb in /proc/mdstat but in this moment also /dev/sda is connected, right?

Lets try to add /dev/sda as a new disk after one failed. Also, not to confuse it with the previous raid data, lets zero the superblock.

sudo mdadm --zero-superblock /dev/sda1
sudo mdadm --zero-superblock /dev/sda2

Add sda1 to md0:
sudo mdadm --manage /dev/md0 --add /dev/sda1

Did it work (some message like re-added /dev/sda1) or it reported an error?
If it worked check /proc/mdstat again, does it show /dev/sda1 as member of md0 and syncing?

---

### Post by choppyfireballs on 2012-05-14
yes it worked it's currently syncing md0

---

### Post by choppyfireballs on 2012-05-14
> **choppyfireballs said:**
> yes it worked it's currently syncing md0

out of curiosity what did the --zero-superblock command do, format the superblocks then add the partition?

---

### Post by darkod on 2012-05-14
Because this is software raid, it needs to keep the raid data somewhere on the partition. If I've got it right, that's called the superblock.

Because these two partitions were used in an array earlier, you simply tell it "forget that info" and it acts as new partition added to your array.

Don't forget, you will need to do the same --add for /dev/sda2 also. But let the sync finish first.

---

### Post by choppyfireballs on 2012-05-14
> **darkod said:**
> Because this is software raid, it needs to keep the raid data somewhere on the partition. If I've got it right, that's called the superblock.

Because these two partitions were used in an array earlier, you simply tell it "forget that info" and it acts as new partition added to your array.

Don't forget, you will need to do the same --add for /dev/sda2 also. But let the sync finish first.


Yeah I assumed as much thank you for your help.

---

