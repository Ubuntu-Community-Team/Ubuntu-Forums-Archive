---
title: "raid one stops ubuntu from booting"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by stuckeyneila1982 on 2013-02-14
I turned my old AMD box into a simple file sharing/backup/streaming server. I got it working except for one issue.  when i reboot the server it stops and says error mounting volume press "s" to skip mounting or "m" for manual recovery.  I hit skip and i can see the raid 1 array in ubuntu and its mounted and functional.  I can read write and share files to and from windows.  But every time i reboot i get the same message. the  cat /proc/mdstat shows the raid and no errors and all devices are there.  any ideas? I have a feeling i messed up somewhere but dont no what to do besides deleting the raid1 array and restarting.

---

### Post by stuckeyneila1982 on 2013-02-14
Oh i am running 12.10 fully updated.  AMD dual core 2GB ram 2x1TB WD in mdadm raid 1 with a WD 500gb as OS drive.

---

### Post by darkod on 2013-02-14
The message would say what it can't mount exactly. There will be some UUID string or similar.

What does it say?

---

### Post by stuckeyneila1982 on 2013-02-14
Im at work now and not at my Ubuntu box.  But i believe the error  UUID matches my Raid UUID.  thats why i cant figure out what to fix.  Because when i hit skip at the Ubuntu splash screen i dont know why its mounted and working.  Just annoying to have to skip everytime i boot because im running headless and i have to move my keyboard mouse and monitor to hit skip to finish boot.  I could be wrong and may have not setup correctly.  or made another raid partition or something by accident.  Ill have to go home and look more closely. 

thanks for the reply

---

### Post by stuckeyneila1982 on 2013-02-14
in the disks section in ubuntu it shows raid as md127.   I wonder if somehow i created a md0 by accident and have a non functioning partition or a partial config of a RAID and its hanging on Boot.  Any commands to check would be appreciated.  As i am not a Ubuntu terminal expert.  I do a lot of Google Foo and breaking Ubuntu and reinstalling.  That's how you learn i guess.

---

### Post by darkod on 2013-02-14
OK, double check the UUIDs, I assume you know you can check them with:
sudo blkid

Also look what /etc/fstab says.

And if maybe the raid is degraded or not (one disk failed). Depending on the selection when you created the array, it might not boot degraded if you told it not to boot, even when raid1 can work with one disk failed.

I just noticed your latest post. It seems from threads here that sometimes md0 is converted in md127 on some reboot/upgrade, etc. I still haven't seen a clear answer why.

Check the UUIDs and what you have in fstab. I think it's safe to edit /etc/mdadm/mdadm.conf and switch md127 back to md0.

One thing to try and see how the arrays work is:
cat /proc/mdstat

That should show if a disk is failed or not.

---

### Post by stuckeyneila1982 on 2013-02-14
ok first error  " an error occurred while mounting /mnt/5b187bea-oedd-4a92-b535-0839f6bfcdf1 press "s" to skip or "m" for manual recovery 

2nd error  "disk not found /mnt90c42f75-1cb3 - 4f54-97f3-2a427-4b98566 is not ready or not present 

if i hit skip both it loads Ubuntu and i see a working RAID1

---

### Post by stuckeyneila1982 on 2013-02-14
Sudo blkid     
 

 neil@server:~$ sudo blkid 
 [sudo] password for neil:  
 /dev/sda1: UUID="3cd07e7d-b053-a4b4-802f-3a05a94b51a4" UUID_SUB="e0fd9083-1ace-03dc-13e2-7ee9136feae9" LABEL="server:0" TYPE="linux_raid_member"  
 /dev/sda5: UUID="2e0b411d-2610-46ba-8c3f-b8d8d1ca4eff" TYPE="swap"  
 /dev/sdb1: UUID="3cd07e7d-b053-a4b4-802f-3a05a94b51a4" UUID_SUB="db895183-94e2-5b0c-c8a2-824c58673c27" LABEL="server:0" TYPE="linux_raid_member"  
 /dev/sdb5: UUID="2e0b411d-2610-46ba-8c3f-b8d8d1ca4eff" TYPE="swap"  
 /dev/sdc1: UUID="0103df44-2e31-4dbc-a1ce-b531d2e85209" TYPE="ext4"  
 /dev/sdc5: UUID="6598f0b3-04a3-4f9a-bb01-7eb1de475c4f" TYPE="swap"  
 /dev/md0: LABEL="Raid" UUID="5b187bea-0edd-4a92-b535-0839f6bfcdfd" TYPE="ext4"  
 neil@server:~$  
 

 then  
 

 bash: /etc/fstab: Permission denied 
 neil@server:~$ sudo -s  
 root@server:~# /etc/fstab 
 bash: /etc/fstab: Permission denied 
 root@server:~# sudo -i 
 root@server:~# /etc/fstab 
 -bash: /etc/fstab: Permission denied 
 root@server:~# sudo /etc/fstab 



/etc/mdadm/.conf


gives me permission denied even at root not sure whats up with this?

---

### Post by stuckeyneila1982 on 2013-02-14
looks like md0 thinks its raid but is a partial setup or something.  Safe to delete?

---

### Post by stuckeyneila1982 on 2013-02-14
root@server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      974464832 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

---

### Post by stuckeyneila1982 on 2013-02-14
/etc/mdadm/.conf
DEVICE partitions
ARRAY /dev/md/0 metadata=1.2 name=server:0 UUID=3cd07e7d:b053a4b4:802f3a05:a94b51a4

---

### Post by SaturnusDJ on 2013-02-15
/etc/fstab and /etc/mdadm/mdadm.conf aren't commands but files. You need to tell linux what you want to do with them.
```
cat /etc/fstab
```
This will print the file in terminal

```
nano /etc/mdadm/mdadm.conf
```
To edit in terminal using nano. (Another cli editor is 'vi',  gedit is common for Ubuntu gui, but because your are using Lubuntu I think you need to use Leafpad.)

---

### Post by darkod on 2013-02-15
> **stuckeyneila1982 said:**
> ok first error  " an error occurred while mounting /mnt/5b187bea-oedd-4a92-b535-0839f6bfcdf1 press "s" to skip or "m" for manual recovery 

2nd error  "disk not found /mnt90c42f75-1cb3 - 4f54-97f3-2a427-4b98566 is not ready or not present 

if i hit skip both it loads Ubuntu and i see a working RAID1

The first UUID is from md0. I don't know why it throws an error, maybe it's not assembled yet when it tries to boot it.

That second UUID really doesn't exist, you can see that in the blkid results. Did you have a swap on mdadm device too and somehow it got deleted? I am asking because sda2 and sdb2 have same UUID which is only possible if they were in mdadm, but there is no other mdadm device right now except md0.

---

### Post by stuckeyneila1982 on 2013-02-15
Interesting.  I think a long time ago i tried making a raid in ubuntu on these disks is it possible there is an extra partition or swap or some kind of object pointing ubuntu to a raid that doesnt exist?  Would it be best just to delete and start over?  

this is the guide i used 
[http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)

the only other thing i did was **dpkg**-reconfigure [B]mdadm
and that asked for booting with degraded setting up email notification etc.  
[/B]

---

### Post by darkod on 2013-02-15
It doesn't exist?

The /proc/mdstat clearly shows there is mdadm array md0 and it's assembled. Whether you are using it on purpose or not, that's not up to the computer to decide. It's only a machine. :)

So, do you want to break the SW raid? What will you boot? Do you have ubuntu on sdc1?

If you are not sure of anything, install and run boot-repair and create the bootinfo summary. Post the link it gives you so we can see more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by stuckeyneila1982 on 2013-02-15
neil@server:~$ sudo blkid 
 [sudo] password for neil:  
 /dev/sda1: UUID="3cd07e7d-b053-a4b4-802f-3a05a94b51a4"  UUID_SUB="e0fd9083-1ace-03dc-13e2-7ee9136feae9" LABEL="server:0"  TYPE="linux_raid_member"  
 /dev/sda5: UUID="2e0b411d-2610-46ba-8c3f-b8d8d1ca4eff" TYPE="swap"  
 /dev/sdb1: UUID="3cd07e7d-b053-a4b4-802f-3a05a94b51a4"  UUID_SUB="db895183-94e2-5b0c-c8a2-824c58673c27" LABEL="server:0"  TYPE="linux_raid_member"  
 /dev/sdb5: UUID="2e0b411d-2610-46ba-8c3f-b8d8d1ca4eff" TYPE="swap"  
 /dev/sdc1: UUID="0103df44-2e31-4dbc-a1ce-b531d2e85209" TYPE="ext4"  
 /dev/sdc5: UUID="6598f0b3-04a3-4f9a-bb01-7eb1de475c4f" TYPE="swap"  
 /dev/md0: LABEL="Raid" UUID="5b187bea-0edd-4a92-b535-0839f6bfcdfd" TYPE="ext4"  
 neil@server:~$

I have ubuntu on its own 500Gb drive non raid ext4 i think its sdc5 right? not sure.  But ubuntu is on its own drive non raid.  the RAID does not have the OS on it.  

So yeah we can wipe it delete whatever.  Nothing stored there.

---

### Post by darkod on 2013-02-15
To be precise, in that case ubuntu is on sdc1, the ext4 partition. sdc5 is a swap partition.

If you DO want to destroy the raid meta data, you can zero the superblock on each partition and that will delete the mdadm info. Also, open /etc/mdadm/mdadm.conf and remove the ARRAY definition.

After you have removed the definition stop the array and zero the superblock:
```
sudo mdadm --stop /dev/md0
sudo --zero-superblock /dev/sda1
sudo --zero-superblock /dev/sda5
sudo --zero-superblock /dev/sdb1
sudo --zero-superblock /dev/sdb5
```

After that it should not assemble any more.

You can reformat and reuse the sda and sdb disks as you wish.

---

### Post by stuckeyneila1982 on 2013-02-15
Ok i will try after work.  After i zero out the devices is the guide i used earlier in my post not correct?  Could you possibly show me the commands to make a Raid1 with mdadm?

---

### Post by stuckeyneila1982 on 2013-02-15
By the way darkod i really appreciate all your help.

---

### Post by darkod on 2013-02-15
> **stuckeyneila1982 said:**
> Ok i will try after work.  After i zero out the devices is the guide i used earlier in my post not correct?  Could you possibly show me the commands to make a Raid1 with mdadm?

Assuming you want to make it from sda1 and sdb1, you only need to do:
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
```

That doesn't add it automatically to mdadm.conf but you can do it with:
```
sudo mdadm --examine --scan >> /etc/mdadm/mdadm.conf
```

The ARRAY definition in mdadm.conf will assemble it on every boot.

---

### Post by stuckeyneila1982 on 2013-02-15
Ok ill give it a shot after work and post results.  Cant thank you enough gave you a +1 on your membership page.

---

### Post by stuckeyneila1982 on 2013-02-16
Ok followed your instructions there. i still was unable to boot.  I found when i tried to zero the block id's on the two that showed the error on boot  it said devices not found.  So that got me thinking and i looked in nano /etc/fstab and they were listed.  I removed these two lines saved and rebooted and boom it went right to desktop with a working RAID array.  

Thanks darkod i would have not gotten this far without your help.  Glad to see there's some still willing to help us newbies.

---

