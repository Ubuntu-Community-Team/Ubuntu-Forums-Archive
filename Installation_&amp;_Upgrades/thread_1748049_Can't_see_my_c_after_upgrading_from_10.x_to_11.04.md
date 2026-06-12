---
title: "Can't see my c:\ after upgrading from 10.x to 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by eder.pereira on 2011-05-03
Hi,

I found no similar threads so I created a new one.

I have w7 and ubuntu on a dual boot arrange. I need them both and I need ubuntu to see my files in c:\.

Life was fine before the upgrade, but now I just can't see my c: drive.

Some help, please.

---

### Post by dino99 on 2011-05-03
is gparted able to see it ?

from synaptic, check ntfsprogs & ntfs-3g, they should be installed

---

### Post by matt_symes on 2011-05-03
Hi

Check as dino99 said but also what is the output of (from a terminal)

```
sudo blkid -c /dev/null
```and 

```
cat /etc/fstab
```For the first, command enter your password. It will not be echoed to the screen. This is normal.

Copy and paste the results back here. 

If these are fine, it could be an issue with your settings in Unity.

Kind regards

---

### Post by eder.pereira on 2011-05-03
yes it can, but i had to install it though. what now? a simple mount shell input? it's been so long since 6.04 that i'll have to look it up.

---

### Post by eder.pereira on 2011-05-03
blkid has brought me:

/dev/sda1: LABEL="PQSERVICE" UUID="ECE63E08E63DD414" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="B0527AAF527A7A44" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="A8D87C79D87C4818" TYPE="ntfs" 
/dev/sda5: UUID="3b6099c5-561a-4dfc-9ed0-abe7f94a9f5c" TYPE="ext4" 
/dev/sda6: UUID="d9d4b895-1a89-4fd1-9719-ede6065f1440" TYPE="swap" 
/dev/sdb: LABEL="IPOD DE EDM-^P" UUID="BDF7-7C03" TYPE="vfat" 


and cat has brought me:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3b6099c5-561a-4dfc-9ed0-abe7f94a9f5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d9d4b895-1a89-4fd1-9719-ede6065f1440 none            swap    sw              0       0

---

### Post by matt_symes on 2011-05-03
Hi

> **eder.pereira said:**
> blkid has brought me:

/dev/sda1: LABEL="PQSERVICE" UUID="ECE63E08E63DD414" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="B0527AAF527A7A44" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="A8D87C79D87C4818" TYPE="ntfs" 
/dev/sda5: UUID="3b6099c5-561a-4dfc-9ed0-abe7f94a9f5c" TYPE="ext4" 
/dev/sda6: UUID="d9d4b895-1a89-4fd1-9719-ede6065f1440" TYPE="swap" 
/dev/sdb: LABEL="IPOD DE EDM-^P" UUID="BDF7-7C03" TYPE="vfat" 


and cat has brought me:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3b6099c5-561a-4dfc-9ed0-abe7f94a9f5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d9d4b895-1a89-4fd1-9719-ede6065f1440 none            swap    sw              0       0

Open a terminal and type

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda3 /media/windows
``` 

Can you now see the drive mounted ?

Kind regards

---

### Post by eder.pereira on 2011-05-03
Yes, that was it, thank u very much.

Since it's my very first thread here, how do i tag it [solved]?

And whatsmore, do I have to run the mount command every time I log in?

Thanks for all the help, again.

---

### Post by matt_symes on 2011-05-03
Hi

> **eder.pereira said:**
> Yes, that was it, thank u very much.

Since it's my very first thread here, how do i tag it [solved]?

And whatsmore, do I have to run the mount command every time I log in?

Thanks for all the help, again.

Hold on. That will not persist across reboots. To do that you need to update fstab. 

Do you know how to do that ?

Kind regards

---

### Post by dino99 on 2011-05-03
you only need sda5 & sda6 lines enabled in fstab (they are commented in your previous post)

all the mounting job is done on demand by the mountall package

To mark your thread as SOLVED, look at "thread tools" on top, near your first post, that will open an other page where you can find on the left "solved"

---

### Post by matt_symes on 2011-05-03
Hi

> **dino99 said:**
> you only need sda5 & sda6 lines enabled in fstab (they are commented in your previous post)

all the mounting job is done on demand by the mountall package

To mark your thread as SOLVED, look at "thread tools" on top, near your first post, that will open an other page where you can find on the left "solved"

That's very true dino99. I prefer to have certain partitions mounted at startup though and not on demand. I assumed that was what the OP was after.

Kind regards

---

### Post by dino99 on 2011-05-03
let fstab as simple as possible (ubuntu is for humans :))

---

### Post by eder.pereira on 2011-05-03
Hi, friends.

I must admit the little I knew vanished since hardy, I guess, started doing everything for me from the first boot. needless to say this sudden back-to-terminal change caught me unprepared.

But it's ok. Now it's research time again. Thank you all very much for the patience with this newbie and the prompt replies.

---

