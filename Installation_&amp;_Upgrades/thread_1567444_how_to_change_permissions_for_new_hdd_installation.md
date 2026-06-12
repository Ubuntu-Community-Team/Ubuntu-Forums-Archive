---
title: "how to change permissions for new hdd installation"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by SGC622 on 2010-09-03
I just got a 1.5 TB HDD for my computer as a Backup/media storage device, i installed it, and formatted it to ext4, through gparted, my question is why dont i have access to move files into that hard drive?, im somewhat of a beginner, i've been running kubuntu for about a year now, and i just came across this problem. Is there a command in terminal that i can change permissions or should i log in as root and set permissions that way, i mean i cant even move files into that folder yet, i have to type in my password to even open it. All the help is appreciated thanks!

---

### Post by SGC622 on 2010-09-03
ok so i found some info on how to enable root and i did as follows in terminal with no luck, it says root is not enabled when i try and login as root
> 
scott@Home:~$ sudo -i
root@Home:~# passwd -u root
passwd: password expiry information changed.

apparently i can get into root fine in terminal but as far as the desktop login, as stated above i still cant

---

### Post by confused57 on 2010-09-03
You can run "sudo fdisk -l" to determine which is your storage drive. Then change ownership of the partition:
```
sudo chown -R scott:scott /dev/sdb1
```
Replace /dev/sdb1 with the results from fdisk -l
Then reboot for the change to take effect.

---

