---
title: "hdd clone"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by pokethesmot on 2010-09-16
i tried clonezilla ive tried so much stuff and nothing has worked i just want to clone my 200gb hdd to my new 1tb hdd so can some one pleas tell me what to do
i dont even need all my files i just want my ubuntu installation like all my settings and add ons that i have

---

### Post by cj.surrusco on 2010-09-16
Using dd is probably the easiest way (It's also the easiest way to screw things up if you don't use it correctly).
> Suppose you have a 40GB hard disk and a removable hard disk whose capacity is 60GB, and you want to backup all the files from the hard disk to the removable disk. With "dd", it is a very easy task. Again, suppose your hard disk's Unix device name is /dev/sda and the removable disk is /dev/sdb. The following command can copy all the content from /dev/sda to /dev/sdb:

dd if=/dev/sda of=/dev/sdb

Here, if=... sets the source and of=... sets the destination. "dd" doesn't care of the contents of the hard disk. It just reads bytes from /dev/sda and writes them into /dev/sdb. It doesn't know what are files. So, the hard disk file system and how many partitions it has are not important. For example, if /dev/sda is splitted into three partitions, the /dev/sdb will have the same partitions. i.e. "destination" is completely same with "source".

Notice: to execute "dd" you should login as "root" or switch to "root" using "su" command. And you must be careful, a small mistake may cause a serious problem!
source: [http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

---

### Post by pokethesmot on 2010-09-16
> **cj.surrusco said:**
> Using dd is probably the easiest way (It's also the easiest way to screw things up if you don't use it correctly).

source: [http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

i just ran this code and all it did is ask me for my password i put it in and now its not doin nothing

sudo dd if=/dev/sdb of=/dev/sda

---

### Post by cj.surrusco on 2010-09-16
It won't show you any feedback while the command is still running. When the prompt shows up again, then it is finished.

---

### Post by pokethesmot on 2010-09-16
> **cj.surrusco said:**
> It won't show you any feedback while the command is still running. When the prompt shows up again, then it is finished.


oh man ur a life saver now if it messes up will it show me and about how long do you think it will take

---

### Post by TimEnid on 2010-09-16
what was wrong with clonezilla?

---

### Post by pokethesmot on 2010-09-16
> **TimEnid said:**
> what was wrong with clonezilla?
  it would get too 100% done and then say there was an error so it quite

---

### Post by cj.surrusco on 2010-09-16
> **pokethesmot said:**
> oh man ur a life saver now if it messes up will it show me and about how long do you think it will take

Depends on how much of the 200 GB hard drive is filled up, the connections between the hard drives (usb or sata) and the speed of the hard drives. My guess would be about 2 hours, but I can't say for sure. And when it stops it gives a report, which would include any errors.

---

### Post by pokethesmot on 2010-09-17
ok its all done but it wont let me save or delete any files like when i tried to delete something it said permission denied

---

### Post by C.S.Cameron on 2010-09-17
You should be booted from the Live CD or other drive when running dd, not from the drive you are cloning.

---

### Post by cj.surrusco on 2010-09-17
> **C.S.Cameron said:**
> You should be booted from the Live CD or other drive when running dd, not from the drive you are cloning.
It's probably safer, but I don't think it's totally necessary though, right?
> **pokethesmot said:**
> ok its all done but it wont let me save or delete any files like when i tried to delete something it said permission denied
Are you talking about the clone or the original? Or both?

---

