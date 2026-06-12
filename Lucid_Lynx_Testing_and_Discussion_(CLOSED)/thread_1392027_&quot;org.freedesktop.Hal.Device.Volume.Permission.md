---
title: "&quot;org.freedesktop.Hal.Device.Volume.PermissionDenie d&quot; on disk mounting"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ubuntiac on 2010-01-27
Moved from [here]("http://ubuntuforums.org/showthread.php?p=8578453#post8578453") as apparently this is the more correct forum for this.

Ever since the KDE 4.4 beta packages came in, I've been unable to mount drives either with the new "removable devices" section in system settings (although my drives are IDE/SCSI) or in Dolphin. I just get an error:
> 
An error occurred while accessing 'Seagate15tb', the system responded: org.freedesktop.Hal.Device.Volume.PermissionDenied : Refusing to mount device /dev/sda1 for uid=1000

Manual disk mounting by the command line works fine.

It's obviously permissions of some description, but I'm wondering how one would fix this. I'm already a member of the disk an PolkitUser groups.

I'm on Kubuntu Lucid AMD64 with KDE 4.4 RC1 (4.3.95)
with 1 ide ext4 partition, 1 ide connected ntfs partition and 1 scsi connected ntfs partition. All fail in the same way. 

Any ideas?

---

### Post by k64 on 2010-01-27
Have you tried re-logging in via the command line as root?

```
gksu killall Xorg && gksu startx
```

---

### Post by cariboo on 2010-01-27
> **k64 said:**
> Have you tried re-logging in via the command line as root?

```
gksu killall Xorg && gksu startx
```

Why would want to run the desktop as root, any chages you make will end up in /root.

Gksu does not work from the command prompt.

---

### Post by koso on 2010-01-28
This is probably regression, It was few time already fixed in Karmic, and it returns and returns ... there was some HAL patch for it, but cant find it now.

Other posibility should be to mount disk as root (kdesu dolphin)

---

### Post by nbensa on 2010-03-22
Hello,

after upgrading to lucid beta1, I got bitten by this bug.

Did anyone find a solution?

Thanks,
Norberto

---

### Post by VMC on 2010-03-22
Is it related to [**_this_**]("http://ubuntuforums.org/showthread.php?t=1434702") topic? If so there's a hack to fix it.

---

### Post by Ubuntiac on 2010-03-22
Seems that it's a KDE bug. It's been put as a goal to be fixed by the next beta release of Kubuntu.

---

### Post by Sciamano on 2010-04-07
I got here because I'm having this problem with Karmic.
It's been working for some time (read hours), then I rebooted after installing a few updates and the nvidia drivers, and it suddenly stopped mounting my drive again.
It's frustrating!

---

