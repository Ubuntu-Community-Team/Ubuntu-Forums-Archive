---
title: "How do I permanently delete Windows?"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by wilwil0 on 2011-05-30
I want to get rid of my Windows partition and delete every last vestige or residual information from the laptop. 

I installed Ubuntu 11.04 and used BleachBit's Free Disk Space to overwrite the files once there.

Is there any data left like recovery data points? I would like ideally to delete everything.

---

### Post by wilwil0 on 2011-06-02
Anything?  :-?

---

### Post by EmporerD on 2011-06-02
Do you still have the windows partition? If you do just boot into live cd, open gparted and merge it into your ext4 partition and that will pretty much do it.

---

### Post by wilwil0 on 2011-06-02
No, I deleted the partition. But I don't want to recover it. Don't worry, I'm haven't just accidently deleted an entire operating system that I was relying on ;)

I want to delete every bit of Windows from it and all the data that can be used to recover Windows (even if you had the boot disk) or sensitive data, etc.

I deleted the Windows partition and overwrote the data a few times with BleachBit's "Free Disk Space" action. Does that mean *all* the data is gone and it is *impossible* to recover the Windows partition? I never understood recovery points in Windows but have I deleted all of those?

---

### Post by royalflush5 on 2011-06-02
If you really want to remove everything on your drive, I would suggest Darik's Book and Nuke: [http://www.dban.org/.]("http://www.dban.org/")
I haven't personally tried it with two partitions on the same disk, I've only used it on multiple disks, but I would assume it would work the same way.
Oh, and by the way, you will irrecoverably lose all the data on the HDD (or partition) you use it on, so be careful!!! And avoid the quick wipe function, as that will erase everything on every disk connected to your pc, including flash drives!
Good luck!

---

### Post by mörgæs on 2011-06-02
(please ignore)

---

### Post by wilwil0 on 2011-06-04
> **royalflush5 said:**
> If you really want to remove everything on your drive, I would suggest Darik's Book and Nuke: [http://www.dban.org/.]("http://www.dban.org/")
I haven't personally tried it with two partitions on the same disk, I've only used it on multiple disks, but I would assume it would work the same way.
Oh, and by the way, you will irrecoverably lose all the data on the HDD (or partition) you use it on, so be careful!!! And avoid the quick wipe function, as that will erase everything on every disk connected to your pc, including flash drives!
Good luck!

I've already deleted the partition but as there is nothing on the Ubuntu OS I installed there is no data I would really care about losing. How does this nuke differ from deleting and overwriting the disk?

Also when you mention wiping everything connected to the PC, do you mean if I have a USB stick in the PC at the same time?

---

