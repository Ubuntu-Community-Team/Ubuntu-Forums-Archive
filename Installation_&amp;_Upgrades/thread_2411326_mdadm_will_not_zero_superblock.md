---
title: "mdadm will not zero superblock"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by fewjr on 2019-01-28
Hello all,
     Well I pulled my old Ubuntu Server out of the basement to set it up with a newer version f Ubuntu Server. I haven't had the server running since 12.x.x! I installed 18.04.1 LTS to the boot drive, (120GB). I have 3 WD red drives in raid5 originally. I wanted to change to raid10 mdadm style. So I umounted and stopped /dev/md0. Then I lsblk to see the raid members. I had sdb1, sbc1, sdd1. I then did mdadm --zero-superblock of each drive but sdb1 will not zero. I have already removed persistent references in /etc/fstab and commented out the array in mdadm.conf. Then I updated initramfs. 
     Everything was going good with the new install but I ran into this hiccup redoing my array. I'm not sure what to do at this point. Could someone please give me some guidance on this one? I have been trying to find the solution for a couple hours now. Thank you in advance.

---

### Post by fewjr on 2019-01-29
Well I was hoping to get a nibble by today. I still am not sure what to do yet. I was thinking that I shouldn't have continued with the steps I did until all 3 drives were zeroed. I thought I might reverse my steps to bring the original array back to active but I still have no idea why sdb1 will not zero.

---

### Post by wildmanne39 on 2019-01-30
Hopefully someone will stop in that can help, please only bump your thread once every twelve hours by posting the word bump only.

Thanks and good luck!

---

### Post by fewjr on 2019-01-31
Sorry about that...I sent that on a cell phone. I'm not sure how I did it twice.

---

### Post by darkod on 2019-02-01
First question: How do you plan to use raid10 with only 3 data disks (I'm not counting the OS disk)? Have I missed something?

Also, please post the output you get when trying to zero sdb1:
```
sudo mdadm -v --zero-superblock /dev/sdb1
```

@Admin, can someone please move this to Server subforum? I think it's better fit.

---

### Post by fewjr on 2019-02-02
Hello, 
     Thank you so much for responding. I read on DigitalOcean's site that raid10 needed at least three drives to configure. Maybe it was a typo because their example shows four drives. I do have a fourth drive like the other three now I just purchased. I was going to pull the drive I'm having the problem with, replace it and reinstall Ubuntu Server if I couldn't get this resolved. I'd rather understand what is going on here though, so thanks again for your help.
     Here is the output of: sudo mdadm -v --zero-superblock /dev/sdb1

      mdadm: Couldn't open /dev/sdb1 for write - not zeroing

     This was a Plex server originally and I'm not worried about losing any data on sbd1. All those media files are backed up. As I stated above, I already removed persistent references in /etc/fstab and commented out the array in mdadm.conf. Then I updated initramfs. I think I should of waited till I figured out why the third drive wouldn't zero before I continued on with those last steps. Maybe raid10 isn't what I should use. I most likely will use this server for backup of documents and media files mostly. I have been reading about creating a NAS or a cloud server. I'm not sure which direction to go yet. This is a learning tool at this point.

Take care,
fewjr

This is the output of: lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT

goblin@Goblinservant:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME     SIZE FSTYPE            TYPE MOUNTPOINT
sde    111.8G                   disk
&#9492;&#9472;sde1 111.8G ext4              part /
sdf      1.8T                   disk
&#9492;&#9472;sdf1   1.8T linux_raid_member part
sdg      1.8T                   disk
&#9492;&#9472;sdg1   1.8T ext2              part
sdh      1.8T                   disk
&#9492;&#9472;sdh1   1.8T ext2              part
sr0     1024M                   rom

sdb1 has changed to sdf1, I think because I tried to restart the array the other night to reverse the steps I performed after zeroing 2 out of the 3 drives.

---

### Post by darkod on 2019-02-02
Well, there lies your problem. You should always check current disk letters to make sure you are working with the correct disk/partition. sdb1 doesn't even exist.

Yes, raid10 can be created with 3 disks but only because you will tell it one member is missing. It needs 4 at least. Creating it with 3 in fact you are creating it degraded from the start (like one disk already failed).

So, now that you know the correct disk letters, can you zero the superblock? Is it sdf1?

If it still doesn't work, try adding --force to the zero command. That should force it.

PS. I also notice sdg1 and sdh1 have filesystem on them. You shouldn't format partition that you will use for mdadm. It can work, but it's not how it's usually done. The filesystem lies on the md devices, not on the physical partitions. So, you don't format the partitions with ext4 or any other filesystem.

---

### Post by fewjr on 2019-02-02
goblin@Goblinservant:~$ sudo mdadm --zero -superblock --force /dev/sdf1
mdadm: option -u not valid in misc mode

Had a space in there that didn't belong...good Lord

goblin@Goblinservant:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdf1[0](S)
      1953382400 blocks super 1.2

Okay....this is what I have now....thank you.

goblin@Goblinservant:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME     SIZE FSTYPE TYPE MOUNTPOINT
sde    111.8G        disk
&#9492;&#9472;sde1 111.8G ext4   part /
sdf      1.8T        disk
&#9492;&#9472;sdf1   1.8T ext2   part
sdg      1.8T        disk
&#9492;&#9472;sdg1   1.8T ext2   part
sdh      1.8T        disk
&#9492;&#9472;sdh1   1.8T ext2   part
sr0     1024M        rom

....and I have no idea why I have ext2 partitions.I installed 18.04.1 and used the alternative download. If you had the patients.....which you definitely must have, I could explain what I did from the get go when I plugged this box back in.

Just curious, but why did the partition letters change before?

---

### Post by darkod on 2019-02-02
Disk letters can change for various reasons. Most often is if you have something like usb stick connected when booting, it can be detected first and the disks can come later. So letters can be moved by one.

I have to admit I find it strange your lsblk shows disks E-H. What is it with A-D?

But at the end of the day, it doesn't matter. Ubuntu uses UUID since long ago, precisely not to depend on disks changing letters. So you can safely ignore this. You can also ignore the fact that partitions seem to have filesystem. It simply won't get used.

You can create raid10 array as it is. And with one disk missing of course. The command would be something like:
```
sudo mdadm --stop /dev/md0
```

The above is to get rid of inactive md0 that seems to be reported with sdf1 as spare.

Then continue creating new array:
```
sudo mdadm --create /dev/md0 --verbose --level=raid10 --raid-devices=4 /dev/sdf1 /dev/sdg1 /dev/sdh1 missing
```

That should do it...

After creating check the array UUID with blkid and adjust it into /etc/mdadm/mdadm.conf if needed to make sure it assembles correctly on reboot. If you don't know how to do that we can work on it after you create the array.

---

### Post by fewjr on 2019-02-02
goblin@Goblinservant:~$ sudo mdadm --create /dev/md0 --verbose --level=raid10 --raid-devices=4 /dev/sdf1 /dev/sdg1 /dev/sdh1 missing
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: chunk size defaults to 512K
mdadm: /dev/sdf1 appears to contain an ext2fs file system
       size=1953513472K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdg1 appears to contain an ext2fs file system
       size=1953513472K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdh1 appears to contain an ext2fs file system
       size=1953513472K  mtime=Wed Dec 31 19:00:00 1969
mdadm: size set to 1953381376K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

goblin@Goblinservant:~$ blkid
/dev/sdh1: UUID="b745a374-1e58-4e72-aabe-f49c98ad627d" TYPE="ext2" PARTUUID="000         88bfc-01"
/dev/sde1: UUID="04de2114-03d1-4788-8a2a-0dd55ded89f1" TYPE="ext4" PARTUUID="55b         fcd04-01"
/dev/sdf1: UUID="7e1fe993-8c54-fd60-d271-3128ac28517e" UUID_SUB="c9304467-d700-9         ad6-23f8-79c44a543892" LABEL="goblinservant:0" TYPE="linux_raid_member" PARTUUID         ="000f3f42-01"
/dev/sdg1: UUID="e979185e-31bb-46b5-be95-a644132b633f" TYPE="ext2" PARTUUID="000         18d04-01"

This is what I have now:
goblin@Goblinservant:~$  lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME      SIZE FSTYPE            TYPE   MOUNTPOINT
sde     111.8G                   disk
&#9492;&#9472;sde1  111.8G ext4              part   /
sdf       1.8T                   disk
&#9492;&#9472;sdf1    1.8T linux_raid_member part
  &#9492;&#9472;md0   3.7T                   raid10
sdg       1.8T                   disk
&#9492;&#9472;sdg1    1.8T linux_raid_member part
  &#9492;&#9472;md0   3.7T                   raid10
sdh       1.8T                   disk
&#9492;&#9472;sdh1    1.8T linux_raid_member part
  &#9492;&#9472;md0   3.7T                   raid10
sr0      1024M                   rom

---

### Post by darkod on 2019-02-03
Was that blkid output before or after you created the new array? Because if it was after, it doesn't look correct.

Now that you have the array created, post the output of:
```
sudo blkid
```

---

### Post by fewjr on 2019-02-03
goblin@Goblinservant:~$ sudo blkid
[sudo] password for goblin:
/dev/sdh1: UUID="e0d13ffb-8a8f-22a9-a0b4-4ba8c7ac92a8" UUID_SUB="630ddc5a-4e79-003c-771d-6658d190e2c4" LABEL="Goblinservant:0" TYPE="linux_raid_member" PARTUUID="00088bfc-01"
/dev/sde1: UUID="04de2114-03d1-4788-8a2a-0dd55ded89f1" TYPE="ext4" PARTUUID="55bfcd04-01"
/dev/sdf1: UUID="e0d13ffb-8a8f-22a9-a0b4-4ba8c7ac92a8" UUID_SUB="1e531906-c5ee-7392-81e1-ba558c6b3212" LABEL="Goblinservant:0" TYPE="linux_raid_member" PARTUUID="000f3f42-01"
/dev/sdg1: UUID="e0d13ffb-8a8f-22a9-a0b4-4ba8c7ac92a8" UUID_SUB="c0b650e0-b5b8-a19c-abe5-1174af793fdd" LABEL="Goblinservant:0" TYPE="linux_raid_member" PARTUUID="00018d04-01"

It was after and I didn't run it with sudo. When I got up this morning for work I ran it again with sudo and the output was different. It looks good now right? So now I need to add the fourth drive to the array. I still don't know why that one drive wouldn't zero in the beginning when they were sdb1, sdc1, sdd1. Two of them zeroed fine but sdb1 wouldn't. What caused that to start with? That was before I made things worse.

---

### Post by darkod on 2019-02-03
Yes, it looks better now. The UUID of the array is e0d13ffb-8a8f-22a9-a0b4-4ba8c7ac92a8 and you need to make sure it is in mdadm.conf. Open /etc/mdadm/mdadm.conf and make sure the line that defines md0 is something like:
```
ARRAY /dev/md0  metadata=1.2 UUID=e0d13ffb:8a8f22a9:a0b44ba8:c7ac92a8
```

You can remove any additional info (like array name) from that line, it doesn't matter. If you set it as above, that is the minimum needed for the array to reassemble on boot.

I don't know why sdb1 wouldn't zero. If you added --verbose to the command it should have given you more output info. Maybe it was in use, or something. Doesn't matter now anyway.

Yes, now you need to partition the last disk and add it to the array. Make sure the partition is equal or bigger than the current array partitions otherwise mdadm won't accept adding it.

PS. To use the array you need to format it and mount it.

---

### Post by fewjr on 2019-02-03
Well okay then..... that's great! I really appreciate your help. I was definitely stuck.
fewjr

---

