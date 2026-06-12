---
title: "How to use my old /home partition after fresh install"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by paks.dreamer on 2010-05-25
I couldn't find a clear answer to my question in the forum or documentation, but if it's been answered before, just point me in the right direction.

On my last upgrade, I decided to go with a fresh install, and make a separate **home **partition, to preserve my files for future upgrades.  Now I want to upgrade again (fresh install) and I'm a bit stuck on the manual partitioning part.

I'm assuming I direct the fresh install to my old **root** partition, overwriting it, and leave the **home** (and **swap**?) partitions as they are, so they're not formatted, but won't this just create a fresh, blank /home folder inside my **root** partition along with the upgrade?**  How do I delete this new /home folder and redirect my OS to use my old *home* partition in its place?**

Please be specific.  I have a good technical knowledge, but I'm relatively new to ubuntu and its commands.

Thanks for any help in advance. :]

---

### Post by ubername on 2010-05-25
You nearly have the answer. In the manual partitioning step, use the old "/" partition as you described (if you want to - you could just leave it and create another partition). The step which you are missing is as follows:
Whilst in the manual partitioning step you also select your existing "/home" partition and select to mount that as /home, without formatting it. That should set your existing home partition as home for your new install. (Swap will sort itself out)

---

### Post by paks.dreamer on 2010-05-25
I had no idea I could allocate a partition without formatting it!  Thanks so much for your quick response ubername. :]

---

### Post by ubername on 2010-05-25
You're welcome. Just make sure the tick box for "format" is clear after you have selected the partition.

---

### Post by ronparent on 2010-05-25
During the partitioning step just make the manual partitioning your choice, designate your current /home partition as /home for the install without formating it. Anything new required for the install in /home will be written to it, but all your data and most of your preferances will be left as they were. The key is to not **format**. Also make sure to enter the same user name and password as previously used. Doing it this way will eliminate the need to take ownership of your old home after the install. Post if you need more help.

---

### Post by paks.dreamer on 2010-05-26
Thanks ronparent. :]

That was the cleaniest & easiest install I've done yet.  Separating the home folder was the best move I've made.

---

### Post by achu91 on 2013-04-30
i did as u had mentioned above .as i novice user i didnt know the type of partition of / home;so i just selected ext2. and i didnt check the format check box.But after installing ubuntu i noticed that all the data is erased.Is there any way to get back the data;or it happens like it.Please advice me so that i can do that next time.

Please reply.

---

### Post by brianw0667 on 2013-04-30
If you did not select format it probably did not erase the data it just has not mounted it. The install will create a blank /home folder then during boot it reads the file /etc/fstab and mounts folders based on that. There was probably an issue with mounting.  If your /home folder was not on a separate partition but part of the single partition under the root "/" folder then it would get erased when / is formatted.

If you open a terminal and type 'sudo fdisk -l' (without the quotes and that is a lower case L) what do you get?  Depending on your drive you should see something like:

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          208845    82124279    40957717+   7  HPFS/NTFS/exFAT
/dev/sda3        82124798   601712639   259793921    5  Extended
/dev/sda4       601714688   625139711    11712512    7  HPFS/NTFS/exFAT
/dev/sda5        82124800    84076543      975872   82  Linux swap / Solaris
/dev/sda6        84078592   601712639   258817024   83  Linux


---

### Post by achu91 on 2013-04-30
the /home was on a seprate partition.

this isthe output by typing sudo fdisk -l

[COLOR=#ff0000]suja@suja-Inspiron-1525:~$ sudo fdisk -l
[sudo] password for suja: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS/exFAT
/dev/sda2        61432621   312580095   125573737+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   122865119    30716248+   7  HPFS/NTFS/exFAT
/dev/sda6       122865664   132630527     4882432   82  Linux swap / Solaris
/dev/sda7       152164352   312580095    80207872   83  Linux
/dev/sda8       132632576   152152063     9759744   83  Linux

Partition table entries are not in disk order
suja@suja-Inspiron-1525:~$ [/COLOR]

i thinkwhen i changed form type to /ext 2 ,the home parttion might not have got formated.Is there any way to get the data back.

---

### Post by brianw0667 on 2013-05-01
if you use a terminal again and type the command mount it will show you which one is your / partition (either sda7 or sda8). Mine shows as:

> mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)


The other one should be your home partition. You can check it by mounting it on the /mnt partition (i.e sudo mount /dev/sda8 /mnt) and that will let you browse the contents to make sure they are there.  then you can unmount it with sudo umount /mnt

if you get an error when you try to mount saying something about the type try sudo mount -t ext4 /dev/sda8 /mnt

You can then check your fstab file to see what is in it cat /etc/fstab and see if /home is in there.  Mine shows:

> cat /etc/fstab
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=f8207c5f-4f6a-4563-b7a9-1b863a3787d8 /               ext4    errors=remount-ro 0       1
UUID=66cca1e9-7265-4ab0-98dc-2258b71e4ed0 none            swap    sw              0       0

If you check and the contents are there and it is showing in the fstab file then it will probably be the type field or the UUID field.

---

### Post by brianw0667 on 2013-05-01
I found a page ([http://www.tuxradar.com/answers/558]("http://www.tuxradar.com/answers/558")) which describes how to find the UUID and a couple other things.  To find the UUID use > sudo vol_id /dev/sda5

After checking I found that vol_id is not the right one to use. Try: > sudo blkid This should tell you the UUID and type as well.


An example fstab entry for /home might be:

> # Separate Home
# /dev/sda7
UUID=413eee0c-61ff-4cb7-a299-89d12b075093  /home  ext3  nodev,nosuid,relatime  0  2

I found that here: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

Some explanations say that you can use auto instead of ext3 or ext2 etc... for the filesystem type.

---

