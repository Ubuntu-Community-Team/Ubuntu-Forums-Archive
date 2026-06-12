---
title: "How to view a slave NTFS drive?"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by driggins on 2006-10-12
Greetings,

Linux newbie here.

I need to copy data from an old Win 2K drive. I have set it up as a slave drive and it appears within Ubuntu as hdb1.

Within File Browser, it appears to show up as Local Disk. When I double-click, I get:
"The Folder Contents Could Not Be Displayed. You do not have the permissions necessary to view the contents of "disks-conf-hdb1"

This seems to be a simple fix - can someone guide me as to how I can browse and copy data from this drive?

Thanks,
daryl

---

### Post by confused57 on 2006-10-12
Maybe this howto will help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by driggins on 2006-10-12
Thanks. I can access the NTFS files now.

I am curious about an item in the How To. It referenced a command:
"sudo unmount"

But when I attempt to execute, it gives me a command not found error.

I rebooted and got the same result.

---

### Post by christhemonkey on 2006-10-12
That should be 
:
```
sudo umount 
```

Note there is no `n` in that command.

---

### Post by Coelocanth on 2006-10-12
> **driggins said:**
> Thanks. I can access the NTFS files now.

I am curious about an item in the How To. It referenced a command:
"sudo unmount"

But when I attempt to execute, it gives me a command not found error.

I rebooted and got the same result.

It's not "sudo **un**mount", it's:

sudo **u**mount

No 'n' after the first 'u'. ;)

*edit* Bah! The monkey beat me to it!

---

### Post by baalthazar on 2006-11-27
hello ppl??
i am having exactly the same problem, but now thanks to this i know how to fix it... i just have one more question,
right now i have my 250 DD sata partitioned in four (i know, bad idea) but i want to mix the two last partitions into one without loosing the winfiles that are there so id have 3 partions in total.

can some1 tell me on how to fix this?:neutral:

ps. mounting the windows partition wont cause any troubles, right? i heard long ago that if windows found something about linux would somewhat try to do something to harm it..

---

### Post by taurus on 2006-11-27
If that harddrive is not mounted right now, you can use gparted from Ubuntu to resize it.  Otherwise, you need to use either the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), to resize it...

---

### Post by baalthazar on 2006-11-27
but are you sure it wont kill my DD? because i did something similar and killed it for some time and had to ask a friend to fix it back (that time i was using windows and partition magic, cuting the size of the primary partition so i could install ubuntu)

btw, mounting the windows partition wont cause any troubles, right? i heard long ago that if windows found something about linux would somewhat try to do something to harm it..

---

### Post by taurus on 2006-11-27
It will not kill it if you do it right!!!  From that website, there are some screenshots so I recommend you look at them first to know what they are before you start running on your harddrive.

---

### Post by baalthazar on 2006-11-29
greetings again ppl..
well.. i didt mess with the partitions because windows was working as well as it should, so i didnt care to fix all 4 partitions, and i also followed the tutorial at psycocat to umount the drives, the thing is, that since i had 3 partitions in ntfs that i coudnt see, wen i did it, 2 remained as folder and one was kept as an icon at the desktop at was viewable. does anyone knows how to turn the other 2 folders as icons too?

---

### Post by taurus on 2006-11-29
You want to mount the remaining two partitions, ntfs, on Ubuntu!

---

### Post by baalthazar on 2006-11-29
was that a question or a comment?

following that two it copied all the files to the folders, but the last partition stayed as a partition, how do i make the other two that look like a folder, look like icons or an actual partition :-?

---

### Post by taurus on 2006-11-29
How do you mount them?  what does your /etc/fstab look like then?

```
cat /etc/fstab
```

---

### Post by baalthazar on 2006-11-29
thanks for the support dude, ill tell you when i arrive home were i have my ubuntu box...

---

### Post by baalthazar on 2006-11-29
ok.. for some reason the other drive that was as an icon, now is as a folder.. 

here is the info
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/sda5 /D ntfs nls=utf8,umask=0222 0 0
/dev/sda6 /e_drive ntfs nls=utf8,umask=0222 0 0
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2006-11-29
How about 

```
sudo fdisk -l
```

---

### Post by baalthazar on 2006-11-29
the info about that??

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3906    31374913+   7  HPFS/NTFS
/dev/sda2           12417       30400   144456480    f  W95 Ext'd (LBA)
/dev/sda3            3907       12416    68356575   83  Linux
/dev/sda5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sda6           25497       30400    39391348+   7  HPFS/NTFS
/dev/sda7           12417       12748     2666727   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2006-11-29
Is there any chance you're using hibernate or things like that?

---

### Post by baalthazar on 2006-11-29
> **taurus said:**
> Is there any chance you're using hibernate or things like that?

erm.. well... i doubt im using hibernate, unless is a default option.. but i have no idea of what your talkin about... :mrgreen::confused:  LOL
sorry...:-?

---

