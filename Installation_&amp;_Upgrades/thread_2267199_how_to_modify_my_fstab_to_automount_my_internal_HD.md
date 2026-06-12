---
title: "how to modify my fstab to automount my internal HDD"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2015-02-28
i have just installed an external sdd as my 1st boot

i now need to automount my internal hdd as a media storage device

i have tried a few permutations on the fstab but not yet got it right


this is the volume     ```
/media/shantiq/739e22d6-04f7-42f0-89e9-7e99603d63b3
```


this is the current reading of /etc/fstab

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=04555420-77de-4cdb-a0e5-f708d2d109d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=233a9f63-2274-43c1-8e2d-b6d9d5fdd734 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



```


what is the UUID i need to add here at the bottom    i tried


```
UUID=739e22d6-04f7-42f0-89e9-7e99603d63b3   /media/media/  [COLOR=#000000]ext4 defaults,realtime 0 2[/COLOR]

```

based on an old post
but it did not work


what is the correct line/    ?    thanx    shan

---

### Post by nerdtron on 2015-02-28
to determine the correct UUID of the device, you should use:
```
sudo blkid
```

next, be sure that a folder exists for its mount point
```
mkdir /media/extradrive
```

next, unmount the drive so that we can test automounting it.
see that the drive is not mounted.
```
df -h
```

then edit the fstab, lesser options means lesser error. here's a sample for it, no trailing slash on the folder mount
```
UUID=cc7b5de6-680c-4638-a85f-9f114d6253b8      ext4          /media/extradrive      defaults              0       0 
```

Then test the automounting by re-reading the fstab.
```
mount -a
```

Then see the mounted drives again.
```
df -h
```

---

### Post by coldraven on 2015-02-28
I think that /media is where removable devices get mounted. As you have an internal drive I suppose that it would be better to mount it under /mnt.
You could also label the drive to make it more human readable. I would use gparted to create a label, say MYDATA.
So create a mount point
```
sudo mkdir /mnt/myfiles
```
Then your fstab would look like this, I don't know if the blue part is correct.
```
LABEL=MYDATA      ext4 /mnt/myfiles      [COLOR=#0000cd]default              0       0[/COLOR]
```

---

### Post by shantiq on 2015-02-28
thanx guys   used nerdtron's advice on this one

only thing was   order of line is a bit different it seems on here

 ```
UUID=739e22d6-04f7-42f0-89e9-7e99603d63b3  ** /media/extradrive ext4**     defaults              0       0
```

---

### Post by Bucky Ball on 2015-02-28
According to my fstab, this is what you should have:

```
UUID=739e22d6-04f7-42f0-89e9-7e99603d63b3  ** /media/extradrive ext4**     errors=remount-ro       0       1
```

Glad you got it mounting at boot. ;)

---

### Post by shantiq on 2015-02-28
yes Bucky    might  change it to that i think  maybe if i understand why


is not    0   0    for the main boot or do i not understand any of this    [i do not actually]


if i change 0  0    to  0    1    what does it mean?

and what does  ```
[COLOR=#000000][FONT=Ubuntu Mono]errors=remount-ro[/FONT][/COLOR]
```   actually do   if you have the time to explain



sorry i am a TOTAL ignoramus   as regards all things fstab



Thanx for all your help guys    shan


PS    it is working right now with the line mentioned before but i would not mind understanding the detail a bit more

---

### Post by nerdtron on 2015-02-28
See here for the explanations on each column of the fstab. I think the last two columns are fsck file check order and dump.
[http://www.howtogeek.com/howto/38125/htg-explains-what-is-the-linux-fstab-and-how-does-it-work/](http://www.howtogeek.com/howto/38125/htg-explains-what-is-the-linux-fstab-and-how-does-it-work/)


As for the error=remount-ro, when your partition encountered errors during the fsck, it will be mounted as read-only, probably to protect it from further write operations until you run fsck again.

---

### Post by shantiq on 2015-03-01
ha ok    thanx for clarifications N;     anyway your original line   went very well here

---

