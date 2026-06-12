---
title: "Auto-Detection Failed: Hard Disk Not Showing Up"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by AdemoS on 2009-10-23
[size=4]Update 1[/size] 
After unplugging/plugging-back-in the SATA cords, "storage" is now being detected, but I am getting an error on boot
```
sata revalidation error -5
```



[size=4]Original Post[/size] 
I have three physical hard disks (not partitions) in my computer.

1.) One for system files (labeled "/")
2.) One for project files (labeled "projects")
3.) One for storage files (labeled "storage")


#3 in that list---storage---is not being detected...at all.

When I run "blkid" in the terminal, I only see system and projects hard disk. 









Is there any other way to detect the hard disk?



Thanks in advance for your help.

---

### Post by AdemoS on 2009-10-24
[size=4]Update 2[/size] 
After setting up fstab, the hard disk is being detected in Palimpsest Disk Utility as a Un-recognized drive. (which usually means I lost my data)

But at the same time, it's not showing correctly in gParted.

I am offered the ability to re-format the disk in Palimpsest Disk Utility...but doing so would destroy a terrabyte of needed data...



Here's the relevant dmesg report:
[http://paste.ubuntu.com/300689/](http://paste.ubuntu.com/300689/)

---

