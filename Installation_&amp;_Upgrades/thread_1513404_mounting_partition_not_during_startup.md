---
title: "mounting partition not during startup"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by nab on 2010-06-19
Hi all,

yesterday I did an upgrade from 9.10 to 10.04 and this time it was a mixed experience, most thing worked, but some things like gdm, sound and other setting need(ed) corrections to work again (as in 9.10).

In 9.10 I setup my system so that the second partition (data) was only manually mounted after asking for my password.

After updating 10.04 I asking me at every bootup whether I want to manually mount or skip the mounting. And when I manually mount the partition I don't need any password anymore.

Why did the upgrade change my setting?

Not being an linux-expert, having not documented how I have done the previous setup and being unlucky with google, I could use some pointers in the right direction :-)

Thanks a lot in advance!

PS:
Even if I sound not so happy at the moment I really appreciate the good work that went into ubuntu. After setting up my system after each new installation or upgrade I enjoyed a carefree time with ubuntu (where I forget everything I need to setup my system because it just works as it should).

---

### Post by darkod on 2010-06-19
Check what is /etc/fstab saying about the partition. There might be auto mount after all.

But be careful not to touch inside fstab unless you know what to do, it can make ubuntu unbootable. Just look first!

---

### Post by Morbius1 on 2010-06-19
> And when I manually mount the partition I don't need any password  anymore.
There has in fact been a change to how this is done in Lucid. Before it would ask you for a password and now it does not.
> After updating 10.04 I asking me at every bootup whether I want to  manually mount or skip the mounting.This I'm not too sure about. I don't think I've ever been prompted for a mount during boot.
Why not post the output of the following commands and let as many people as possible see how your are configured:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by nab on 2010-06-20
Sorry for not supplying the info:

sudo blkid -c /dev/null
```

/dev/sda1: LABEL="PQSERVICE" UUID="C48612038611F6A0" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="A85A138C5A135702" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="86F21601F215F661" TYPE="ntfs" 
/dev/sda5: UUID="420bbaed-0f2b-4ac7-bc02-ffafbbfeecce" TYPE="ext4" 
/dev/sda6: LABEL="Daten" UUID="789509c2-9b4c-4eaf-88b5-47de9f3d9b40" TYPE="ext4"

```

cat /etc/fstab
```

# / was on /dev/sda5 during installation
UUID=420bbaed-0f2b-4ac7-bc02-ffafbbfeecce /               ext4    errors=remount-ro 0       1
# /daten was on /dev/sda6 during installation
# UUID=f3c40586-3eb4-453b-8570-bd57a25ffecd /daten          ext4    defaults        0       2

```


In fstab I commented the second line out to get rid of the question at boot time.

At the moment I'm looking into the Gnome-setting for mounting the partitions with password there. 

Or is this the wrong place to look?

---

### Post by Morbius1 on 2010-06-20
The line you commented out is referring to a uuid that doesn't exist:
> # UUID=f3c40586-3eb4-453b-8570-bd57a25ffecd /daten          ext4    defaults        0       2Assuming /daten is referring to this in blkid:
>  /dev/sda6: LABEL="Daten" UUID="789509c2-9b4c-4eaf-88b5-47de9f3d9b40" TYPE="ext4"Then you need to change the line in fstab to look like this:
```
UUID=789509c2-9b4c-4eaf-88b5-47de9f3d9b40 /daten          ext4     defaults        0       2
```[COLOR=Blue]EDIT: Since /daten is not currently mounted you should be able to add the line above and in a terminal issue the following command to mount it without a reboot:[/COLOR]
```
 sudo mount -a
```

---

