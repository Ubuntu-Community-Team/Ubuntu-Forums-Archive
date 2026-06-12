---
title: "Error while Mounting /etc/fstab"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Mrs Twaddle on 2010-04-29
I just ugraded from karmic, and it all went without a hitch. Except now when i boot i get...
Error while mounting /etc/fstab
press s to skip or m for manual recovery.

Pressing s works and i have a working machine, but i would like to fix this. Not tried the manual recovery yet as i have no idea about fstab and don't want to break it.

---

### Post by kbielefe on 2010-04-29
Can you attach your /etc/fstab file so I can take a look?

---

### Post by swhit on 2010-04-29
I get the same error after updating 9.10 to 10.4. I'm guessing that it has to do with my editing the fstab file previously to automount a shared folder (I use ubuntu as a vm on my mac). Like the original poster, I press the S key to skip the mount and end up with a perfectly functioning vm - including a mounted shared folder!

below is the edited fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2cb9f201-381a-4bc3-a19d-05ba78923f8f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bef18a57-2b44-424b-adde-28de7ea0e427 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
Host /home/username/Desktop/Mac_host	vboxsf	rw,uid=1000,gid=1000	0	0

---

### Post by Mrs Twaddle on 2010-04-30
here is mine

ed# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ba904bdc-c8f9-4441-9d65-2490aaad8e92 /               ext3    defaults,errors=remount-ro,relatime 0       0
# /dev/sda5
UUID=6ae43e89-4c5b-42ec-8fa6-68be1456bef1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by kansasnoob on 2010-04-30
> **Mrs Twaddle said:**
> I just ugraded from karmic, and it all went without a hitch. Except now when i boot i get...
Error while mounting /etc/fstab
press s to skip or m for manual recovery.

Pressing s works and i have a working machine, but i would like to fix this. Not tried the manual recovery yet as i have no idea about fstab and don't want to break it.

I've been getting that with fresh install sometimes also. It's not consistent but I've found that if I start in recovery mode then choose to resume normal boot it's OK for quite a while.

I suspect something related to ureadahead but I'm not sure. I'm going to give the new "proposed" kernel a try-out later today :)

---

### Post by myharries on 2010-04-30
I also got the same error, after I upgraded, unfortunately I'm an absolute beginner with Ubuntu.
There was an error in the file at first, where sde1 was not mounted, and sda1 was mounted ( a second time) in sdb1 position.
Also please note, that the HDD's are not in a raid system, the name is a carry over from a previous setup
 
Could someone knowledgable give me some direction on how to stop this error? Thanks
 
-----------------------------------------------------------
 
/etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=e3dcc4fd-9d63-471f-8933-f12fa66eafd4 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=9b6ff94b-0251-45ac-a167-8e5cb19fc49b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /var/raid01 ext3 defaults,errors=remount-ro 0 2
/dev/sdc1 /var/raid02 ext3 defaults,errors=remount-ro 0 2
/dev/sdd1 /var/raid03 ext3 defaults,errors=remount-ro 0 2
/dev/sde1 /var/raid04 ext3 defaults,errors=remount-ro 0 2

---

### Post by ram130 on 2010-05-01
same here..really annoying problem. No one can help?

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=8e7cae7b-970b-4f7e-8d8c-410f3613877d /               ext4    relatime,errors=remount-ro 0       1
   sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by dmdevotee on 2010-05-01
i have this problem too.

for me it seems like the hard drives are not in the same /dev/sd** at every boot.

i have to change the fstab every time, before looking the mstab when mounted, to avoid this problem. it's very annoying...

this didn't happened with 9.10 to me, so i think it's a bug

edit: now i tried to reboot with a webcam unplugged, and the fstab doesn't work with a hard drive now....

edit: and now i tried to reboot with a webcam PLUGGED, and the fstab works...

---

### Post by Mrs Twaddle on 2010-05-01
this is really slowing down my pc to the point i can't be bothered waiting for it to start up.

---

### Post by overkillm on 2010-05-01
Just installed 10.4 myself and had the same problem.  My sda and sdb were switched when I rebooted.  I edited my fstab to use UUIDs instead of /dev/sd* and it seems to be working.

To get past the "Error while mounting /etc/fstab" screen, press M for manual edit.  That will get you to a command prompt.  From there, you can edit the fstab by typing: 

```
sudo nano /etc/fstab
```

Then, just change the /dev/sd* entries at the beginning of each line with the correct entries for those mount points.  For instance, since my sda and sdb were swapped, I just changed all the /dev/sda* entries to /dev/sdb* and vice versa.  Save your changes, exit nano, and press Ctrl+D to exit the command prompt and attempt to boot again.

Once you've successfully booted, try replacing the /dev/sd* at the beginning of each line in your /etc/fstab file with UUID= followed by the UUID of the drive that you want at that mount point.  To get a list of UUIDs for each drive, enter the following command in a terminal session: 

```
ls /dev/disk/by-uuid -l
```

The UUID is a unique identifier that will point to that particular drive regardless of which /dev/sd* entry it inhabits.  Make sure you use the correct UUIDs in your fstab or the drives will still mount at the wrong point.

Hope that helps.

---

### Post by Metallinut on 2010-05-03
I had/have the same issue. Looks like it's a problem trying to mount the VirtualBox shared folder (from the host) before the vbox service is running. From what it sounds like, on previous Ubuntu versions it would also fail at fstab, but would not prevent booting. Then I guess at some point later it would mount the VBox share.

Now with 10.04 it appears to halt the boot process. It looks like you can mount the VBox share later, by adding a line to /etc/init.d/rc.local

I added this line:
```
mount -t vboxsf -o rw,uid=1000,gid=1000 <sharename> </path/to/mountpoint>
```
directly under this line in /etc/init.d/rc.local:
```
### END INIT INFO
```

I also took the line out of /etc/fstab that mounts the VBox share. 

Rebooted...Ubuntu came up without the mount error, and my VBox share mounted no problems, with the correct permissions.

Hope this helps! :D

---

### Post by Mrs Twaddle on 2010-05-03
> **overkillm said:**
> Just installed 10.4 myself and had the same problem.  My sda and sdb were switched when I rebooted.  I edited my fstab to use UUIDs instead of /dev/sd* and it seems to be working.

To get past the "Error while mounting /etc/fstab" screen, press M for manual edit.  That will get you to a command prompt.  From there, you can edit the fstab by typing: 

```
sudo nano /etc/fstab
```

Then, just change the /dev/sd* entries at the beginning of each line with the correct entries for those mount points.  For instance, since my sda and sdb were swapped, I just changed all the /dev/sda* entries to /dev/sdb* and vice versa.  Save your changes, exit nano, and press Ctrl+D to exit the command prompt and attempt to boot again.

Once you've successfully booted, try replacing the /dev/sd* at the beginning of each line in your /etc/fstab file with UUID= followed by the UUID of the drive that you want at that mount point.  To get a list of UUIDs for each drive, enter the following command in a terminal session: 

```
ls /dev/disk/by-uuid -l
```

The UUID is a unique identifier that will point to that particular drive regardless of which /dev/sd* entry it inhabits.  Make sure you use the correct UUIDs in your fstab or the drives will still mount at the wrong point.

Hope that helps.
I on;y have the one drive, so i know my haven't been switched.
I did try the UUID anyway, and it made no difference, still said can't mount fstab:


I also don't run a virtual box.

A further clue to the problem might be that it can't mount fstab: (which is a folder in /etc) the folder itself is empty.

---

### Post by Niels R on 2010-05-04
I upgraded to 10.04 using update-manager and I have the same problem now except my bootscreen says:

```
Error while mounting mount
```

I tried commenting the NTFS partitions in fstab and checked the UUIDs, but it didn't help.

I used ntfs-config in 9.10 to automatically mount the NTFS drives. I dual boot ubuntu and windows 7 with a shared NTFS partition. 

This is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda2 :
UUID=60a2207f-905d-410d-9e32-36ca89e79bb3       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sda4 :
UUID=51B9240372D1A03C   /media/Storage  ntfs-3g defaults,locale=en_US.utf8      0       0
#Entry for /dev/sda1 :
UUID=7A24652B2464EB97   /media/sda1     ntfs-3g defaults,locale=en_US.utf8      0       0
#Entry for /dev/sda3 :
UUID=01a31cc3-e426-451d-82e9-870166ebe371       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8   0       0
sudo    mount   /dev/shm        0       0       0
sudo    mount   |       grep    0       0

```

During the update I was prompted to install a new version of GRUB and I picked the package maintainers version since the old GRUB was a beta version. After skipping the mount during boot it starts normal and the NTFS disks are mounted like they should.

---

### Post by swhit on 2010-05-06
Thanks Metallinut! Your suggestion worked perfectly for me (post #11).

kind regards.

---

### Post by dino99 on 2010-05-06
i never have to tweak fstab on my system, i'm too lazy, i use mountmanager, much more user friendly  ):P

---

### Post by quadproc on 2010-05-06
> **dmdevotee said:**
> i have this problem too.

for me it seems like the hard drives are not in the same /dev/sd** at every boot.

That is very possible.  The /dev/xxx identifiers are assigned by the operating system and not by the hardware.  As you plug or unplug hardware, the identifiers will change.
> 
i have to change the fstab every time, before looking the mstab when mounted, to avoid this problem. it's very annoying...
I suggest using the UUID in the fstab file.  The whole UUID concept was invented to avoid the variable device ID problem.  Here is a sample from my fstab file:
```
UUID=e61d892a-0341-4f99-a87b-c9345d9f9eb1 /home        ext3    relatime,errors=remount-ro    0    2
```> 

this didn't happened with 9.10 to me, so i think it's a bug

quadproc

edit: now i tried to reboot with a webcam unplugged, and the fstab doesn't work with a hard drive now....

edit: and now i tried to reboot with a webcam PLUGGED, and the fstab works...

---

### Post by arnebaier on 2010-05-08
Slightly different in my installation...

I am using 5 different external USB hard disk drives for backup purposes and have been including them in 9.10 by their UUIDs in /etc/fstab:

[PHP]UUID=06eef8d6-b9d7-49c9-b7be-48a38e691c48 /media/backupsmall ext4 defaults,users 0 2
UUID=9110edec-f3e1-4f75-9c47-da2c190e8de4 /media/backupsmall ext4 
[...][/PHP]

When connecting one of the HDDs, karmic mounted it on /media/backupsmall and I could run my rsync backup script.

These drives are never connected at boot time!! Which was ignored by karmic but isn't ignored anymore by lucid lynx.

Can I somehow override the "check-if-all-drives-are-available" feature which seems to be used here?

---

### Post by zenon222 on 2010-05-16
I am in precisely the same situation as arnebaier.

Essentially, in v10.04 if there is an entry in /etc/fstab and the drive is not present at boot time the system will hang until it is found.

I verified this by selecting "M", turned on my eSATA drive, entered the command "mount -a", ctrl+?? to return to boot sequence.  Ubuntu proceeded to boot smoothly.

If there is an fstab command that tells ubuntu "ignore if not present" I would sure like to know it.

---

### Post by arnebaier on 2010-05-16
I meanwhile managed to have a really fast booting system. First thing I did is to remove the hard disks identified by their UUIDs from the /etc/fstab. Then I modified the backup script to dynamically mount every known partition connected at run-time. 

This solved the "Press M" issue.

But I still had a 30 seconds lasting hang after entering user credentials.

So I removed the /dev/fd0 entry from the /etc/fstab aaaaand....*drums*...the time between pressng enter and a fully working desktop was 2 seconds only.

I was so happy.

After next re-boot I had the 30 seonds delay, again...why?

---

### Post by frantid on 2010-05-16
you guys could try to add the "noauto" option to those entries, that does mean you will have to manually mount them.

---

