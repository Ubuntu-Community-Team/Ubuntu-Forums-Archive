---
title: "The external hard drive is not useable after laptop come out of sleep mode"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-27
Hi
I have an external hard drive which is formatted as NTFS.
When my laptop goes to sleep mode and come out of sleep Ubuntu shows an error titled: **Unable to mount DriveB**and the content of error dialog is as follow:

```


Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc2 is already mounted on /media/DriveB
mount faile

```

To recover from this error, I should close all process which are accessing this drive and then perform the following commands:

```

sudo umount /media/DriveB
sudo mount -a

```

Is there any solution for this problem?

Thanks

---

### Post by legolas_w on 2009-10-28
Any comment?


Thanks

---

