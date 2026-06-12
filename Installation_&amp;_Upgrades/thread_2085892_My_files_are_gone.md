---
title: "My files are gone"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by La Mangra on 2012-11-19
My files are gone, but I don't care. In the moment I've moved to Ubuntu I feel a relief

Previously I had 4 partitions, the Windows 7 were installed on disk C. Is there a chance the files are still out there on the disks E, F and G or had I lost them forever?

---

### Post by Erik1984 on 2012-11-19
That depends on how you did the install (entire disk?). You can list all your partitions with the command:
```
sudo fdisk -l
```

In case the NTFS partitions are all gone and you definitely need data that was one there: STOP USING THE DISK and start Ubuntu from a Live CD. From there you can run recovery tools like Photorec. Chances are (some of) the data is still somewhere on the disks but you need recovery software to obtain it.

---

### Post by La Mangra on 2012-11-19
> **Euroman said:**
> That depends on how you did the install (entire disk?). You can list all your partitions with the command:
```
sudo fdisk -l
```In case the NTFS partitions are all gone and you definitely need data that was one there: STOP USING THE DISK and start Ubuntu from a Live CD. From there you can run recovery tools like Photorec. Chances are (some of) the data is still somewhere on the disks but you need recovery software to obtain it.


How do I run 
sudo fdisk -l

Never mind, I found it. All is gone

How do I make a Live CD?

Never mind, I don't think I need them anymore. Still, can you tell me, please how do I make a Live CD?

---

### Post by Erik1984 on 2012-11-19
You already have it, it's whatever you used to install Ubuntu (can also be Ubuntu USB stick). I have never used any of these tools myself so can't help you any further other than pointing to this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by ibjsb4 on 2012-11-19
Go here

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

12.10 is the latest release.  Every six months there will be a new release.

12.04 is LTS (long term support) and will be supported for five years.

Also choose if you want to  run 32 or 64 bit system.  Most people choose 64 bit if there machine supports it.

---

### Post by La Mangra on 2012-11-19
Thank you

---

