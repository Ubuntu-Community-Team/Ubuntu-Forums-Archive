---
title: "how to make dos partition visible"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Amellou on 2009-11-13
Hi 

While I was installing ubuntu on a partition X I had a free space that vista did not want to format because I already have another logical partition Z, so during the installation of ubuntu it offered me to format it in one of the option, so I did but I choosed somewhere there to mount point dos, I am new to Ubuntu so I thought maybe that would make it readable in vista too. 
So now when I log in to my Ubuntu i can not view the new partition in my computer folder, but when I go to System>Administration>System Monitor, it shows it there, and I can access it from there, in the same windows it shows DOS under directory.

What should I do to make it visible in Places?

Thank you

---

### Post by lemming465 on 2009-11-15
Do you know what type of filesystem you formatted that "dos" partition with?  To be visible in both Vista and Linux it should probably be fat32/vfat, and the partition type id code needs to match the filesystem format (e.g. type "b" hex).  Can you post the output of```

mount
sudo fdisk -lu
sudo blkid
```
for us?  Then we can give more specific advice.

---

