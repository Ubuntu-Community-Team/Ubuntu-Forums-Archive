---
title: "/home created during install is not used"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by 02darkRS on 2011-09-23
I set up as follows: 
60GB OCZ SSD 
sda1 - ntfs (for future Windows 7 install) 
sda2 - ext4 - / 

I also have a 1TB HDD setup as follows: 
sdb1 - apps 
sdb2 - W7system files (stuff moved from ssd for space saving) 
sdb3 - extended 
sdb5 - ext4 - /home 
sdb6 - Swap
sdb7 - ext4 - /tmp 
sdb8 - ext4 - /var 
sdb4 - ntfs - data  

my extended partitions do not appear to be in use. all home files are still in sda2 /home under the separate user names folders. i thought ubuntu knew to use the respective created partitions? do i now need to follow:  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) or one of the many other how to's? 

also how do i force use of /tmp , /var ?
I also set up a swap on sdb but it is not visible in computer. is that normal?

---

### Post by 02darkRS on 2011-09-25
> **02darkRS said:**
> I set up as follows: 
60GB OCZ SSD 
sda1 - ntfs (for future Windows 7 install) 
sda2 - ext4 - / 

I also have a 1TB HDD setup as follows: 
sdb1 - apps 
sdb2 - W7system files (stuff moved from ssd for space saving) 
sdb3 - extended 
sdb5 - ext4 - /home 
sdb6 - ext4 - /tmp 
sdb7 - ext4 - /var 
sdb4 - ntfs - data  

my extended partitions do not appear to be in use. all home files are still in sda2 /home under the separate user names folders. i thought ubuntu knew to use the respective created partitions? do i now need to follow:  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) or one of the many other how to's? 

also how do i force use of /tmp , /var ?
I also set up a swap on sdb but it is not visible in computer. is that normal?

Can someone just point me to a link that does not assume I know the beginning steps of every action in the terminal? for instance all tut's regarding moving home seem to assume I know how to grant access to myself to perform such actions as mounting & moving directories, etc.

---

### Post by Hakunka-Matata on 2011-09-25
have you added entries in your /etc/fstab file?  All the resources (partitions) declared in fstab get mounted.

> Can someone just point me to a link that does not assume I know the  beginning steps of every action in the terminal? for instance all tut's  regarding moving home seem to assume I know how to grant access to  myself to perform such actions as mounting & moving directories,  etc.If you've never had a separate /home partition yet, then you have to migrate your home data to the new partition as described in that Hyperlink you use in post# 1, & 2.  
Just copy and paste the commands into a terminal one at a time, they will all work.

> I also set up a swap on sdb but it is not visible in computer. is that normal?
I think that is normal.

---

### Post by jocko on 2011-09-26
> **02darkRS said:**
> I set up as follows: 
60GB OCZ SSD 
sda1 - ntfs (for future Windows 7 install) 
sda2 - ext4 - / 

I also have a 1TB HDD setup as follows: 
sdb1 - apps 
sdb2 - W7system files (stuff moved from ssd for space saving) 
sdb3 - extended 
sdb5 - ext4 - /home 
sdb6 - ext4 - /tmp 
sdb7 - ext4 - /var 
sdb4 - ntfs - data  

my extended partitions do not appear to be in use. all home files are still in sda2 /home under the separate user names folders. i thought ubuntu knew to use the respective created partitions? do i now need to follow:  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) or one of the many other how to's? 

also how do i force use of /tmp , /var ?
I also set up a swap on sdb but it is not visible in computer. is that normal?

Could you post the results of a few commands to let us see what actually happened:
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```

---

### Post by 02darkRS on 2011-09-29
I will run that command this evening if it lets me.

---

### Post by Quackers on 2011-09-29
During installation when creating the /home partition, did you give it a mount point /home?

---

### Post by 02darkRS on 2011-09-29
> **Quackers said:**
> During installation when creating the /home partition, did you give it a mount point /home?

i don't know how to do that so I am assuming no. I created the partitions, formatted the sda2, & installed from LiveCD.

---

### Post by 02darkRS on 2011-09-29
sudo fdisk -l:
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075b5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3956    31769600    7  HPFS/NTFS
/dev/sda2   *        3956        5359    11275264   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19214   154328064    7  HPFS/NTFS
/dev/sdb2           19214       32115   103626752    7  HPFS/NTFS
/dev/sdb3           32115       39568    59872257    5  Extended
/dev/sdb4           45001      110265   524234752    7  HPFS/NTFS
/dev/sdb5           32115       34048    15525888   83  Linux
/dev/sdb6           34048       35472    11437056   82  Linux swap / Solaris
/dev/sdb7           35472       38159    21584896   83  Linux
/dev/sdb8           38159       39568    11321344   83  Linux

```

cat etc/fstab:
```
cat: etc/fstab: No such file or directory

```

mount:
```
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dillon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dillon)
gvfs-fuse-daemon on /home/darkrs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darkrs)

```

sudo blkid:
```
/dev/sda1: LABEL="W7" UUID="4307946B66D20EFB" TYPE="ntfs" 
/dev/sda2: UUID="68db7931-3f9b-45e5-acdc-fb177c5f1dfb" TYPE="ext4" 
/dev/sdb1: LABEL="Apps" UUID="5A5C0CE3543B0EF2" TYPE="ntfs" 
/dev/sdb2: LABEL="W7sys" UUID="363099477DED436B" TYPE="ntfs" 
/dev/sdb4: LABEL="data" UUID="784ECE3C6209F341" TYPE="ntfs" 
/dev/sdb5: LABEL="/home" UUID="e3a1a937-a023-4757-a0bb-e3d4c737a7a4" TYPE="ext4" 
/dev/sdb6: LABEL="swap" UUID="2f7fd365-a71d-4401-86dd-29b8002b1e2a" TYPE="swap" 
/dev/sdb7: LABEL="/tmp" UUID="d4404d37-29ab-4108-9705-51ddf419436c" TYPE="ext4" 
/dev/sdb8: LABEL="/var" UUID="3681e029-8893-437f-b8dc-63ed3a5ae41f" TYPE="ext4" 

```

---

### Post by jocko on 2011-10-02
> **02darkRS said:**
> ```
cat: etc/fstab: No such file or directory
```You have to type the path to the file correctly. It's "/etc/fstab", not "etc/fstab"...

---

### Post by 02darkRS on 2011-10-02
```
darkrs@darkrs-A780L3G:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=68db7931-3f9b-45e5-acdc-fb177c5f1dfb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none            swap    sw              0       0

```

I am assuming this agrees with my issue but I didn't see anywhere during install that I could have told it to go to the Sdb drive.
/ was on /dev/sda2 during installation

---

### Post by Quackers on 2011-10-02
When installing, if you want a separate home partition you need to select the manual partitioning option (in 11.04 that's called "something else") then you need to manually create (or designate) partitions for the Ubuntu root file system with a mount point of " / " and the home partition with a mount point of "/home".
Then the installer knows where to install everything and the /etc/fstab file correctly identifies your home directory in the /home partition.

---

### Post by 02darkRS on 2011-10-03
I did this. Hence, the separate partitions which are created & shown. What could I have not chosen to make it not use the /home it created?

---

### Post by Hakunka-Matata on 2011-10-03
Post@ 10:, is that your complete /etc/fstab file?  If so, it has the error of not including your /home partition and UUID.

**ADDITION: **> 
     Quote:
                                                 I also set up a swap on sdb but it is _**not visible in computer**_. is that normal?                                 
I think that is normal. My answer: "I think that is normal:" assumed you meant you were looking for it in nautilus File Manager, (swap type is not usually browse-able, or if it is browsable, I don't know how to view it's contents)."
You can however verify you have a swap partition by using fdisk, or blkid, or gparted.

---

### Post by 02darkRS on 2011-10-03
> **Hakunka-Matata said:**
> Post@ 10:, is that your complete /etc/fstab file?  If so, it has the error of not including your /home partition and UUID.


Yes that is correct. So based on your other response:
> have you added entries in your /etc/fstab file?  All the resources (partitions) declared in fstab get mounted.

How can I add the missing entries?

---

### Post by Hakunka-Matata on 2011-10-03
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cd328419-f3f6-47bb-8b34-987b301342ad /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=3f358de2-71d3-4784-981b-0918c3e49f87 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=6709c2c9-a0a2-4108-8a69-0b46fb72b44c none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=01f64158-cfc8-4de5-b54c-e50262d3b76b none            swap    sw              0       0

```That is my /etc/fstab.  There are two swaps, not a problem, just how my system happens to look.
make a backup of the current fstab file so you can go back to it if you wish.  
```
#from home, 
sudo cp /etc/fstab /etc/fstabbackup
sudo gedit /etc/fstab
```#add the two lines, with the correct UUID of your /home partition
Ctrl - S = save the file and reboot

---

### Post by 02darkRS on 2011-10-05
How do I find the correct UUID?

---

### Post by jocko on 2011-10-05
> **02darkRS said:**
> How do I find the correct UUID?
I've already given you the command to check that:
> **02darkRS said:**
> 
[/CODE]sudo blkid:
```
/dev/sda1: LABEL="W7" UUID="4307946B66D20EFB" TYPE="ntfs" 
/dev/sda2: UUID="68db7931-3f9b-45e5-acdc-fb177c5f1dfb" TYPE="ext4" 
/dev/sdb1: LABEL="Apps" UUID="5A5C0CE3543B0EF2" TYPE="ntfs" 
/dev/sdb2: LABEL="W7sys" UUID="363099477DED436B" TYPE="ntfs" 
/dev/sdb4: LABEL="data" UUID="784ECE3C6209F341" TYPE="ntfs" 
[COLOR=Blue] /dev/sdb5: LABEL="/home" UUID="e3a1a937-a023-4757-a0bb-e3d4c737a7a4" TYPE="ext4" [/COLOR]
/dev/sdb6: LABEL="swap" UUID="2f7fd365-a71d-4401-86dd-29b8002b1e2a" TYPE="swap" 
/dev/sdb7: LABEL="/tmp" UUID="d4404d37-29ab-4108-9705-51ddf419436c" TYPE="ext4" 
/dev/sdb8: LABEL="/var" UUID="3681e029-8893-437f-b8dc-63ed3a5ae41f" TYPE="ext4" 

```

So the line you need to add to your /etc/fstab should look like this:```
[COLOR=Blue]UUID=e3a1a937-a023-4757-a0bb-e3d4c737a7a4 [/COLOR]/home ext4 defaults 0 2
```

---

### Post by 02darkRS on 2011-10-08
This is what I get when I followed the aforementioned commands:

darkrs@darkrs-A780L3G:~$ sudo cp /etc/fstab /etc/fstabbackup
[sudo] password for darkrs: 
darkrs@darkrs-A780L3G:~$ sudo gedit /etc/fstab

(gedit:4122): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.90A72V': No such file or directory

(gedit:4122): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by 02darkRS on 2011-10-08
I went ahead & updated /etc/fstab. Saved. Restarted. Then my system would not work...... after many reboots i was able to get back into gedit to remove the added /home information. reboot & return to normal. I followed the above directions. these are the errors I recv'd below. What did you leave out or what did I possibly get wrong? 

Initial error on boot: Could not mount 0. Options: manual mount or skip. 
Chose: Skip

errors after logging into admin user on splash screen:

1. Could not update ICEauthority file /home/darkrs/.ICEauthority
2. There is a problem with the configuration server (/usr/lib/libconfig 2 - 4/gconf-sanity-check-2) exited with status 256
3. Nautilus could not creat the following required folders: /home/darks/Desktop./home/darkrs/.nautilus
         before running, please create these folders or set permission such that nautilus can create them


(I attempted to just load the backed up /etc/fstab.... that resulted in a whole other set of errors with it claiming root could not access. does not exist. etc. What good is backing up a file if cp /etc/fstab/backup /etc/fstab fails to work?)

---

### Post by 02darkRS on 2011-10-08
I've read these. I understand what I am doing but I am still getting the same errors when adding the /home to the /etc/fstab.... what's wrong? 

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

something about using default seems to flag me as the problem. Default is explained in the link to only allow root to mount the device. I would want anyone to be able to access /home.

---

### Post by 02darkRS on 2011-10-09
bump
:popcorn:

---

### Post by Hakunka-Matata on 2011-10-09
> **post# 19:02darkRS** (I attempted to just load the backed up /etc/fstab.... that resulted in a  whole other set of errors with it claiming root could not access. does  not exist. etc. What good is backing up a file if cp /etc/fstab/backup  /etc/fstab fails to work?)> **post# 15:Hakunka-Matata **#from home,  sudo cp /etc/fstab /etc/fstabbackup 
sudo gedit /etc/fstabIf the code to create the backup was input correctly as posted: **sudo cp /etc/fstab /tec/fstabbackup, [COLOR=Red]It created a _file_ named _fstabbackup_ in the _/etc directory_[/COLOR]**:

The command you used as quoted in post# 19: **cp /etc/fstab/backup** went looking for a file named backup in the /etc/fstab directory which does not exist.  The correct command to replace the original fstab file with the backup copy would be **sudo cp /etc/fstabbackup /etc/fstab**.  
Again, that is supposing the copy command I proposed in post# 15, were input precisely as stated.  Copying the commands, and posting them into the Terminal window is a good practice to use.  
It's easy enough to check the directory listings to see if what you wanted to happen actually happened.

It's hard for me to keep track of all the directory/file paths in my local (head) memory at times too, I hope it happens to others also, occasionally...................

**EDIT:**correcting a typo in this line "sudo cp /etc/fstab /[color=red]tec[/color]/fstabbackup," should read "sudo cp /etc/fstab /[color=red]etc[/color]/fstabbackup,"

---

### Post by 02darkRS on 2011-10-10
> **Hakunka-Matata said:**
> If the code to create the backup was input correctly as posted: **sudo cp /etc/fstab /tec/fstabbackup, [COLOR=Red]It created a _file_ named _fstabbackup_ in the _/etc directory_[/COLOR]**:

The command you used as quoted in post# 19: **cp /etc/fstab/backup** went looking for a file named backup in the /etc/fstab directory which does not exist.  The correct command to replace the original fstab file with the backup copy would be **sudo cp /etc/fstabbackup /etc/fstab**.  
Again, that is supposing the copy command I proposed in post# 15, were input precisely as stated.  Copying the commands, and posting them into the Terminal window is a good practice to use.  
It's easy enough to check the directory listings to see if what you wanted to happen actually happened.

It's hard for me to keep track of all the directory/file paths in my local (head) memory at times too, I hope it happens to others also, occasionally...................

I generally do copy & paste. I am also certain the backup was created with **sudo cp /etc/fstab /etc/fstabbackup**.

**sudo cp /etc/fstabbackup /etc/fstab  **was the code I used to attempt to pull in the backed up fstab after the failure. Which resulted in all the other errors I posted about.[B] 

I am assuming this is a mistype? :
[/B]> If the code to create the backup was input correctly as posted: **sudo cp /etc/fstab [COLOR=Red]/tec/[/COLOR]fstabbackup**

I still need to know why the addition of the /home partition in the fstab file caused all those failures. Everything was typed correctly I assure you. I did it three times & each time I rechecked everything multiple times.

> It's easy enough to check the directory listings to see if what you wanted to happen actually happened.
I have checked (cat /etc/fstabbackup):
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=68db7931-3f9b-45e5-acdc-fb177c5f1dfb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none            swap    sw              0       0


---

### Post by Hakunka-Matata on 2011-10-10
Yes, that is a typo, sorry.  I go on about syntax then throw in a typo myself!

I don't know why your /home is not working, unless it has to do with the other partitions you say you created, /tmp and /var.
Where/when do these partitions get mounted?  Since I've used only a separate /home partition, I'm not up on what to do when using the umpteen other schemes of separate partitions.  I suspect that may be the problem here.  [This link]("https://help.ubuntu.com/community/MoveMountpointHowto") says a lot about the subject.

---

### Post by 02darkRS on 2011-10-10
I'll check that out. It's one I have not read.

I do not know how/when they are mounted or used. In my pre install study I read & was advised to create them. I assumed I'd be asked or have a point during install to direct items to these but just like /home...... that was not the case.

---

### Post by Hakunka-Matata on 2011-10-10
Ubuntu is so easy to install, have you thought about just reinstalling and using a separate /home, but not all the other ones?
If you have an extra 10GiBs unallocated, format a new ext4 partition and install a fresh os to it.  Fast & Easy.  Call it 'testing'...

---

### Post by jocko on 2011-10-11
> **02darkRS said:**
> I'll check that out. It's one I have not read.

I do not know how/when they are mounted or used. In my pre install study I read & was advised to create them. I assumed I'd be asked or have a point during install to direct items to these but just like /home...... that was not the case.
When you made the partitions you should have set their mount points, and you would have had no problems (but there should be no problem setting the mount points after the fact)... 
From your blkid output it looks like you put  your intended mount points as lables for the partitions instead of actually setting the mount points...

---

### Post by 02darkRS on 2011-10-11
Great, so how do I fix it? 
 
I did mull over reinstalling. No, I do not have extra space to add another instance of Ubuntu. The OS's are residing on a 60G SSD. I would have to install it over the current. If I cannot fix this. I am willing to do that but I need to apparently have my hand held through this process as I do not remember anything/anywhere asking for mount points: 
 
> When you made the partitions you should have set their mount points, and you would have had no problems
 
 
> From your blkid output it looks like you put your intended mount points as lables for the partitions instead of actually setting the mount points... 
 
I get what you're saying but I need to know where I would have done that wrong? I created & labeled them in GPARTED during a live CD session. Then during install I saw nowhere asking me to set the mount points.

---

### Post by Hakunka-Matata on 2011-10-11
[http://ubuntuforums.org/showthread.php?p=11151903#post11151903](http://ubuntuforums.org/showthread.php?p=11151903#post11151903)

That is a recent thread (Aug - 2,011) that might be helpful to understand the issue at a deeper level.  

Are you operating off a liveCD boot now?

---

### Post by jocko on 2011-10-11
> **02darkRS said:**
> I get what you're saying but I need to know where I would have done that wrong? I created & labeled them in GPARTED during a live CD session. Then during install I saw nowhere asking me to set the mount points.
See my screenshots from the installer:

---

### Post by 02darkRS on 2011-10-11
> **Hakunka-Matata said:**
> [http://ubuntuforums.org/showthread.php?p=11151903#post11151903](http://ubuntuforums.org/showthread.php?p=11151903#post11151903)

That is a recent thread (Aug - 2,011) that might be helpful to understand the issue at a deeper level.  

Are you operating off a liveCD boot now?

no i was able to get into fstab even when booting into a user failed & edit it back to normal. save & reboot. so, i  am running an the installed version.

That link has a great idea since I have a data partition but..... since I can't even edit my fstab correctly I don't think it will help with my current issue.

---

### Post by 02darkRS on 2011-10-11
> **jocko said:**
> See my screenshots from the installer:


got it. I must not have chosen the mount points in pic 4..... well thank you. if I don't figure out anything reading the two links posted recently then I guess I know where to fix it now during my reinstall.

---

### Post by 02darkRS on 2011-10-11
how about this: if someone has the time to instead of quoting lines that I should add independently. show me what my fstab should have looked like when I edited it as previously directed:


> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=68db7931-3f9b-45e5-acdc-fb177c5f1dfb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none            swap    sw              0       0
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3956    31769600    7  HPFS/NTFS
/dev/sda2   *        3956        5359    11275264   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19214   154328064    7  HPFS/NTFS
/dev/sdb2           19214       32115   103626752    7  HPFS/NTFS
/dev/sdb3           32115       39568    59872257    5  Extended
/dev/sdb4           45001      110265   524234752    7  HPFS/NTFS
/dev/sdb5           32115       34048    15525888   83  Linux
/dev/sdb6           34048       35472    11437056   82  Linux swap / Solaris
/dev/sdb7           35472       38159    21584896   83  Linux
/dev/sdb8           38159       39568    11321344   83  Linux
sdb 5: /home
sdb 6: swap
sdb 7: /tmp
sbd 8: /var


something else I noticed when writing this. I opened Disk Utility to view the partitioning & it shows Mount point for sdb5 as:
 /media/ home   (the space is actually there between /media/ & home
 does this point to anything?

---

### Post by jocko on 2011-10-12
> **02darkRS said:**
> something else I noticed when writing this. I opened Disk Utility to view the partitioning & it shows Mount point for sdb5 as:
 /media/ home   (the space is actually there between /media/ & home
 does this point to anything?
A partition that has no (proper) entry in fstab will be mounted manually in /media. If the partition has a label the mount point will be the same as the label. In your case the label is "/home", so the mount point would become "/media//home". I guess the double slash is converted to a single slash and a space...

This fstab should work for you:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=68db7931-3f9b-45e5-acdc-fb177c5f1dfb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none            swap    sw              0       0
# /home partition (/dev/sdb5):
UUID=e3a1a937-a023-4757-a0bb-e3d4c737a7a4 /home           ext4    defaults        0       2
```But I just realized that if you reboot with this fstab, you will have a completely empty /home, so you won't be able to log in. You will first have to copy your existing home directory to your /dev/sdb5 partition, but when doing this you will have to make absolutely sure that all file permissions are kept...

rsync should do it:
```
sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/\ home/.
```
(this command assumes your /dev/sdb5 partition is mounted in "/media/ home". Make sure that's the real mount point it has by 'ls /media')

For more help, [read this page]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

---

### Post by 02darkRS on 2011-10-12
> But I just realized that if you reboot with this fstab, you will have a completely empty /home, so you won't be able to log in. You will first have to copy your existing home directory to your /dev/sdb5 partition, but when doing this you will have to make absolutely sure that all file permissions are kept...

 
so, this seems to explain the problem & errors I had when I attempted this.
 
I have multiple users. Does this change any steps?
> rsync should do it:
 
Code:
sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/\ home/.
(this command assumes your /dev/sdb5 partition is mounted in "/media/ home". Make sure that's the real mount point it has by 'ls /media')

 
> For more help, [[COLOR=#444444]read this page[/COLOR]]("https://help.ubuntu.com/community/Partitioning/Home/Moving").
This is the link I posted in Post 1 asking if I should follow these steps or not to do what I need to do.

---

### Post by jocko on 2011-10-12
> **02darkRS said:**
> I have multiple users. Does this change any steps?.It changes nothing. All directories in your current /home will be copied to your /dev/sdb5 partition (and nothing will be deleted so you can always get it back by reverting to your old /etc/fstab)...

If it does not work you can always boot into recovery mode, drop to a root terminal and edit your /etc/fstab again with this command:
```
nano /etc/fstab
```
and comment out the line for the /dev/sdb5 partition (just put a # in front of it, ctrl+o to save, ctrl+x to exit nano, then type "reboot" to reboot)...

---

### Post by 02darkRS on 2011-10-12
ok, I am following the link but I am still getting the same error when I edit fstab:
> darkrs@darkrs-A780L3G:~$ gksu gedit /etc/fstab

(gedit:1782): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.J40A3V': No such file or directory

(gedit:1782): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1782): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.EBZM3V': No such file or directory

(gedit:1782): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
When I restarted after 4. (making the /media/home directory) I received: Serious errors while attempting to mount /media/home.........

I follow this stuff to a T.... why does none of it work?

Now add these errors when checking the copy:
> darkrs@darkrs-A780L3G:~$ sudo diff -r /home /media/home
Only in /home/darkrs: .gvfs
Binary files /home/darkrs/.mozilla/firefox/1590tru4.default/cookies.sqlite-shm and /media/home/darkrs/.mozilla/firefox/1590tru4.default/cookies.sqlite-shm differ
Binary files /home/darkrs/.mozilla/firefox/1590tru4.default/cookies.sqlite-wal and /media/home/darkrs/.mozilla/firefox/1590tru4.default/cookies.sqlite-wal differ
diff: /home/darkrs/.mozilla/firefox/1590tru4.default/lock: No such file or directory
diff: /media/home/darkrs/.mozilla/firefox/1590tru4.default/lock: No such file or directory
Binary files /home/darkrs/.mozilla/firefox/1590tru4.default/urlclassifier3.sqlite and /media/home/darkrs/.mozilla/firefox/1590tru4.default/urlclassifier3.sqlite differ
Only in /home/dillon: .gvfs
diff: /home/dillon/.local/share/Trash/files/oolite: No such file or directory
diff: /media/home/dillon/.local/share/Trash/files/oolite: No such file or directory
diff: /home/dillon/.pulse/cfc0c2144e405d06d3dfb3ee00000003-runtime: No such file or directory
diff: /media/home/dillon/.pulse/cfc0c2144e405d06d3dfb3ee00000003-runtime: No such file or directory
Only in /home/family: .gvfs
diff: /home/family/.pulse/cfc0c2144e405d06d3dfb3ee00000003-runtime: No such file or directory
diff: /media/home/family/.pulse/cfc0c2144e405d06d3dfb3ee00000003-runtime: No such file or directory
Only in /media/home: lost+found
Only in /home/ryan: .gvfs
diff: /home/ryan/.pulse/cfc0c2144e405d06d3dfb3ee00000003-runtime: No such file or directory
diff: /media/home/ryan/.pulse/cfc0c2144e405d06d3dfb3ee00000003-runtime: No such file or directory


and again when changing /media/home to the appropriate /home:
> darkrs@darkrs-A780L3G:~$ gksu gedit /etc/fstab

(gedit:1765): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.34A42V': No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XH402V': No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9X3I3V': No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WR5M3V': No such file or directory

(gedit:1765): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


---

### Post by jocko on 2011-10-13
> **02darkRS said:**
> ok, I am following the link but I am still getting the same error when I edit fstab:
When I restarted after 4. (making the /media/home directory) I received: Serious errors while attempting to mount /media/home.........

I follow this stuff to a T.... why does none of it work?

Now add these errors when checking the copy:


and again when changing /media/home to the appropriate /home:
Those errors when running gedit as root are normal and can safely be ignored. It's just gedit trying to save a list of recently opened files in some non-existent subdirectory in the /root directory...
And I see nothing wrong in your diff output. The .gvfs directory is created when you log in to gnome, and it's not readable which is why the command I gave you explicitly excludes that directory from being copied. The other files that differ are files that have changed since the time you copied them, or files that are created uniquely when you log in or start an application. Nothing to worry about. everything you need is there.

As far as I can see you have no real problem. You have copied your current /home including all your user's home folders and your diff output verifies that you really have copied everything. Now just do the appropriate change to your /etc/fstab, ignore any command line messages you get, save the file and reboot.

---

### Post by 02darkRS on 2011-10-13
> **jocko said:**
> Those errors when running gedit as root are normal and can safely be ignored. It's just gedit trying to save a list of recently opened files in some non-existent subdirectory in the /root directory...
And I see nothing wrong in your diff output. The .gvfs directory is created when you log in to gnome, and it's not readable which is why the command I gave you explicitly excludes that directory from being copied. The other files that differ are files that have changed since the time you copied them, or files that are created uniquely when you log in or start an application. Nothing to worry about. everything you need is there.
 
As far as I can see you have no real problem. You have copied your current /home including all your user's home folders and your diff output verifies that you really have copied everything. Now just do the appropriate change to your /etc/fstab, ignore any command line messages you get, save the file and reboot.
 
ok will complete tonight. what about the serious errors mounting when I restarted?

---

### Post by 02darkRS on 2011-10-13
I've now found this while researching moving /var to it's correct place (and to answer an earlier question: the OS's are on an SSD. So, the frequently written to directories were placed on a seperate HDD to minimize writes.) :
[http://www.digizenstudio.com/blog/2007/06/14/watch-out-when-you-move-var-in-ubuntu/comment-page-1/#comment-194486](http://www.digizenstudio.com/blog/2007/06/14/watch-out-when-you-move-var-in-ubuntu/comment-page-1/#comment-194486)
 
So, I think I am just going to wipe & fresh install. Now that you posted those pics I know to choose the moint points correctly. I have all my important docs stored in the /data partition on the HDD. So, those should still be available right? Also, if I finish moving home I should be able to retain all users setting for desktop, internet, & bookmarks right?

---

### Post by 02darkRS on 2011-10-13
attempting to follow last steps of tut:
> darkrs@darkrs-A780L3G:/$ cd / && mv /home /old_home && cd / && sudo mkdir -p /home
mv: cannot move `/home' to `/old_home': Permission denied


---

### Post by 02darkRS on 2011-10-13
ok aside from the above.... (which I believe means i still have duplicate /home information stored on /???)

my Mount now shows /home on the correct partition but how do I make sure the same data isn't still stored on /dev/sda2  / ?

> darkrs@darkrs-A780L3G:/$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb5 on /home type ext4 (rw,nosuid,nodev,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/darkrs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darkrs)


---

### Post by Hakunka-Matata on 2011-10-13
> **02darkRS said:**
> 
my Mount now shows /home on the correct partition but how do I make sure the same data isn't still stored on /dev/sda2  / ?

unmount it and look around on sda2 (if the system will let you).  No, really, comment out your mount /home line in /etc/fstab, then reboot and see how things look.

You're making progress...................  yes?

---

### Post by 02darkRS on 2011-10-13
yes, thank you for all the help & hanging in there.... I almost feel like I understand! :p I think the main key was understanding errors weren't really errors. :-k seriously, that should be somewhere as the first thing new users read! I get errors everywhere but if i ignore them & trudge on it all ends up working.

so, here is where I am: 

I moved /home as described above. 
I did not get to move the home to old home as the link stated though..... & did not remove the directory I believe i made.

after this I restarted to be sure /etc/fstab worked. it did with no serious errors this time & home directories were under /dev/sdb5 as expected. 

so, I reinstalled using the liveCD & added the mount points appropriately this time as shown earlier in the thread via linked pics. the only worry was I recv'd serious errors while mounting /var. I typed "I" to Ignore. The only user listed was me...... so, I recreated the users while waiting for the updated nvidia driver to load. Then restarted. No /var error the second time (i read somewhere else today of someone having this issue & being told to reboot twice). The only issue now is I had to recreate the users. I would think that would stick no? Because I messed up & somehow created a new user name so, I have an unused login folder in home now. . . . . . but we're so much farther than when this started.......
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=124f0412-3e68-46f4-a9df-162dc81b94e6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=e3a1a937-a023-4757-a0bb-e3d4c737a7a4 /home           ext4    defaults        0       2
# /tmp was on /dev/sdb7 during installation
UUID=80cecb02-84e2-4e39-8aea-3ddeeca0b391 /tmp            ext4    defaults        0       2
# /var was on /dev/sdb8 during installation
UUID=4e41415f-9378-4fe7-9d2a-95f9f8778802 /var            ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none            swap    sw              0       0
> darkrs@darkrs-A780L3G:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb7 on /tmp type ext4 (rw,commit=0)
/dev/sdb5 on /home type ext4 (rw,commit=0)
/dev/sdb8 on /var type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/darkrs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darkrs)
/dev/sdb4 on /media/data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
I just need to research the options settings I have & also reset my dual screen setup which was a whole other nightmare. I'll leave unsolved for a day or so in case more errors arise or if you can help with the extra user folder since that is sort of related to moving home. I also still need to poke around to see if /home is left in dev/sda2 / somewhere & post back on that. 

(I almost installed 11.10 but I figured i'd end up with a whole new issue!)

---

### Post by 02darkRS on 2011-10-13
> **Hakunka-Matata said:**
> unmount it and look around on sda2 (if the system will let you).  No, really, comment out your mount /home line in /etc/fstab, then reboot and see how things look.


I just re read & pondered this..... won't it tell me I have errors since all user files are in home? will it really let me log in without a /home? If it did would it not recreate one in /?

---

