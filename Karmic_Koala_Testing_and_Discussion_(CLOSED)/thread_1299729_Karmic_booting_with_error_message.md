---
title: "Karmic booting with error message"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by forficula on 2009-10-24
Hi, I have just installed Karmic and get an error message during booting - something to the effect there was an error mounting a partition (swap, I think) and that I can press esc to go to the recovery console.  The message is quite quick, so haven't got it all and the system boots OK - any ideas?  Many thanks, d

---

### Post by drs305 on 2009-10-24
If your swap didn't get mounted and you run the first command the second line will probably be all zeros. If so, your swap isn't mounted.  
```

free -m
sudo swapon -a

```

If you run the second command and get errors, it probably means your swap UUID isn't correct. If so, open your fstab and compare the UUIDs to the results from:
```

sudo blkid -c /dev/null

```

If they are different, change the entries in fstab, save the file, then try the swapon command again.

---

### Post by forficula on 2009-10-24
Many thanks, the results are below but I am not sure how they fit with the explanation:

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013       1966         46          0         20       1515
-/+ buffers/cache:        431       1582
Swap:         1906         12       1893

$ sudo swapon -a

swapon: cannot find the device for UUID=696d08d1-3fa7-499c-aaf2-85d46637b1b1

$ sudo blkid -c /dev/null
/dev/sda1: UUID="0cf4089d-57ca-432d-abf8-6aa5edd46f99" TYPE="ext4" 
/dev/sda5: UUID="9b193b33-e177-4f03-9804-d3383d1377e3" TYPE="swap" 
/dev/sda6: UUID="78ff7e57-97e8-4281-ba77-cb317ef49895" TYPE="ext4" 
/dev/sdb5: LABEL="data" UUID="6a5b8016-eabb-4c44-84c2-1b9eefd8073b" TYPE="ext4"

---

### Post by mr_steve on 2009-10-24
This means that you should edit your /etc/fstab, find the entry for your swap, and change the UUID to the one returned by blkid, in your case it looks like you want UUID="9b193b33-e177-4f03-9804-d3383d1377e3" TYPE="swap"

---

### Post by drs305 on 2009-10-24
> **forficula said:**
> Many thanks, the results are below but I am not sure how they fit with the explanation:
swapon: cannot find the device for UUID=696d08d1-3fa7-499c-aaf2-85d46637b1b1

$ sudo blkid -c /dev/null
/dev/sda5: UUID="9b193b33-e177-4f03-9804-d3383d1377e3" TYPE="swap" 


Your swap appears to be working. You may have a couple of entries for swap in fstab,  including one for UUID=696.... and that partition no longer exists or has a new UUID. Remove or comment (put a # at the start of the line) any entry with the UUID=696.. designation. 

If you don't find such an entry or don't understand what to do, just post the fstab contents here.

---

### Post by forficula on 2009-10-24
I have just found fstab and the content is below.  I note I have two swap areas on different discs, though I am sure swap was only set up on one.  Many thanks for any advice:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0cf4089d-57ca-432d-abf8-6aa5edd46f99 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=78ff7e57-97e8-4281-ba77-cb317ef49895 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=9b193b33-e177-4f03-9804-d3383d1377e3 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=696d08d1-3fa7-499c-aaf2-85d46637b1b1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2009-10-24
Simultaneous posts.  :-)

Remove the red highlighted section. You will have to do it as root. That will fix things up.
```

gksu gedit /etc/fstab

```

> **forficula said:**
> I have just found fstab and the content is below.  I note I have two swap areas on different discs, though I am sure swap was only set up on one.  Many thanks for any advice:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0cf4089d-57ca-432d-abf8-6aa5edd46f99 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=78ff7e57-97e8-4281-ba77-cb317ef49895 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=9b193b33-e177-4f03-9804-d3383d1377e3 none            swap    sw              0       0
[COLOR="Red"]# swap was on /dev/sdb2 during installation
UUID=696d08d1-3fa7-499c-aaf2-85d46637b1b1 none            swap    sw              0       0[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by forficula on 2009-10-24
Brilliant, did the trick.  Many thanks for your help.  d

---

