---
title: "After upgrade: [RAID] is not ready yet or not present."
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by heltsvensk on 2013-01-22
I’ve been running RAID10 on two hard drives for backup, but after I just allowed Ubuntu 12.10 to perform automatic updates, now at boot I get the following message:

> The disk drive for /mnt/Backup is not ready yet or not present.
Continue to wait, or press S to skip mounting or M for manual recovery.

I can continue to wait forever, but nothing happens.  When I skip mounting at boot, then if I try to mount manually, here’s what happens:

> $ sudo mount -a
mount: specialenheten /dev/md0 finns inte
*(English translation would be something like ‘the special device /dev/md0 does not exist’.)*

Thanks so much for any help!

---

### Post by darkod on 2013-01-22
You didn't specify whether you have SW raid with mdadm, or another type of raid?

This is just the storage array? The system can still boot, right?

If it can, what does this show:
```
cat /proc/mdstat
```

---

### Post by heltsvensk on 2013-01-22
Thanks for getting back to me.  Yes, I’m running software RAID with mdadm.  The problem concerns only the storage array, not the boot disk.

> $ cat /proc/mdstat
md127 : active (auto-read-only) raid10 sdb[0] sdc[1]
1953382912 blocks super 1.2 256K chunks 2 far-copies [2/2] [UU]

I know this response says “md127”, but the number was that way before, too.  Not sure what explains the difference between md127 and md0.

Trying “sudo mount -a” still gives the same error, and navigating to the /mnt/Backup location still shows nothing that was there before upgrading the system.

---

### Post by darkod on 2013-01-22
Ok, can you post the fstab:
cat /etc/fstab

Also, try mounting md127, not md0, to some temp mount point like:
```
sudo mount /dev/md127 /mnt
ls /mnt
```

Did that mount and did it list some data from the storage array?

---

### Post by heltsvensk on 2013-01-22
Thanks, Darko!

```
$ cat /etc/fstab
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=deebe173-062a-4e6b-8343-1050d924805d /               ext4    errors=remount-ro 0       1
/dev/md0	/mnt/Backup	ext4	errors=remount-ro	0	1
# swap was on /dev/sda5 during installation
#UUID=645b0132-14bc-4622-a50c-d015734341a4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

```
$ sudo mount /dev/md127 /mnt/Backup
mount: du måste ange filsystemstypen
*(“mount: you must specify the filesystem’s type”)*

```

---

### Post by darkod on 2013-01-23
In the fstab it is still looking to mount md0 while the array device has somehow changed to md127.

Make a copy of fstab and edit it replacing /dev/md0 with /dev/md127, then try the mount -a.
```
sudo cp /etc/fstab /etc/fstab.copy
gksu gedit /etc/fstab
sudo mount -a
```

After editing with gedit save and close the file, then run the mount -a and see if it mounts it.

Also, in the fstab entry for /dev/md0 you have the option as errors=remount-ro which is standard for the root partition, not for data partitions. If you did this on purpose, OK, but if not, you can change that with simply 'defaults' (without the quotes). That will use the default options.

---

### Post by SaturnusDJ on 2013-01-23
The format of /etc/mdadm/mdadm.conf has probably changed. You'll get the normal md device instead of the temporary md127 after you've fixed this.
[http://ubuntuforums.org/showpost.php?p=10907831&postcount=6](http://ubuntuforums.org/showpost.php?p=10907831&postcount=6)

---

### Post by heltsvensk on 2013-01-23
> **darkod said:**
> In the fstab it is still looking to mount md0 while the array device has somehow changed to md127.

Make a copy of fstab and edit it replacing /dev/md0 with /dev/md127, then try the mount -a.
```
sudo cp /etc/fstab /etc/fstab.copy
gksu gedit /etc/fstab
sudo mount -a
```

After editing with gedit save and close the file, then run the mount -a and see if it mounts it.

As I mentioned, I noticed this md0/md127 difference even before updating, but the problem of unmountability showed up only after updating.  Per this suggestion, I’ve just tried editing /etc/fstab to replace “md0” with “md127”, but then

```
$ sudo mount -a
    mount: fel filsystemstyp, felaktig flagga, felaktigt superblock
    *mount: wrong fstype, bad option, incorrect superblock*
        på /dev/md127, codepage eller hjälpprogram saknas, eller annat fel
        *on /dev/md127, codepage or helper application is missing, or other error*
        I en del fall kan användbar information hittas i syslog
        *In some cases, useful information can be found in syslog*
        - prova dmesg | tail eller något liknande
        *try dmesg | tail or something like that*

```

---

### Post by heltsvensk on 2013-01-23
> **SaturnusDJ said:**
> The format of /etc/mdadm/mdadm.conf has probably changed. You'll get the normal md device instead of the temporary md127 after you've fixed this.
[http://ubuntuforums.org/showpost.php?p=10907831&postcount=6](http://ubuntuforums.org/showpost.php?p=10907831&postcount=6)

I followed this link and inspected the files it mentions, but I don’t know how I’m to update/fix them.

---

### Post by SaturnusDJ on 2013-01-23
Okay, post the content of /etc/mdadm/mdadm.conf here.

---

### Post by heltsvensk on 2013-01-24
> **SaturnusDJ said:**
> Okay, post the content of /etc/mdadm/mdadm.conf here.

The relevant part seems to be:
```
ARRAY /dev/md0 level=raid10 num-devices=2 metadata=1.2 name=Host:0 UUID=e2443f8f:033127c2:28dca19a:08de906f
   devices=/dev/sdb1,/dev/sdc1
```

---

### Post by SaturnusDJ on 2013-01-24
Back-up that part and replace it with:
```
ARRAY /dev/md0 UUID=e2443f8f:033127c2:28dca19a:08de906f
```
Run (with sudo)
```
update-initramfs -u
```

Now look if it's fixed.

---

### Post by heltsvensk on 2013-01-24
> **SaturnusDJ said:**
> Back-up that part and replace it with:
```
ARRAY /dev/md0 UUID=e2443f8f:033127c2:28dca19a:08de906f
```
Run (with sudo)
```
update-initramfs -u
```

Now look if it's fixed.

I can definitely try that, but first I want to make sure:  If I’m turning off RAID (not sure whether the suggested change actually turns off RAID), then will my two hard drives go out of sync?  Thanks!

---

### Post by SaturnusDJ on 2013-01-24
Your OS isn't on the array right?

Then it's safe. Only if you start to mount hard disks manually (instead of md devices) things can go wrong.

If the format isn't right, mdadm just won't assemble (at least not to /dev/md0), and then you got to do it yourself like you do now or with the mdadm --assemble command.

**But...**always have a back-up.

---

### Post by heltsvensk on 2013-01-24
> **SaturnusDJ said:**
> Your OS isn't on the array right?

Then it's safe. Only if you start to mount hard disks manually (instead of md devices) things can go wrong.

If the format isn't right, mdadm just won't assemble (at least not to /dev/md0), and then you got to do it yourself like you do now or with the mdadm --assemble command.

**But...**always have a back-up.

OK, I edited /etc/mdadm/mdadm.conf accordingly, then:

```
$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-22-generic
W: mdadm: the array /dev/md/Host:0 with UUID 0de675a5:8975ffec:00b94863:cf15bbed
W: mdadm: is currently active, but it is not listed in mdadm.conf. if
W: mdadm: it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!
W: mdadm: please inspect the output of /usr/share/mdadm/mkconf, compare
W: mdadm: it to /etc/mdadm/mdadm.conf, and make the necessary changes.

```

---

### Post by SaturnusDJ on 2013-01-24
Nothing to worry about because you've got the conf back-up and OS at other partition.

Did you reboot to try?

What does ```
cat /proc/mdstat
``` have to say?

---

### Post by darkod on 2013-01-24
Why does it says md0 has different UUID? Compare the UUID of the info message and the part of mdadm.conf you posted. They don't match.

Also, the mdadm.conf you posted shows a defitnition of raid10 array but with only two devices (partitions), sdb1 and sdc1. As far as I know, raid10 needs at least 4 devices, since it means striping two mirrored arrays.

What kind of raid setup do you have exactly and with which partitions?

---

### Post by SaturnusDJ on 2013-01-25
I agree. That are some good points.

It could be a best case degraded array, but mdstat didn't even show it is degraded.

Also post:
```
mdadm --detail /dev/md*
```

---

### Post by heltsvensk on 2013-01-25
> **darkod said:**
> Why does it says md0 has different UUID? Compare the UUID of the info message and the part of mdadm.conf you posted. They don't match.

Also, the mdadm.conf you posted shows a defitnition of raid10 array but with only two devices (partitions), sdb1 and sdc1. As far as I know, raid10 needs at least 4 devices, since it means striping two mirrored arrays.

What kind of raid setup do you have exactly and with which partitions?

Yes, I saw that the UUIDs don’t match.  In /etc/mdadm/mdadm.conf, the UUID=___ clause still matches what worked before.  I don’t know anything about why the UUID reported at the console would not match.

I will reiterate:  My RAID setup worked perfectly before updating.  The setup was RAID10 with two internal hard drives.  I don’t know what the formal requirements should be, but the problem is not there.

I have a RAID10 setup with two identical hard drives (I think they’re called /dev/sdb1 and /dev/sdc1).  Before I allowed Ubuntu 12.10 to install the most recent updates, everything worked fine, but afterward, I get the hang on reboot that I mentioned in my initial post.

The problem is still exactly the same.

Thanks!

---

### Post by heltsvensk on 2013-01-25
> **SaturnusDJ said:**
> Nothing to worry about because you've got the conf back-up and OS at other partition.

Did you reboot to try?

What does ```
cat /proc/mdstat
``` have to say?

I had not rebooted before trying, but I just did and got an identical response to “$ sudo update-initramfs -u”.

```
$ cat /proc/mdstat
md127 : active (auto-read-only) raid10 sdb[0] sdc[1]
      1953382912 blocks super 1.2 256K chunks 2 far-copies [2/2] [UU]
unused devices: <none>
```

One thing I notice but don’t understand that this response mentions sdb[0], not sdb1 (not sure whether that’s a problem).

---

### Post by heltsvensk on 2013-01-25
> **SaturnusDJ said:**
> I agree. That are some good points.

It could be a best case degraded array, but mdstat didn't even show it is degraded.

Also post:
```
mdadm --detail /dev/md*
```

I don’t know what a “degraded array” means, but I do know that the drives are 2TB WD Reds less than one month old.

```
$ sudo mdadm --detail /dev/md*
mdadm: /dev/md does not appear to be an md device
/dev/md127:
        Version : 1.2
  Creation Time : Sat Jan  5 12:31:39 2013
     Raid Level : raid10
     Array Size : 1953382912 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 1953382912 (1862.89 GiB 2000.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sun Jan  6 08:31:14 2013
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : far=2
     Chunk Size : 256K

           Name : Host:0  (local to host Host)
           UUID : 0de675a5:8975ffec:00b94863:cf15bbed
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
```

---

### Post by darkod on 2013-01-25
> **heltsvensk said:**
> 
I will reiterate:  My RAID setup worked perfectly before updating.  The setup was RAID10 with two internal hard drives.  I don’t know what the formal requirements should be, but the problem is not there.


I will reiterate too. You CAN NOT have a raid10 with two disks. Look here for example, where it says raid10 or raid0+1 = minimum 4 drives.
[http://www.icc-usa.com/raid-calculator.php](http://www.icc-usa.com/raid-calculator.php)

Now, mdadm can use both disks or partitions as devices for raid, but they have to be 4 for a raid10 setup. With two disks you can either have raid0 or raid1.

I don't agree the problem is not there. The number of devices you have in your raid10 doesn't match the minimum needed and that might have bigger influence than you think.

Are you trying to say mdadm allowed you to configure a raid10 array with only two devices?

---

### Post by darkod on 2013-01-25
Degraded means disks failed, or missing. Which might have something to do in this case since there aren't 4 disks.

Whether it says sdb or sdb1 depends how you configured it. mdadm accepts both disk devices like /dev/sdb or disk partitions like /dev/sdb1. It's best to use partitions, but it seems you used the whole disks as devices. You will still have the same space since you will create sdb1 to span the whole disk, but it will be a partition as a device for the raid, as opposed to a disk.

---

### Post by heltsvensk on 2013-01-25
> **darkod said:**
> I will reiterate too. You CAN NOT have a raid10 with two disks. Look here for example, where it says raid10 or raid0+1 = minimum 4 drives.
[http://www.icc-usa.com/raid-calculator.php](http://www.icc-usa.com/raid-calculator.php)

Now, mdadm can use both disks or partitions as devices for raid, but they have to be 4 for a raid10 setup. With two disks you can either have raid0 or raid1.

I don't agree the problem is not there. The number of devices you have in your raid10 doesn't match the minimum needed and that might have bigger influence than you think.

Are you trying to say mdadm allowed you to configure a raid10 array with only two devices?

All I meant to say is that I have had two disks, each one with a single ext4 partition, and they worked fine in RAID10 earlier—maybe they weren’t supposed to work, but they did work.  The system always mounted the array at startup, and I always saw all the data in /mnt/Backup.

---

### Post by darkod on 2013-01-25
I understand, in theory I found on google that mdadm can be configured for raid10 with 2 disks but is strongly recommended not to do it. Maybe you configured it like that by mistake or on purpose having only two disks instead of four.

A raid10 array can still work with 2 disks failes, as long as the "correct" disks fail. Maybe that's what you had all this time, you were running degraded.

A raid10 is basically two raid1 arrays of 2 disks each, and then raid0 array of those two arrays. So, if one disk from raid1 array A and one disk from raid1 array B fail, the system will still work since both A and B are raid1 mirrors which can work with one disk failed.

You might need to add a parameter to grub like bootdegraded=true, and also check the /etc/fstab that in the options for /mnt/backup you don't have anything like errors=remount-ro because that will mount the array read-only if it finds an error, and it always finds an error since it's always degraded with 2 disks.

---

### Post by heltsvensk on 2013-01-25
> **darkod said:**
> I understand, in theory I found on google that mdadm can be configured for raid10 with 2 disks but is strongly recommended not to do it. Maybe you configured it like that by mistake or on purpose having only two disks instead of four.

A raid10 array can still work with 2 disks failes, as long as the "correct" disks fail. Maybe that's what you had all this time, you were running degraded.

A raid10 is basically two raid1 arrays of 2 disks each, and then raid0 array of those two arrays. So, if one disk from raid1 array A and one disk from raid1 array B fail, the system will still work since both A and B are raid1 mirrors which can work with one disk failed.

You might need to add a parameter to grub like bootdegraded=true, and also check the /etc/fstab that in the options for /mnt/backup you don't have anything like errors=remount-ro because that will mount the array read-only if it finds an error, and it always finds an error since it's always degraded with 2 disks.

If I just want to use two hard drives redundantly, which raid should I use?  Is changing the array simple?  Would I lose the data?

Thanks.

---

### Post by SaturnusDJ on 2013-01-25
You need raid1.

It might be possible you are running raid1 already.
Ways to find out:
- Disconnect one drive and see if the array still 'assembles.' If yes: raid1.
- Check the size of a single disk. If 2TB: raid1.

But...even if you run raid1, it is not fool proof to do a (re)create and overwrite the metadata with raid1 superblocks because the parameters (layout/chuck) may differ.

I suggest making a **back-up** of the data, for science check if a (re)create works and tell us. ;) If it doesn't zero the superblocks and build a clean raid1 and restore the back-up.


Oh and one more thing: If you love your data, read more about what you are doing.

---

### Post by darkod on 2013-01-25
Yeah, a redundant with 2 disks would be raid1. But you have to take into account that it will halve the usable capacity. Depending how much capacity are you using now, with two disks in a mirror you will have much less.

I wouldn't start unplugging disks yet, if you have raid0 i don't know how it would affect the array since raid0 can't work with only one disk. Usually plugging it back in should make it start again, but if you have important data, I wouldn't risk it.

I don't know of a way to convert to raid1 without destrying the data, it will be a whole new array. I would consider copying the data somewhere temporarily, making a new raid1 mdadm array, and copying the data back.

That should sort out all your worries. :)

---

### Post by SaturnusDJ on 2013-01-25
A non-hot unplug is safe. Array will become inactive, not mountable. When the device is plugged back in, it's normal again.

---

### Post by heltsvensk on 2013-01-25
> **darkod said:**
> Yeah, a redundant with 2 disks would be raid1. But you have to take into account that it will halve the usable capacity. Depending how much capacity are you using now, with two disks in a mirror you will have much less.

I wouldn't start unplugging disks yet, if you have raid0 i don't know how it would affect the array since raid0 can't work with only one disk. Usually plugging it back in should make it start again, but if you have important data, I wouldn't risk it.

I don't know of a way to convert to raid1 without destrying the data, it will be a whole new array. I would consider copying the data somewhere temporarily, making a new raid1 mdadm array, and copying the data back.

That should sort out all your worries. :)

Is there a way I can disable the RAID, mount just one of the two redundant disks, then create a new RAID that will re-synchronize the second disk to the first?

---

### Post by darkod on 2013-01-26
In theory yes, but the issue is that you don't seem to have any redundancy left.

If my assumption about the raid10 array is correct, you are already running degraded without 2 disks out of 4 which is the maximum you can lose, in the best case. The array will not be usable if you remove a third disk of four. So you can't copy anything from it.

If you were running on a single disk for example and bought a new one. You will use the new disk to create raid1 array with one disk missing (you can do that), copy everything to the array, and then adding the old disk to the array and let it sync with the one already there.

If you want, you can try unplugging one disk and see if the array assembles with only one. That will show you if it can run until you prepare the other disk for raid1 and start copying. Personally, I don't think it will let you.

---

### Post by heltsvensk on 2013-01-26
> **darkod said:**
> In theory yes, but the issue is that you don't seem to have any redundancy left.

If my assumption about the raid10 array is correct, you are already running degraded without 2 disks out of 4 which is the maximum you can lose, in the best case. The array will not be usable if you remove a third disk of four. So you can't copy anything from it.

If you were running on a single disk for example and bought a new one. You will use the new disk to create raid1 array with one disk missing (you can do that), copy everything to the array, and then adding the old disk to the array and let it sync with the one already there.

If you want, you can try unplugging one disk and see if the array assembles with only one. That will show you if it can run until you prepare the other disk for raid1 and start copying. Personally, I don't think it will let you.

Let’s go on the theory that the problem is in only the software (i.e., not the hardware), given that the problem arose after a software update and my console quotations (earlier posts) show both disks still recognized (I think).  Under that assumption, how do I disassociated the two disks currently in the level-10 RAID, remove/cancel/stop that RAID, create a new level-1 RAID, and put the disks into it?

If that’s too much to answer, then my main question concerns disassociating the disks currently in the RAID because I think I can figure out how to create a new RAID once I have the disks separated.

---

### Post by darkod on 2013-01-26
OK, so, your disks currently in the raid10 are sdb and sdc. First power down the computer and disconnect sdc. Then boot without it and see if you can access the data on the array or not.

That is the only way I can think of to check if it will work without one disk. Saturnus says it's safe since with one disk if it can not work the array won't even assemble, so when you connect the second later it will be normal again.

So, first check if the data is accessible with only one disk. If it is, we can talk later about the steps needed. If it's not accessible, you can't do it without moving the data somewhere temporarily.

We never said the problem is in the hardware. This is software raid and the issue is in software, but that still doesn't mean you can access the data with only one disk. In a raid1 array you can access data with only one disk, but you have raid10, not raid1.

---

### Post by heltsvensk on 2013-01-27
> **darkod said:**
> OK, so, your disks currently in the raid10 are sdb and sdc. First power down the computer and disconnect sdc. Then boot without it and see if you can access the data on the array or not.

That is the only way I can think of to check if it will work without one disk. Saturnus says it's safe since with one disk if it can not work the array won't even assemble, so when you connect the second later it will be normal again.

So, first check if the data is accessible with only one disk. If it is, we can talk later about the steps needed. If it's not accessible, you can't do it without moving the data somewhere temporarily.

We never said the problem is in the hardware. This is software raid and the issue is in software, but that still doesn't mean you can access the data with only one disk. In a raid1 array you can access data with only one disk, but you have raid10, not raid1.

I’d rather not mess with the hardware, so I thought I would just sacrifice all my backup data and start over.  I commented-out the entries for the RAID in “/etc/fstab” and “/etc/mdadm/mdadm.conf”, then tried to stop the RAID (“mdadm --stop /dev/md0” and “mdadm --stop /dev/md127”).  I thought I’d succeeded.  I restarted the computer, but even now, GParted complains about some “/dev/md/0” [sic] and pretends to recognize some “/dev/md127”, while “fdisk -l” talks about “/dev/md127”.  Every time I restart, I have to “mdadm --stop /dev/md127”, even though it’s commented-out in “/etc/mdadm/mdadm.conf”.  And even after stopping the array, when I attempt “sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1”, I get some error about /dev/sdb1 being busy.  As far as I know, neither /dev/sdb1 nor /dev/sdc1 are mounted anywhere.

Any suggestions about where I can find good information about starting from ground zero?

---

### Post by darkod on 2013-01-27
Hmm, I guess it would go something like:
1. Unmount the array (it might not be mounted right now since you edited fstab):
sudo umount /mnt/backup

2. Stop the md device:
sudo mdadm --stop /dev/mdX (try with both 0 and 127)

3. Delete the ARRAY definition from mdadm.conf.

4. Zero the superblock on all partitions that were part of any array. This is very important since if the superblock is recognized they won't be used in a new array:
sudo mdadm --zero-superblock /dev/sdaX (for /dev/sdbX too)

After that you should be able to use mdadm --create since the partitions(disks) will be considered as new disks never used in your array.

Note that the above will delete all data, but you already said you want to sacrifice that.

---

### Post by heltsvensk on 2013-01-27
Looks like step #4 (zeroing the superblocks) is what I&#8217;d forgotten.  Thanks for the help.

---

### Post by heltsvensk on 2013-01-27
> **darkod said:**
> Hmm, I guess it would go something like:
1. Unmount the array (it might not be mounted right now since you edited fstab):
sudo umount /mnt/backup

2. Stop the md device:
sudo mdadm --stop /dev/mdX (try with both 0 and 127)

3. Delete the ARRAY definition from mdadm.conf.

4. Zero the superblock on all partitions that were part of any array. This is very important since if the superblock is recognized they won't be used in a new array:
sudo mdadm --zero-superblock /dev/sdaX (for /dev/sdbX too)

After that you should be able to use mdadm --create since the partitions(disks) will be considered as new disks never used in your array.

Note that the above will delete all data, but you already said you want to sacrifice that.

I tried this procedure, but something is really screwed up.  I unmounted Backup (it wasn’t mounted), tried to stop both md0 and md127, deleted the entry from mdadm.conf and from fstab, and restarted the machine.  When I open GParted, it complains about “/dev/md/0” and shows “/dev/md127” as an unformatted device.  Then I checked “sudo mdadm --detail /dev/md127”, and it’s still reporting a RAID, even after I stopped the software device, deleted it, zeroed the superblock, and restarted.

Now it’s the second time I’ve had this identical situation; after the first time, I had spent another several hours letting mdadm recreate and synchronize the array (afterward I created an ext4 file system on the software device).  At first, the array had mounted, but then once I restarted, I got back to the same errors I had in the original posts (first, device not ready, then when trying to mount from the terminal after launch, the terminal complains about a lack of file system, even though I had successfully mounted the device before the restart).  So I’ve come back in a circle.

I don’t care about data right now—I just want to make these hard drives usable.  Any thoughts?  Anybody know of any accurate tutorials on how to start an mdadm level-1 software RAID?

Thanks.

---

### Post by tenmoi on 2013-01-28
> **heltsvensk said:**
> I tried this procedure, but something is really screwed up.  I unmounted Backup (it wasn&#8217;t mounted), tried to stop both md0 and md127, deleted the entry from mdadm.conf and from fstab, and restarted the machine.  When I open GParted, it complains about &#8220;/dev/md/0&#8221; and shows &#8220;/dev/md127&#8221; as an unformatted device.  Then I checked &#8220;sudo mdadm --detail /dev/md127&#8221;, and it&#8217;s still reporting a RAID, even after I stopped the software device, deleted it, zeroed the superblock, and restarted.

Now it&#8217;s the second time I&#8217;ve had this identical situation; after the first time, I had spent another several hours letting mdadm recreate and synchronize the array (afterward I created an ext4 file system on the software device).  At first, the array had mounted, but then once I restarted, I got back to the same errors I had in the original posts (first, device not ready, then when trying to mount from the terminal after launch, the terminal complains about a lack of file system, even though I had successfully mounted the device before the restart).  So I&#8217;ve come back in a circle.

**I don&#8217;t care about data right now**&#8212;I just want to make these hard drives usable.  Any thoughts?  Anybody know of any accurate tutorials on how to start an mdadm level-1 software RAID?

Thanks.

Hi,

This is what would I usually do in a virtualised environment. (Because I don't own RAID hardware)

1. Download desktop ubuntu 12.10, which doesn't have mdadm. And boot your machine with the live CD.
2. sudo fdisk /dev/sdb (From what I have read, I figure that you have two hard disks for RAID, namely sdb and sdc. If not, replace /dev/sdb accordingly)
3. Enter d to delete partitions. Repeat entering d until fdisk tells you that there's no more partitions to delete.
4. Enter n and choose your partition type: p or e (two options: primary and extended)
5. fdisk asks you to decide on the number of partitions. In your case, I suggest you enter 1, which means one partition for the whole disk.
6. Pressing your enter key twice to accept the default values.
7. Press the t key.
8. Enter 83 to change your partition id to linux's.
9. Enter w.
Done.
10.Repeat these steps for your second disk.
11. sudo fdisk -l. If you see after /dev/sdb1 the words, ' id 83', you know that you've got rid of RAID.

12. Reboot and remove the live CD.
13. Recreate your RAID 1 array. (To be sure you should apt-get remove --purge mdadm. Then reinstall mdadm)
15. mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1.
16. You can now use gparted or fisk to format md0. I often use fisk to format and mkfs to create a file system. I just don't trust gparted and .... ubuntu 12.10's mdadm, which even Canonical doesn't want us to use.

Cheers,

---

### Post by darkod on 2013-01-28
Why do you restart? Just create the new array. I'm not sure if the initramfs is messing it up for you, having remembered the md devices.

After stopping the arrays and confirming nothing is mounted, you can try something like:
sudo update-initramfs -u

I don't have any tutorials about mdadm handy right now, but this is not about creating the new array, it's about getting rid of the old one. At least that's how it seems to me.

Also, I am surprised Gparted is complaining about md0 as you say. Gparted is Gparted, it will open whatever disk you tell it to. If you want to open /dev/sda with Gparted, why would it complain about any md device?

I think you might have some kind of mess, but it's not easy to figure it out remotely. Make sure to check regularly what is mounted with:
df -h

Also check mdadm status with:
cat /proc/mdstat

Does the above command say you still have arrays running after you have removed them from mdadm.conf and rebooted?

EDIT PS: @tenmoi, I respect your choice for a partitioning tool, but I have seen some threads about fdisk not being very good at partitioning in some cases. I would say parted or cfdisk are much preferred. I clearly remember a case where fdisk created partitions not equal which messed up a raid array for that person. It was some weird case.

---

### Post by tenmoi on 2013-01-28
Hi Helt,

I have been running ubuntu server 12.04 in RAID 0 for some time now on Virtualbox. I have never had any problem even though I did notice that /dev/md0 changed to /dev/md127 after I rebooted.

So please note that after a reboot, you don't deal with MR md0 any more. His name is now, and forever after, MR **md127**:p
Do you still miss your old little Mr md0. Do this:
mdadm -S /dev/md127
mdadm --assemble --scan
fdisk -l

and go meet your old friend.

Cheers,

@darkrod,

Gparted just acts weirdly sometimes and it is slow. So as long as I don't have to deal with GPT disks, I stick with fdisk.

---

