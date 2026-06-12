---
title: "Cannot Read External HD"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by darkwarrior0404 on 2006-03-17
I was just curious if their was any way at all to read the ntfs file system I have on my external hard drive, I tried looking in the NTFS thread, but nothing really seemed to work, any help would be great

---

### Post by aysiu on 2006-03-17
Plug in the drive and then can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by darkwarrior0404 on 2006-03-17
Well I figured it out, (kinda new to Linux) and can't have any weird symbols in the name, and I had a "/" in the name of it soooo I renamed it and it worked fine lol.. Thanks tho. Maybe one day I'll have enough common sence to run Linux with ease

---

