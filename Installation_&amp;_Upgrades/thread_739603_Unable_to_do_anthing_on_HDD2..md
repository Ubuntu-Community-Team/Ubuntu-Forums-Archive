---
title: "Unable to do anthing on HDD2."
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by duo001 on 2008-03-29
Let me start off by saying that I am new to Linux, and I am attempting to learn something new, well something better.
With that said, I installed Ubuntu 7.04, then upgraded to 7.10 with no problems. I then installed a second drive in the machine, using GParted I formatted the drive.
However I am unable to save any files to the drive. I have tried using chown to give myself ownership. Also I have tried chmod, and that gave an error of 
"chmod: changing permissions of `/dev/sdb1': Operation not permitted".

Any help would be appreciated. 

Thank You, 
Duo

---

### Post by scragar on 2008-03-29
check the drives mount options:
```
mount
```
check for either **rw**(read write) or **ro**(read only) on the partition, you may not even have it mounted as rw.

```
mount -w -o remount /dev/**device** /media/**mount point**
```

---

### Post by duo001 on 2008-03-30
Here is what I have done to get my 2nd HDD up and running.
I did find this data on another site, though I have modified it to fit my needs, I would like to give the original author credit: 
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

Create a mount point for the partition:
```

sudo mkdir /media/storage

```
Then make a backup of the /etc/fstab file:
```

sudo cp /etc/fstab /etc/fstab_backup

```
Next edit the /etc/fstab file:
```

sudo nano /etc/fstab

```
Once in there, add in this line:
```

/dev/sdb1 /media/storage ext3 defaults 0 0

```
Then save (Control-X), confirm (Y), and exit (Enter).
Since we've made changes to the /etc/fstab file, we need to have Ubuntu acknowledge those changes:
```

sudo mount -a

```
Now we need to give it the proper permissions.
```

sudo chown -R duo:duo /media/storage
sudo chmod a+rwX -R /media/storage

```
Now the partition is mounted in the /media/storage folder and is ready for use!

---

