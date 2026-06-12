---
title: "Hardy won't automatically mount my hard drives on login"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2008-04-30
Hi everyone,

The title says it all.  Every time I log in to hardy, I must now click on each hard drive in the Places menu once for them to mount and then again to access it.  Once this is done the drives are mounted for the rest of the session, which is great, but this is really annoying since I always forget and will do something like start amarok before mounting my music drive.  Then amarok will go crazy and lose my list of music and have to take another 10 minutes to rescan it when I mount the disk.

Haas anyone else had this problem?

What can I do?

Thanks

---

### Post by garyedwardjohnston on 2008-04-30
If these are internal drives, then I don't know, if they are external usb ones then disable HiSpeed USB 2.0 support in BIOS.

---

### Post by djrobthaman on 2008-04-30
It's funny you ask.  I never even realized to say this but they are all internal drives.  However, in the places menu they're being displayed as "removable media".

---

### Post by kestrel1 on 2008-05-01
Got the same problem here. Tried editing the /etc/fstab file, but made no difference. Presume I have done something wrong. Any help appreciated.

---

### Post by wolfpacker1983 on 2008-05-02
I have the same problem. Any help would be appreciated

---

### Post by kestrel1 on 2008-05-03
Not sure if this will work, but it has for me.
You need to use pmount. This may not be installed, to install it type this in a terminal:
```
sudo apt-get install pmount
```
Once pmount is installed type:
```
sudo pmount /dev/sdb1
```
sdb1 was the correct drive for me, you may need to change that to the correct drive or partition.
If you get an error that a folder is not present in mount, you need to create the folder first. If your partition is named use that as the folders name. To create the folder type:
```
sudo mkdir /mount/pname
```
pname being the name of the partition.
Hope this helps someone.
After doing this, my drive now mounts at boot up.

---

### Post by djrobthaman on 2008-05-03
Good idea kestrel.  The description says that pmount is for allowing regular users to mount removable media without doing some fstab authentication (or something in that vein).  I just tried and I think it only works for true removable media though.  Because I got the following msg:


"Error: device /dev/sda1 is not removable"

So I guess I'm still stuck with mounting drives manually on login

---

### Post by kestrel1 on 2008-05-03
The drive I mounted was not removable. It is an internal HDD. Are you sure that the drive & partition are correct. sda1 would refer to the first partition on on the first drive (master)
You can check what disk's are attached by running this command:
```
sudo fdisk -l
```
This will tell you what each disk is & the partitions that are on it.
```
Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4560fa8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4982     1686825    5  Extended
/dev/sda5            4773        4982     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59c69c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6ed7387

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4864    39070048+   7  HPFS/NTFS

```
The above is what I get when I run the command. sdc is the only drive that is removable (USB)

---

### Post by djrobthaman on 2008-05-04
sudo fdisk -l gives me 

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00059e8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2           10454       24321   111394710    7  HPFS/NTFS
/dev/sda3            5100       10198    40957717+  83  Linux
/dev/sda4           10199       10453     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2633ec1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14589   117186111    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c685c68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x673c673c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641    7  HPFS/NTFS

```

I tried to use pmount on these devices with the same error as before.  Also, all the drives you see in the output above are internal.

I actually thought about just adding "gksudo mount -a" to the startup processes, but that didn't quite work.  I got the password box pop up on login, but no drives were mounted after that.  Is there an option that I'm missing?

Thanks

---

### Post by kestrel1 on 2008-05-04
Have you been able to get sda2 or sdb1 to mount?
I ask because they are the only ones that are not flagged up as boot partitions.

---

### Post by garyc_onbuntu on 2008-05-04
I also have this problem with a second internal drive that I added after install.

Strangely, two USB drives that I also added afterwards have no problem automounting.

fdisk shows;

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29641   238091301   83  Linux
/dev/sda2           29642       30394     6048472+   5  Extended
/dev/sda5           29642       30394     6048441   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f76e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa80bfea1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36453   292808691   83  Linux
/dev/sdc2           36454       36468      120487+  83  Linux
/dev/sdc3           36469       36483      120487+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaccf6143

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30379   244019286   83  Linux
/dev/sdd2           30380       30394      120487+  83  Linux
/dev/sdd3           30395       30401       56227+  82  Linux swap / Solaris

(/dev/sdb1 is the drive that refuses to automount after a restart).

Cheers,
Gary

---

### Post by kestrel1 on 2008-05-04
Gary: Have you tried pmount? If so did you get an error message?

---

### Post by djrobthaman on 2008-05-04
Kestrel.  I am able to mount all of my drives.  It's just that none of them are automatically mounted when my system boots.

---

### Post by ukblacknight on 2008-05-04
I'm also having this issue.  The drives show up in Places but not /media.  Double clicking them mounts them in /media, labeled as 'disk', 'disk-1' and so on.

fdisk -l:

```
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c3ebc67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15017   120624021    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x082a3b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19957   160304571    7  HPFS/NTFS
/dev/sdb2           19958       20081      996030   82  Linux swap / Solaris
/dev/sdb3           20082       30401    82895400   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f114b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```

Looking at sda1, I swear I formatted that as ex3.  I'm using that as my /home partition.  I've no idea why Ubuntu chose that as the boot drive either, as it's meaning I can't boot XP which is on sdb1.  Vista installed mbr on there too when I had that a year ago.

I'll try pmount and I'll let you know the results.

---

### Post by ukblacknight on 2008-05-04
```

tom@blacknight:~$ sudo pmount /dev/sdc1
Error: device /dev/sdc1 is not removable

```

This happened with sdb1 too.

---

### Post by kestrel1 on 2008-05-04
djrobthaman: Can you post your /etc/fstab file? To view it type:
```
sudo gedit /etc/fstab
```
Might be able to see what is going on.

---

### Post by djrobthaman on 2008-05-04
Here you go

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ac4a7f05-ae5c-410f-b9ee-7a8e898802d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=48a918d8-0347-f190-b2fc-7cbc38599ee9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Hmmm... Why did I not look here.  This seems to be the problem.  And now that I think about it when I installed hardy I did the partitioning manually and I did not check the "use this drive" box for anything other than the main linux partition.  I thought hardy would take care of that later.  Dammit.

---

### Post by megale on 2008-05-05
I have the same problem with an XP partition.
As a real Ubuntu newbie, if you could post the code fix for fstab, I would appreciate it.

Thanks

---

### Post by Joeb454 on 2008-05-05
> **megale said:**
> I have the same problem with an XP partition.
As a real Ubuntu newbie, if you could post the code fix for fstab, I would appreciate it.

Thanks

Open synaptic (click System>Administration) or Add/Remove (Under Applications) and search for NTFS config. Install this, then make sure your XP drive is not mounted, and run it from Applications>System Tools :) It will automatically mount your drive on boot :)

---

### Post by davbren on 2008-05-05
> **Joeb454 said:**
> Open synaptic (click System>Administration) or Add/Remove (Under Applications) and search for NTFS config. Install this, then make sure your XP drive is not mounted, and run it from Applications>System Tools :) It will automatically mount your drive on boot :)

Seconded, I had the same problem and ntfs-config worked a treat, make sure you haven't screwed up your fstab though...

---

### Post by jonssoni on 2008-05-05
I've got also two internal hard disks (ntfs + fat32) drives.
After upgrading from Gutsy to Hardy automount on login does not work.
Anyone to make bug report?
Very irritating problem, because my mp3 files are on fat32 disk and I have to click on the hard disk in Places menu before Audacious can play the files...

---

### Post by djrobthaman on 2008-05-05
It looks like the post I made this morning has disappeared.  But I just wanted to say that joeb's suggestion of using ntfs config worked like a charm.

johnssoni - you can make a bug report if you want.  Anyone can, no need to ask someone else to.  But is it really a bug?

I did an upgrade first and had no problem.  The problem I had, and I'm guessing you're in the same boat, happened when I did a clean install.  During the partitioning part of the install process the livecd detected all of my drives, but I did not specify that I wanted to use them (this is located in the properties menu for each partition).  So the entries needed in the fstab for automatic mounting were not saved.

I'm sure if you look in your fstab (/etc/fstab) you will only find entries for your cd drives and your linux drive.  To fix this I recommend you first make sure your drives are unmounted  (open the terminal and type "sudo umount -a") then run ntfs config (of course you have to have ntfs config installed first).    It will then give you the options for mounting your ntfs drives and when you do it that way, the fstab will get updated properly and that drive will mount automatically.

As for the fat32 drive, I think you're just going to have to edit the fstab yourself.  I'm sure that you can find the proper edit by googling around a little or you could just wait and someone will probably tell you how it should be done in this thread.

---

### Post by zsolt320i on 2008-05-05
Hi,

my problem is that the hard drives do not appear in the "places"(between the applications and system menu in the tray) menu, but the drives are automaticaly mounted in winc, wind, wine.
What should i do to appear the mounted ntfs drives in the menu?

---

### Post by megale on 2008-05-05
JOEB454,
That did the trick!  
Thanks!

---

### Post by Sari on 2008-05-22
JOEB454,
thanks man.. but one problem remain is FAT :)
this method only works for NTFS file system :(

---

### Post by seriey_x2 on 2008-05-30
I have the same problem and I found a solution which required me to edit /etc/hal/fdi/policy/preferences.fdi

from
[INDENT]<merge key="storage.automount_enabled_hint" type="bool">false</merge>[/INDENT]

to this

[INDENT]<merge key="storage.automount_enabled_hint" type="bool">true</merge>[/INDENT]


However I am a little bit hesitate to follow it. Is this will really solve the problem? Will there be any subsequent problem arise?

---

### Post by ShereKhan on 2008-06-21
This is not funny, I found really embarrassing the fact that my hard drives are not mounted automatically... I've tried suggestions in this thread but without success. Please, can someone help? At least a proper link to the solutions...

This is what I get after "sudo fdisk -l"

[I]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d972d96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19456   156280288+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       19456    53881978+   7  HPFS/NTFS
/dev/sda7               1         124      995935+  82  Linux swap Solaris
/dev/sda8             125        6374    50203093+  83  Linux[/I]

I've noticed that people usually get also partition "/dev/sda1" but for some reason I don't have that one...

Thank you for your replies...

---

### Post by Hachi-Roku on 2008-07-27
> **Joeb454 said:**
> Open synaptic (click System>Administration) or Add/Remove (Under Applications) and search for NTFS config. Install this, then make sure your XP drive is not mounted, and run it from Applications>System Tools :) It will automatically mount your drive on boot :)



After researching a way to do this in fstab, for the purposes of learning, this method proved quicker and easier.

props!

---

### Post by Capa Pinbacker on 2008-07-28
Here what I did to auto-mount an NTFS drive at boot:
1.  I used "Gparted" (via Partition Editor on the System->Administration menu) to determine that it was called hda2.

2. Then I added the appropriate line to the /etc/fstab file: 
/dev/hda2	/media/DATA	vfat umask=000 0 0 

The latter gives read/write permissions (I copied it from a prior thread).

---

### Post by The Spy on 2008-08-27
> I have the same problem and I found a solution which required me to edit /etc/hal/fdi/policy/preferences.fdi

from

    <merge key="storage.automount_enabled_hint" type="bool">false</merge>

to this

    <merge key="storage.automount_enabled_hint" type="bool">true</merge>


However I am a little bit hesitate to follow it. Is this will really solve the problem? Will there be any subsequent problem arise?

I tried this "fix" and it worked with no problems.
Thanx for posting!

---

### Post by aitjcize on 2008-08-27
> **Capa Pinbacker said:**
> Here what I did to auto-mount an NTFS drive at boot:
1.  I used "Gparted" (via Partition Editor on the System->Administration menu) to determine that it was called hda2.

2. Then I added the appropriate line to the /etc/fstab file: 
/dev/hda2	/media/DATA	vfat umask=000 0 0 

The latter gives read/write permissions (I copied it from a prior thread).

Just a little question..
why do you used "vfat" for mounting an ntfs?
here is what i do:

/dev/sdaX /media/yourdisk ntfs-3g silent,umask=0,uid=1000,gid=046,locale=en_us.utf8

---

### Post by Capa Pinbacker on 2008-09-06
> **aitjcize said:**
> Just a little question..
why do you used "vfat" for mounting an ntfs?
here is what i do:

/dev/sdaX /media/yourdisk ntfs-3g silent,umask=0,uid=1000,gid=046,locale=en_us.utf8
That's interesting.  I had read to use vfat for ntfs drives.

---

### Post by gsanders99 on 2008-10-19
Once I found the reference to this file, I edited it to comment out the entire section.  That solved my problem.  Here is what that section looks like now:

greg@garage:~$ sudo nano /etc/hal/fdi/policy/preferences.fdi

<!--  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->

Since doing that, My auto mounting problem has disappeared.

g

---

### Post by xeddog on 2008-10-19
Hi all,

I am having this same problem on my system, but unfortunately for me, I don't quite understand the resolutions that some people have posted.  From what I gather, most people are having problems with an ntfs drive, but I am not.

I have two internal IDE hard drives.  sda is a 320GB disk I used for my Hardy install, and sdb is a 200GB disk used for my Intrepid install.  When I boot Hardy on sda1, the 200GB (which is sdb)disk is shown as a "place" and I can click on it and mount it.  But when I boot Intrepid on sdb, the 320GB (which is sda) disk shows up in "Removable Media".  I can still click on it there and mount it, but I still have one additional problem.  I cannot map that drive from my Windows XP machine.  

Here is my fdisk -l results from the Intrepid install on sdb:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4f51b05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38539   309564486   83  Linux
/dev/sda2           38540       38913     3004155    5  Extended
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8283fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23948   192362278+  83  Linux
/dev/sdb2           23949       24321     2996122+   5  Extended
/dev/sdb5           23949       24321     2996091   82  Linux swap / Solaris


And here is my /etc/fstab from sdb:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6b1c38d3-e7f8-4afe-b0f6-50c37203213d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=b59ecd66-915a-42f2-806b-35b8cfa61249 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0


I can see that sda is not listed in fstab, but why not?  I could probably figure out how to fix it by comparing the fstabs from both systems, etc., but if this is a reported bug I could wind up making a problem for the "fix".  



xeddog

---

