---
title: "System is trying to mount a drive that is not present"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by almikul on 2012-02-01
Hi,

When I installed Ubuntu alongside windows, I decided to make custom partitions. So, besides usual ext4 and swap, I created a small fat32 partition to serve as an exchange place between Windows and Ubuntu. My mistake was that at that time, I set it to mount on /media/exchange. 

First it was working fine, but after I manually reformatted this small partition to NTFS, I started having an annoying problem. Now, when I load Ubuntu, I get this message "The disk drive for /media/exchange is not ready yet or present". To ignore this and proceed, I have to push "s" button. It is not a show-stopper, but it is really annoying. Is there any way to prevent Ubuntu from automatically trying to mount /media/exchange ? I tried to delete it as a root from /media and relabeling this partition to another name, but to no avail. Any help would be appreciated.

---

### Post by divague on 2012-02-01
You have to edit the /etc/fstab file, open a terminal and put

```
sudo gedit /etc/fstab
```

when the file opens look for the line that mounts that partition and put a # before it, save it and you shouldn't have more problems with that.

---

### Post by almikul on 2012-02-02
Thank you very much, divague! Worked like a charm :)

---

