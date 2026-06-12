---
title: "Can't enlarge ubuntu partition"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by MasterOfMuppets on 2007-02-20
I have Ubuntu/Kubuntu Edgy here and a windows partition. When I try to enlarge the linux partition, gparted gives me some weird error.
I will post this error when I'm back home, but maybe someone here can help me still.
I noticed with win defragmenter that I have an immovable block somewhere towards the far end of the partition. I assume this is just a graphic presentation of things and not a direct translation of what is happening on the HD proper, but I thought this info might be useful.

---

### Post by floke on 2007-02-20
No worries.

The 'immovable' stuff on the right are the page file and the hibernation space.
To be rid of them simply turn of hibernation from the Windows power options.
To get rid of the page file go to (i think this is it anyway...) My Computer (maybe right click?) - Advanced tab - then page file (its somewhere around here anyway). Select the no page file or disable page file option thing (this is basically a swap file). Windows will then need to reboot (reminding you nicely of why you want to shrink it in the first place). And GParted can take care of things from here.

I had exactly the same issue shrinking my Win partition the other day.

Post back if you have any problems.

-- EDIT: Not sure if you can resize from right to left though - ie expand an existing Lx partition on the right and make it go leftwards. What I did was to shrink Windows and in the new space between windows and ubuntu (about 5 gigs) put an installation of Feisty. I then shrank the 'old' ubuntu partitions and added new partitions on the end (right) which are now used for the home directories. So - my disc looks (something) like this:

[1] Windows XP
[4] Feisty
[2] Edgy
[3] Feisty home Directory
[4] Edgy home directory 

Once Feisty is released i can then erase the Edgy partitions and expand Feisty rightwards to gobble up the space!

---

### Post by MasterOfMuppets on 2007-02-20
Lol :)
Your HD looks like a mess :).
Anyways thanks for the tip, I'll give it a shot.
Restarting windows....

---

### Post by Metallinut on 2007-02-20
I have my disk partitioned thusly:

[1] Windows 
[2] Edgy /
[3] Edgy /home
[4] Swap

I wanted to decrease the size of [3], and increase the size of [2] but I'm running into errors.  I'll have to get the exact errors, but I believe it had something to do with immovable blocks or something like that.  

Could this be caused by Windows (e.g. pagefile) even though Windows isn't running?  And wouldn't Windows be confined to use the NTFS partition I gave it?

Thanks,

---

### Post by MasterOfMuppets on 2007-02-20
That's exactly it metal.
It worked! Thanks Steve!
Now my HD looks like this:
1)win
2)Extended (swap+free space, still a mystery to me if it's even mounted)
3) Ex3

Can someone give me any clarification to my situation?
I don't even know where I can see how much space I'm using... :(

---

### Post by floke on 2007-02-20
Not sure if I understand your disc setup - you say that 2 is the extended with the swap file and 3 is ext3 - so where do you have ubuntu installed? Surely ubuntu would be on your HD before the extended partition? And can the LiveCd tell you what filesystems are using what amount of space.

(I forgot to mention that my home directories for edgy and feisty  both live in the same extended partition as the swap file - which is shared by edgy and feisty).

---

### Post by MasterOfMuppets on 2007-02-20
```
moshewe@moshewe-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       31031    15639246    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           67921       77520     4838400   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/hda3           58555       67910     4715077+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           31031       58555    13872127+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           31031       33055     1020096   82  Linux swap / Solaris
/dev/hda6           33055       58555    12851968+  83  Linux
Partition table entries are not in disk order
moshewe@moshewe-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3    4.5G  2.4G  2.0G  55% /
varrun       tmpfs    506M   84K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs     10M  192K  9.9M   2% /proc/bus/usb
udev         tmpfs     10M  192K  9.9M   2% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile

```

I think I found my answer... Now all I need to do is mount:
/dev/hda6           33055       58555    12851968+  83  Linux
Do I need to mount the swap? How does that work?...
Can I define my /home to be /dev/hda6? How?

---

### Post by floke on 2007-02-20
The information about mounted partitions is in the /etc/fstab file.
Mine looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc       proc    defaults        0       0
# /dev/sda4
UUID=6411e052-3eb4-455a-bd70-af84e4eadc5e /  ext3 defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=741C89A01C895E4C /media/sda1  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=f002860a-df3d-4510-bab4-6e344145c383 /media/sda2     ext3    defaults        0       2
# /dev/sda6
UUID=e8a8fb2a-0caf-40d4-b2a3-7f3e79675ecc /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=23838828-43dd-4894-9d1f-d1626a5bcae4 /media/sda7     ext3    defaults        0       2
# /dev/sda5
[B]UUID=dc3b15d5-7642-f9a0-1dda-b78ce61f8f52 none            swap    sw              0       0
[/B]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# mounting sda6 as Feisty home directory
**/dev/sda6 /home ext3 nodev,nosuid 0 2**

The first highlight should (I think) tell you if the swap file is mounted (there's actually a better way to see if you have a swap file set up, and how much it is using, from the CLI - but I can't remember off the top of my head - so I'd have a look round the forum on this one).

The second highlight mounts sda6 as my home file, so just copy the line and change it to hda6 (best to use 'sudo cp /etc/fstab /etc/fstab_backup' first though, in case anything goes wrong - if it does then get to a terminal and use 'sudo nano /etc/fstab' or 'sudo cp /etc/fstab_backup /etc/fstab' to change things back).

If you are transferring an existing home directory with files in to a new partition then folliow the guide here [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hope this helps:)

---

### Post by hinzel on 2007-02-20
> **MasterOfMuppets said:**
> ```
moshewe@moshewe-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       31031    15639246    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           67921       77520     4838400   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/hda3           58555       67910     4715077+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           31031       58555    13872127+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           31031       33055     1020096   82  Linux swap / Solaris
/dev/hda6           33055       58555    12851968+  83  Linux
Partition table entries are not in disk order
moshewe@moshewe-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3    4.5G  2.4G  2.0G  55% /
varrun       tmpfs    506M   84K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs     10M  192K  9.9M   2% /proc/bus/usb
udev         tmpfs     10M  192K  9.9M   2% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile

```

I think I found my answer... Now all I need to do is mount:
/dev/hda6           33055       58555    12851968+  83  Linux
Do I need to mount the swap? How does that work?...
Can I define my /home to be /dev/hda6? How?

is /dev/hda6 already located in your fstab?

---

### Post by floke on 2007-02-20
It's there, but it's not mounted as /home

Also, Ubuntu should automatically detect and use a swap file

---

### Post by Metallinut on 2007-02-20
Are you guys using gparted from the Live CD, or are you able to use it when logged in normally?

---

### Post by floke on 2007-02-20
You should use it from the LiveCD.
Looking at your above post - why do you want to reduce the size of your home partition and extend the system partition?

---

### Post by MasterOfMuppets on 2007-02-20
Done. Thanks for the help guys!
Found a guide for mounting everything.

---

### Post by floke on 2007-02-20
Good to hear it :) 

Can you post a link to the guide here so it can help others?

Cheers

---

### Post by Metallinut on 2007-02-20
> **Steve.K said:**
> You should use it from the LiveCD.
Looking at your above post - why do you want to reduce the size of your home partition and extend the system partition?

I had 5 GB set aside for / with the rest for /home.  After playing around and installing a bunch of stuff, my / partition is running out of space, so I wanted to resize a tad...

---

### Post by floke on 2007-02-20
Given that it looks from your outline that its sitting between XP and your home dir., and given that I don't think you can resize leftwards due to the arrangement of the data (though someone please correct me if I'm wrong), it looks like your best option is to 

(a) create a new home dir. (i.e. split your existing home into 2)
(b) shift everything from your home dir. over to the new one
(c) mount your new home dir. 
(d) delete the old one
(e) Use GParted to have the existing / partition grab the extra space space - i.e. shift / to the right.

See the above guide by Aysiu for creating a new home partition and for moving folders between them.

Of course all this depends on how much room you have in your existing home partition.

---

### Post by MasterOfMuppets on 2007-02-21
I used Aysiu's guide for making a new home.
I think I messed up something with the fstab, I can't read CDs anymore...

This is the fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

#cd-rom/dvd mount
/dev/hdc        /media/cdrom0   udf,iso9660 user,	noauto     0       0

#floppy mount?!
/dev/           /media/floppy0  auto    rw,user,	noauto     0       0

#windows partition
/dev/hda1    	/media/windows 	ntfs  	nls=utf8,	umask=0222 0       0

# /dev/hda3 (main linux partition)
UUID=eff3da31-fbc3-4aab-a4d8-30aeb8a6d61d /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda5 (linux swap partition)
UUID=76e046d0-7430-4b4c-9ff2-eb4b80b56ee9 none            swap    sw              0       0

#linux /home partition
/dev/hda6 	/home 		ext3 	nodev,		nosuid 	   0 	   2

```

This is the mtab (I don't know what this file means, Nautilus just said something about it in correlation with fstab whom I know of):
```
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
/dev/hda6 /home ext3 rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

If someone could explain to me what mtab means, I'd be grateful.\
About fstab, my intuition says I should make the cd drive automount.

EDIT:
I can't mount my windows partition either :(.

---

### Post by floke on 2007-02-21
What errors are you getting? Your fstab looks like mine so it can't be that.
Is it an ownership issue. Can you navigate through to your cdrom mount point and read the contents of it by using gksu nautilus? If so, then you need to change the ownerships.

---

### Post by MasterOfMuppets on 2007-02-23
Something is terribly wrong, I can't even log in... :( Using live CD now...
What's the ownership part? How do I change it?
EDIT:
Toyed a little with the fstab, I'm logged in now.
Windows partition still not mounting, these are the errors I get:
```
moshewe@moshewe-laptop:~$ sudo mount -a
Password:
[mntent]: line 7 in /etc/fstab is bad
[mntent]: line 10 in /etc/fstab is bad
[mntent]: line 13 in /etc/fstab is bad

```
I'll try to fix it myself, maybe syntax problems...?
fstab looks just the same, I think...
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

#cd-rom/dvd mount
/dev/hdc        /media/cdrom0   udf,iso9660 user,	noauto     0       0

#floppy mount?!
/dev/           /media/floppy0  auto    rw,user,	noauto     0       0

#windows partition
/dev/hda1    	/media/windows 	ntfs  	nls=utf8,	umask=0222 0       0

# /dev/hda3 (main linux partition)
UUID=eff3da31-fbc3-4aab-a4d8-30aeb8a6d61d /  ext3    defaults,errors=remount-ro 0       1

# /dev/hda5 (linux swap partition)
UUID=76e046d0-7430-4b4c-9ff2-eb4b80b56ee9 none            swap    sw              0       0

#linux /home partition
/dev/hda6 	/home 		ext3 	nodev,nosuid 	   0 	   2

```

And these are the errors I get trying to read a CD:
```

[mntent]: line 7 in /etc/fstab is bad

[mntent]: line 10 in /etc/fstab is bad

[mntent]: line 13 in /etc/fstab is bad

mount: can't find /dev/hdc in /etc/fstab or /etc/mtab


```

EDIT:
After a mount -a everything works.
How do I make it automount the windows partition?!

---

