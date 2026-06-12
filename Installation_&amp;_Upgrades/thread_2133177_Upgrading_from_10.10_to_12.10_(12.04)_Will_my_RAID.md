---
title: "Upgrading from 10.10 to 12.10 (12.04?) Will my RAID5 automatically reconfigure?"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by eMTea on 2013-04-07
Hi!

I have been running my fileserver for a long time without issues, but now I need to upgrade it to the latest.
Would you recommend using the .04, since this is just an headless server, and hopefully will be untouched for another long time?

To to this upgrade, I need to do a complete reinstallation, but what will happen to my 5disc RAID5 system? I have the OS on a separate SSD drive.

Will the RAID5 system pop up and mount itself on a fresh install, or will I have to mess with it again?
I'm not that good with linux, and as far as I remember, I spent alot of time setting it up the first time, hope I don't have to do it again, and maybe loose my 7TB of media..

---

### Post by darkod on 2013-04-07
If the raid5 is software raid with mdadm, and the OS is on separate disk, it should be fine. You will install the 12.04 LTS on the OS disk, and later add the existing array. Just make sure you DO NOT create a new array during installation, that will overwrite the current one.

In your place I would install only the OS and leave the mdadm alone during installation. You can easily add the array to the OS later.

As for setting it up, if you mean various configuration of the OS, you will have to do that gain in most cases. Those settings can't exist in the new clean install until you do them again.

Some things, like the samba config in smb.conf you can easily redo by making a copy of your smb.conf and restoring it on the new system after you install the OS and samba.

---

### Post by eMTea on 2013-04-07
Ok, this doesn't sound too bad :)

Raid5 is software with mdadm yes, so I'll just ignore the setup of the RAID during installation, and just add it in Disk Manager afterwords?

But where do I find the smb.conf file?

---

### Post by darkod on 2013-04-07
/etc/samba/smb.conf

I prefer using the terminal for mdadm but Disk Manager should be fine I guess.

---

### Post by eMTea on 2013-04-07
I have a problem with the current installation, that the RAID will not mount on startup, I have to manually stop it, start it and mount it. Hope this gets fixed in a new installation :)

---

### Post by darkod on 2013-04-07
You may have errors in /etc/mdadm/mdadm.conf or /etc/fstab but since you plan to reinstall anyway it might not be worth the time to troubleshoot.

In the new installation you might need to first add the mdadm package since the Desktop version doesn't include it by default, then to assemble the existing array (VERY IMPORTANT, use only --assemble and never --create, that will create new array destroying the old one, and then you are in big trouble). And then to include the details of the new array in mdadm.conf.

So, once your new OS is installed, the mdadm part would go like:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

The first command install the package, the second scans the disks and assembles any array it can find which in your case should be your existing array. Then the third line makes an ARRAY definition in mdadm.conf which will assemble the array on boot.

From there on, you need to make a correct entry in fstab to make it mount on boot and that's it. Don't forget that first time you will also need to create the folder/mount point, depending which mount point you are using for the array.

---

### Post by eMTea on 2013-04-07
I have assebled the array using mdadm, and got this line in the end of mdadm.conf file:

> # definitions of existing MD arrays
ARRAY /dev/md/filserver metadata=1.2 UUID=2b62d9ee:aa10b351:4066d03d:74615324 name=:filserver


But what do I do next to add it to fstab and make it mount automatically on boot?
It is such a long time ago I set it up the first time, and I don't remember the file system I used, where can I find such details?

---

### Post by darkod on 2013-04-07
You can use the /dev/mdX or the UUID of the mdadm device, and if you have ext4 filesystem on the raid, depending what your mount point is it would be:
```
/dev/mdX   /mountpoint   ext4   defaults   0   2
```

If you want to use the UUID just replace /dev/mdX with UUID=<string>.

You can get the UUIDs for all partitions with:
sudo blkid

---

### Post by eMTea on 2013-04-07
I entered this text in the fstab:
> UUID=2b62d9ee:aa10b351:4066d03d:74615324 /media/filserver   ext4   defaults    0   2


During startup, I get the message that the ARRAY is not ready.
When I open the home folder, and presses the "filserver" icon, it automounts, and I can use it. 
The problem is that when I setup samba shares, and the media is not mounted on startup, the samba share setting is lost, and I have to do them all over again :(

EDIT:
I replaced the "2" with 0, to skip checking until network is available, (wait for mdadm to start?) and it seems to solve the problem.
I also added a "user" command to be able to find it using logitech media server.

---

### Post by darkod on 2013-04-07
Does the folder /media/filserver exist?

I wouldn't use /media to mount raid. The /media folder is usually used for temporary mounts, not for permanent ones. For example, by clicking on the raid array filserver, it will mount at /media/filserver but that doesn't mean the folder exists before you click on the array. And the folder needs to exist so thet fstab can mount it.

Do this. Reboot the server, and without clicking on the raid array at all, without even touching it, open terminal and post the output of these commands:
```
cat /proc/mdstat
sudo blkid
ls /media
```

After I see the results I can give you my opinion.

---

### Post by eMTea on 2013-04-07
I created a folder on /media that is named filserver, and with the fsck order set to 0 it mounts perfectly on startup. 
Maybe it mounts ok because of the creation of the folder, not the fsck order?

Last time i rebooted, without any clicking, it mounts and samba shares are ok :)

This is what I get immediately after reboot:
> emtea@eMTeaSERVER:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid5 sda1[1] sdb1[0] sde1[3] sdd1[5] sdf1[2]
      7814045696 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      bitmap: 0/466 pages [0KB], 2048KB chunk

unused devices: <none>
emtea@eMTeaSERVER:~$ sudo blkid
[sudo] password for emtea: 
/dev/sda1: UUID="2b62d9ee-aa10-b351-4066-d03d74615324" UUID_SUB="c5ca8154-d378-6755-dc24-de7232691980" LABEL=":filserver" TYPE="linux_raid_member" 
/dev/sdb1: UUID="2b62d9ee-aa10-b351-4066-d03d74615324" UUID_SUB="6e8cd6a8-0007-fe7b-6bca-f320ddb3a91a" LABEL=":filserver" TYPE="linux_raid_member" 
/dev/sdc1: UUID="cc79740b-098d-4fe4-a61e-fa467b94bfdf" TYPE="ext4" 
/dev/sdc5: UUID="a32a8cf9-5d4a-453b-8c52-893e9f96ad0d" TYPE="swap" 
/dev/sdd1: UUID="2b62d9ee-aa10-b351-4066-d03d74615324" UUID_SUB="7228e161-b31c-055b-1704-e21f54514120" LABEL=":filserver" TYPE="linux_raid_member" 
/dev/sde1: UUID="2b62d9ee-aa10-b351-4066-d03d74615324" UUID_SUB="eadbb89b-b95e-9f98-4ce3-9bb852200b66" LABEL=":filserver" TYPE="linux_raid_member" 
/dev/sdf1: UUID="2b62d9ee-aa10-b351-4066-d03d74615324" UUID_SUB="440aefdd-87f2-a3c7-6103-687582eb3c77" LABEL=":filserver" TYPE="linux_raid_member" 
/dev/md127: LABEL="filserver" UUID="f46c3568-c132-4c5b-a133-2ec06d842d5e" TYPE="ext4" 
emtea@eMTeaSERVER:~$ ls /media
emtea  filserver  floppy  floppy0
emtea@eMTeaSERVER:~$ 

---

### Post by darkod on 2013-04-07
If the folder didn't exist, then the mount point you were specifying in fstab didn't exist to be used. fstab will not create it, only use it. So it needs to exist.

Now it works because you created it.

---

### Post by eMTea on 2013-04-07
Thanks alot for you help Darko! Really appreciate it!

---

### Post by eMTea on 2013-04-18
Suddenly after a reboot it would not mount the raid on startup. Says it is not ready or present.
I booted without mounting and tried to mount manually, but I get this error:
> emtea@eMTeaSERVER:~$ sudo mount -a
mount: special device UUID="f46c3568-c132-4c5b-a133-2ec06d842d5e" does not exist


Can someone help me? :P

---

### Post by darkod on 2013-04-18
Have you checked to which device that UUID belongs to? You can do that with:
sudo blkid

That will show which device it can't find. It might be the array UUID. You can also see the array UUID in mdadm.conf.

---

### Post by eMTea on 2013-04-18
It seems like the raid UUID was changed somehow. the UUID was: 2b62d9ee-aa10-b351-4066-d03d74615324, but when I replace it in fstab, it does not mount it on startup anyway.
There is a line in fstab like this: 
> /dev/sr0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
I do not have a floppy, any particular reason for this line, or can I remove it?

This is the last line from the boot.log after I chose to skip the mounting:
> 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mountall: mount /media/filserver [397] terminated with status 32
mountall: Filesystem could not be mounted: /media/filserver
Skipping /media/filserver at user request


I ran the "dmesg | tail" commmand, and it tells me: 
> EXT4-fs (md127): warning: maximal mount count reached, running e2fsck is recommended


How do I run the e2fsck on my array?

I'd like to add that after the machine is booted, "filserver" mounts nice if i click it, but not by "sudo mount -a" command.

---

### Post by darkod on 2013-04-18
Wasn't your array md0? Now it seems to be md127.

In the mdadm.conf does the ARRAY definition say 0 or 127?

I have seen it sometimes changed to 127 but I have no idea when or why it happens.

You can try running fsck but the array needs to be unmounted, so don't mount it manually, and the auto mounts seems not to work anyway:
```
sudo fsck /dev/md127
```

Yes, you can remove the /dev/sr0 line from fstab, I have no idea how it got there.

In the blkid output the shared UUID of the raid disks seem the same as the old one, only the md127 has a new one. If there is a defitnion for 127 in mdadm.conf I would comment it out so that it doesn't try to assemble on boot.

Then I would check the disk order in md0 (if you don't have it written down from before, it might be even posted in this thread), and once you have the exact order you can try assembling it as md0 manually. You can view details of the superblokc with --examine and the Device Role will tell you the order of the partitions:
```
sudo mdadm --examine /dev/sd[abdef]1
```

---

