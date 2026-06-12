---
title: "installer doesn't see all drives / partitions - solved"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by heiko_s on 2010-05-10
I write this in the hope it is of help to you. Note: Please follow the advise below **at your own risk. Backup any and all important data!** You have been warned.

When I tried to install Ubuntu 9.10 or 10.04 (from CD or USB drive), and selected manual partitioning, the installer would not show all my drives.

However, when booting the life CD/USB, gparted or the Disk Utility did recognize all drives and partitions.

It turned out that one of my drives was marked as RAID partition, although I never used RAID!

Here the symptom:

When you run the installer and select "manual partitioning", the resulting list of drives and partitions is incomplete. In my example it was:

sda
- sda1
sdc
- sdc1
- sdc2
- sdc3
...

sdb was missing!

In order to analyze the problem, you can do the following:

cd into a mounted, writable directory (USB stick, persistent)

```
> udevadm info --export-db > file.txt
```

Open the file.txt and search for "ID_FS_TYPE=". There are usually multiple appearances of it. Check all of them.

If you discover something like that:

E: ID_FS_TYPE=isw_raid_member
E: ID_FS_USAGE=raid

and **you do NOT use RAID**, then follow the instructions below:

See the lines above the ID_FS_USAGE=raid part and identify the drive, for example: E:

DEVNAME=/dev/sdb

Does it correspond with the missing drive?

If yes, let's make sure we don't damage a RAID installation:

```
> sudo dmraid -ay
```

Read what it tells you - did it mount RAID partitions/drives?

One more precautionary step:

```
> ls /dev/mapper
```

If there is **no or only one drive/partition listed**, it is reasonable save to assume you are not running RAID.

If it says something like /dev/mapper/nvidia_aebhdfib1 ...2 ...5 etc., **stop right here and consult an expert**.

Once you made sure you don't destroy an existing RAID, let's remove the incorrect RAID mark from the drive:

```
> sudo dmraid -E -r /dev/sdX
```

where X is the drive designation. Don't add a number, we refer to the drive, not to a partition. In my example above the command is:

```
> sudo dmraid -E -r /dev/sdb
```

You may have multiple drives with the RAID metadata on it. In that case you need to repeat the above command for all those drives. **Just make sure you don't wipe out your existing RAID, if you have one.**

Reboot the system and see if it works.

P.S.: Also check your BIOS settings - do you have drives configured as RAID?

Good luck.

---

### Post by ronparent on 2010-05-10
Good tutorial. Despite the fact that most new MB's have a raid capability built in, little attntion has been given to informing users of potential pitfalls with them. You have covered one aspect of this very well. Congratulations.

---

### Post by heiko_s on 2010-05-10
Thanks. However, the credit should go to frantid, oldfred, ronparent and gooched who identified the problem and pointed me to the solution. I only summarized it, since I'm a lazy guy and like things as straightforward as possible.

There seems to be another solution to the same issue, which sounds a lot easier:
After booting into the live CD/USB, just remove the dmraid and all should be fine:

```
> sudo apt-get remove dmraid
```

That's it.

The reason I didn't choose the above solution is that it treats the symptoms, not the cause. Let's say that in 2 years from now some package dependancy requires the re-installation of dmraid. I could run into this or a related problem again and I'm not sure I would remember how to fix it.

---

### Post by heiko_s on 2010-05-10
> **ronparent said:**
> Good tutorial. Despite the fact that most new MB's have a raid capability built in, little attntion has been given to informing users of potential pitfalls with them. You have covered one aspect of this very well. Congratulations.

Also thanks to you.

---

### Post by jc3835 on 2010-05-16
heiko_s, thanks for all of your investigation into this issue.
I had the same problem yesterday when trying to upgrade this machine from a USB thumbdrive in that the installer would see all drives but the one SATA drive I wanted to install to. Then the drive would show up under GParted and an fdisk -l when I was in the LiveCD mode.
What I found interesting was that other SATA drives on the same channel were showing up in the installer.
Can this have something to do with Windows 7 being on the drive first? I've never used that disk as part of a RAID, so I was wondering if something Windows does trips that issue.
I went the simple route with removing dmraid from apt-get, although I do agree with you about the problem coming back if you ever need to install dmraid, especially if it gets grabbed as a dependency and you don't notice.

Thanks again.

---

### Post by rmjohnson144 on 2010-05-20
Thanks, this worked great, although I used the info from your original post.  My problem was slightly different in that my drive was in a RAID 0 array over a year ago and have many OSes installed since.  This is the first time for this drive to have Ubuntu apparently as I've never had this happen before.

When I ran the installer, I got nothing from my drive.  The 10.4 live CD said it was there and functioning properly. But the command:

```
sudo dmraid -ay
```

said it was an incomplete raid.  and all I had to do was:

```
sudo dmraid -E -r /dev/sda
```

as my drive was assigned SDA. 

Now it is installing just fine on my other computer as I type here, on my backup computer.

so sometimes it doesn't have to be in RAID currently as it will know it was in a RAID mode at some point in time.

Thanks for all your help
-=Mark=-

---

