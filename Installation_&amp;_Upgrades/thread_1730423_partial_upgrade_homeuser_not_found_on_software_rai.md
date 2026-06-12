---
title: "partial upgrade /home/user not found on software raid0"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2011-04-16
I have Ubuntu Studio Lucid 64 (pre-empt kernel) on a software raid 0 partition (md0).  My /home is supposed to be on another raid 0 partition (md1).

I believe that in my tiredness I may have ran a partial upgrade which didn't succeed in loading the latest kernel -30, so I am still on -28.
I couldn't boot into my system anymore, so I tried recovery, and chose to repair broken pkgs, (also apt-get clean since I also had a message that my /boot partition was 100% full- which is ok now).
What I can do at this point is to boot into a blank desktop with no access to programs or my files etc....

I get
```
ERROR:could not update ICEauthority file /home/user.ICEauthority

nautilus could not create the following required folders
/home/user/Desktop
/home/user/.nautilus
pls. create therse folders or set the permissions such that nautilus can create them.
```

I worked from TTY console or recovery console and attempted various recommended chown but get message that/home/usr is not found:
```
"/home/user" "file does not exist" 
``` 

```
cat /etc/fstab
```
lists swap files only no / or /home ...Is this normal? If not how can I still be accessing / then? Other Ubuntu versions on same and other computers seem to have / and /home partitions in fstab. Could a partial upgrade that didn't get fully installed mess up fstab? 

From terminal and cding to /home and typing:

```
ls -la 
shows 2 lines with permissions etc ending in      .
                                                  ..
but NO lines showing                              lost+found
                                                  user
```


here's an example of a working OS also on a md0 partition on another computer:

```
user@computer:/home$ ls -la
total 28
drwxr-xr-x  4 root         root          4096 2008-10-25 07:13 .
drwxr-xr-x 22 root         root          4096 2011-04-05 12:48 ..
drwx------  2 root         root         16384 2008-10-25 06:38 lost+found
drwxr-xr-x 69 user         user         4096 2011-04-15 21:16  user
```


Some posts suggest to remove and re-install nautilus but I beleive I need to fix /home first...For all I know it may have been just a partial update-I was so tired.  I did a couple of other things that had changed the permissions, but I didn't rm anything for certain!
Are my home contents lost?
Pls. re-installating the whole distribution is NOT an option and re-installing home will be tricky with software raid....any solutions???

---

### Post by MrEgg on 2011-04-16
You say your fstab doesn't show your raid - that's your problem.

It should have an entry like this :
```
/dev/md1     /home     ext4     defaults     0  0
```
Note: adjust the filesystem type if it isn't ext4

---

### Post by streamsanddragonflies on 2011-04-16
> It should have an entry like this :
Code:

/dev/md1     /home     ext4     defaults     0  0

MrEgg, love the name BTW, so my fstab is messed up and my home contents may still be there? Thankyou!! I'm feeling better already...I completely forgot that one has to get mdam to boot, of course. Now I looked at another Ubuntu on my older computer which has raid 0 /home as well, and sure enough md0 /home is in fstab. In that case shouldn't I add the UUID, relatime as well then? Also Isn't it nessary to add / in fstab as well (/ is md0, /home is md1)?

Note: I'm attemping this only tommorow when I'm alert!

---

### Post by MrEgg on 2011-04-16
I used to create my raids from scratch w/ mdadm. But once I moved to 10.10, I found things to be much easier - although maybe less geeky.

If you want to re-construct your raid manually, it's indeed much safer to use UUIDs than /dev/sdx. 

On 10.10, you want to open Disk Utility (DU) with which you can create, remove, mount, umounted and check your raids, even add and remove elements from and to it. Really cool and easy. I suppose you'd have DU on Studio as well.

You said you originally had / on md0 and /home on md1. If none of your raids are mounted and yet you still have Studio running, you want to check where it's installed.

Check /proc/partitions and /proc/mounts.

At this point, if the only thing that got screwed up was an update, I don't see why your raid data should be lost.

As a side note, in the future do backup your / using dd so you can easily restore it as it was before-it-got-messed-up!!

---

### Post by streamsanddragonflies on 2011-04-17
ok I'm back! Pls. bear in mind that I had to copy this by hand from my screen and I ommitted some less relevant info..

```
cat /proc/partitions:

9    1    70711168   md1
9    0    45212544   md0
```

my /home and / raid partitions are both still there!
For example:

```
sudo blkid
...
/dev/md1: label "U Studio L Home" UUID:63626aef-46d0-49cc-83ei-7810029217d2 Type 
ext 4
...
```

is there among other devices but when I did 

cat /proc/mounts  /home is missing!

I have:

```
cat /proc/mounts
rootfs / rootfs rw 0  0
/dev/disk by UUID........  / ext4  rw, relatime, barrier=1, stripe=32, data=ordered 0 0
....
/dev/sde2/boot ext3....
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc_misc rw, nosuid, no dev, no exec,relatime 0 0
```

even cat /proc/mdstat lists both md0 /  and md1 /home
and I was told to sudo mdadm --detail/dev/md1
and md1 shows working fine and the 2 devices that make the stipe set are listed correctly...

So now I have to figure out how to add /home to cat /proc/mounts  properly....just remember DU, will it fix the mount ommission automatically?

---

### Post by MrEgg on 2011-04-17
Fire up Disk Utility from System - Administration. Check if you see your raids in the left column. Select your /home raid. In the main screen, you'll find a button to start and mount it.

Otherwise, add in /etc/fstab the entry mentioned earlier.

Cheers

---

### Post by streamsanddragonflies on 2011-04-17
Hello again!

Couldn't use the Disk Utility; the only option was to:
```
start the disk array.
Not enough components to start the array.
```

In order to use the DU I had to work from my non raid Ubuntu which I can access and I even installed mdadm in case it was needed.

Spent hours trying to edit fstab of my U Studio from TTY or recovery, using the exact specifics and then, variations on what you wrote.  I used nano again (including trying to add the UUID since the rest of devices in my fstab are listed by UUID). Once I'd reboot, I still get the ICEauthority and same other messages.  I also tried to edit etc/mtab using same commands as for fstab but to no avail. 

I can't edit sudo nano /proc/mount using:
/dev/md1 /home ext4 rw,relatime, data=ordered 0 0
it gives me  error: invalid arguement!

I noticed that my /proc/mounts has the word "none"- before most listed lines (I believe that's the word). Here it is on my raid Hardy installation, which I would refer to  for comparison:
```

none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
```

thus these lines are borrowed from my Hardy system as an example.

I also noticed in the Hardy installation, variations on lines for /home such as relatime and 0 2 instead of: defaults 0 0. Also could it maybe be "automount" instead of defaults for an array? Trying to find the answer & I am exhausted and ready to wipe out my /home if needed at this point. I seem to be turning in circles...

---

### Post by MrEgg on 2011-04-17
Okay - don't panic. You're trying to edit the wrong files.

Please post the full results of :
```
sudo fdisk -l
df -h
cat /proc/partitions
cat /proc/mounts
cat /etc/fstab
cat /etc/mdadm/mdadm.conf
sudo dpkg --list | grep mdadm
```

Also, can you confirm that your raid was of type 0 ?

---

### Post by streamsanddragonflies on 2011-04-17
Mr. Egg, please stay connected with my thread, it feels like a lifeline right now! I have to be out the whole day and will try again late tonight if I can.  Is there a way to send the results to my email or a USB key, even though nautilus isn't operable? ...If not, I'll write it down manually, but I'm more akin to make an error. (Note: I don't have a printer).

ok, will remain hopeful then!

NOTE: I forgot that I already have the following:

```
sudo mdadm --detail/dev/md1 
version: 00.90
creation time:  ....
raid level: raid 0
Array size: 77.44 Gig  72.41 Gig
raid device: 2
total devices: 2 
preferred minor: 1
superblock is persistant
failed devices: 0
state: clean
UUID: 10ab42e0:8df64531:2e110cb:b1cc6cd8
events: 0.1
/dev/sdd7
/dev/sde6
```

One or 2 lines that seemed irrelevant were ommited.  Yes I definitely had built raid 0 (md0) never tried any other raid level.

```
cat /proc/partitions:

9    1    70711168   md1
9    0    45212544   md0
```

This one I had also posted earlier and has no errors.  Ok the rest will be when I return!

---

### Post by MrEgg on 2011-04-18
> **streamsanddragonflies said:**
> Is there a way to send the results to my email or a USB key, even though nautilus isn't operable?

Yes. To send the result of command, proceed like this in Terminal:

```
sudo fdisk -l > fdisk.txt
```

This will send the output of the command to /home/username/fdisk.txt file, which you can then use as you wish. After you plug in a USB key, it will appear under /media. Still in terminal, you go
```
ls -l /media
```
and find the relevant directory. Then you copy the file to the relevant directory :
```
cp /home/username/fdisk.txt /media/relevantdirectory
```



If you PM me, I can give you my email address and Skype username to help you further with your problem.

---

### Post by streamsanddragonflies on 2011-04-18
Mr. Egg, looks like it won't be necessary; I don't why the first time I rebooted with the following, it didn't succeed at first:

```
cat /etc/fstab
 #UUID=63626aef-46d0-49cc-83e1-7810029217d2
 **/dev/md1 /home ext4 defaults 0 2**
 #UUID=f1a032cc-ec4c-4634-a05f-504ec83a87d5 /media/Ubuntu Multimedi
 ext4 users 0 0
 #UUID=f1a032cc-ec4c-4634-a05f-504ec83a87d5 /media/Ubuntu Multimedi
 ext4 users 0 0
 UUID=25494036-6939-4437-ad67-831238ff03cf swap swap sw 0 0
 UUID=a8263a1a-1b02-4535-a480-3509ac0d1d8b swap swap sw 0 0
 UUID=b628db22-8d88-437e-b09d-0aebd24e4036 /boot ext3 defaults 0 2
 UUID=0465eb55-7de7-4547-bd9d-ccd7fa350185 swap swap sw 0 0
```




 but when I rebooted again later and expected to have to use the TTY to output fstab etc...My /home was back!!!  Note that I left the /home UUID commented out, rather than delete it. I had attempted to use the UUID earlier. I had tried /dev/md1 /home ext4  defaults 0 0 and /dev/md1 /home ext4  relatime 0 0 and finally /dev/md1 /home ext4  defaults  0  2.  The other #/media/Ubuntu Multimedia partition is the partition for which I had tried to change permissions with Mount Manager gui program. I am pretty sure that I **didn't** touch my /home with that program.  That data partition is now writable, as was my intention, perhaps the Mount manager chmod it after all! I have changed this partition's label as well to UbuntuMultimedia while in my Ubuntu generic distro.

 While in recovery mode I remember that I had tried the following :

```
chmod 1777 /tmp 
``` suggested in another thread.  Hopefully chmoding my temp doesn't create other problems down the road. Here is what my /proc/mount looks like now:
```

cat /proc/mounts
 rootfs / rootfs rw 0 0
 none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
 none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
 none /dev devtmpfs rw,relatime,size=2019908k,nr_inodes=504977,mode=755 0 0
 none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
 /dev/disk/by-uuid/5e77bf7c-3152-45f3-a2bf-b6a321538677 / ext4
 rw,relatime,barrier=1,stripe=32,data=ordered 0 0
 none /sys/fs/fuse/connections fusectl rw,relatime 0 0
 none /sys/kernel/debug debugfs rw,relatime 0 0
 none /sys/kernel/security securityfs rw,relatime 0 0
 none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
 none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
 none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
 none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
 **/dev/md1 /home ext4 rw,relatime,barrier=1,stripe=32,data=ordered 0 0**
 /dev/sde2 /boot ext3 rw,relatime,errors=continue,data=ordered 0 0
 binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc
 rw,nosuid,nodev,noexec,relatime 0 0
 [B]gvfs-fuse-daemon /home/myusername/.gvfs fuse.gvfs-fuse-daemon
 rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0[/B]
 /dev/sdb9 /media/UbuntuMiscellans ext4
 rw,nosuid,nodev,relatime,barrier=1,data=ordered 0 0
 /dev/sdb8 /media/MULTIMEDIA fuseblk
 rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096
 0 0
 /dev/sdb2 /media/UbuntuMultimedia ext4
 rw,nosuid,nodev,relatime,barrier=1,data=ordered 0 0
```

As soon as I was back with /home/my username and nautilus working again, the message with /boot being full 100% came up so I followed instructions and checked my linux-images in synaptic:  It confirmed that last kernel had installed in /boot but failed due to dependancies:

from synaptic error messages:

 ```
E: linux-image-2.6.32-30-preempt: subprocess installed
 post-installation script returned error exit status 2
 E: linux-image-preempt: dependency problems - leaving unconfigured
 E: linux-preempt: dependency problems - leaving unconfigured

 Udate manager: package installation failure:
 E: linux-image-2.6.32-30-preempt: subprocess installed
 post-installation script returned error exit status 2
 E: linux-image-preempt: dependency problems - leaving unconfigured
 E: linux-preempt: dependency problems - leaving unconfigured

```

I then I removed linux-image-2.6.32-30 & 2.6.32-21 & 2.6.32-25 pre-empt kernels (I marked the latter 2 for complete removal) and did:

```
sudo update-grub
```

I rebooted a couple of times since and my /boot isn't full anymore but now I am concerned about the latest pre-empt kernel 2.6.32-30.  Should I check with bug tracker now, cause eventually I will need to update to the latest kernel?  It seems that most likely that that last update or partial upgrade is what messed up my /proc/mount...Also changing another partition's permissions at the same reboot probably made it worse!!

Also I still  want to make sure I back things up now, but I have will have to wait a couple of days now as other things are taking precedence and at least I can breathe a sigh of relief!  So if you want to still follow up, I would like to find out how to properly bk my /home and / once and for all!  It should get done soon since I have such a complicated set-up and still quite a gap in understanding linux's workings!!! I should mark this thread as solved, in the meantime. And many thanks!! for the help and follow up!

---

### Post by MrEgg on 2011-04-19
Excellent! I'm glad to hear things got back as they should.

Just so you understand, /proc is actually a virtual filesystem: it doesn't reside anywhere on your drive. 'proc' stands for processor, and what you're doing as you navigate through /proc is navigating through what your cpu sees (eg: mounted partitions, files in ram, cpu temperatures, etc.). /proc is gone when you shutdown the computer, and it gets re-created when you turn it back on. In other words, you can't solve things permanently by trying to edit /proc files.

Filling up / to capacity is always a problem. How much room did you give it to begin with? Maybe you'd want to expand that partition. You can view all of your partitions' capacities with the command :
```
df -h
```

To backup data (/), I use the dd command from Terminal.
To backup data (/home), I use rsync to send it to a network drive.

---

### Post by streamsanddragonflies on 2011-04-22
Hello, back but for a momment!

Still no time to do bkups yet.  Mr. Egg thanks for pointing out:

>  /proc is actually a virtual filesystem: it doesn't reside anywhere on your drive.'proc' stands for processor, and what you're doing as you navigate through /proc is navigating through what your cpu sees...  

I finally looked into it and realise thus that having attempted to write to proc/mounts made no sense.  Only fstab yields the mount instructions. I read up on fstab configuration and mount options, and to my understanding, the last number or sixth field, is fsck, so the number will mean the order in which filesystems are checked if the system wasen't shutdown properly.  So as long as we aren't trying to recover / (then it's 1), 2 is probably a safer bet than 0, (which means no filesystem check) when something goes wrong...Things always seem to make more sense once trouble is already averted!

> To backup data (/), I use the dd command from Terminal.
To backup data (/home), I use rsync to send it to a network drive.

When I get to backing up; ```
/ dd /dev/sda3/bkup1
``` is this the correct way, if I have a spare partition on another drive? Also wondering what is the command to back up to external USB HDD...

BTW it was my /boot specifically showing full, my / should have sufficient space, will check again tommorow.  I read that others have had to remove old kernels to solve this issue...don't mind since grub2 screen looks cleaner this way...

---

