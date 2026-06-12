---
title: "Update manager crashes instantly when doing updates"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shamusl on 2009-03-13
Whenever I open update manager, even through failsafe terminal I receive the following error in the terminal as soon as I click the "Install updates" button: 

```
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 562, in on_button_install_clicked
    self.cache.checkFreeSpace()
  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py", line 907, in checkFreeSpace
    if self.config.getWithDefault("Aufs","Enabled", False):
AttributeError: 'MyCache' object has no attribute 'config'


```

Anyone know what to do from here?

---

### Post by taavikko on 2009-03-14
Update via CLI,
there's been several upgrades on update-manager, I've personally havent used U-M a long time.

```
sudo aptitude update && sudo aptitude full-upgrade
```
If it wants to remove any packages, please let us know, so we can tell you if it's wotrh going through

---

### Post by forumache on 2009-03-14
It crashed for me too (like two days ago) and I updated from CLI. Since then, no problems, the bug was solved, further updates can be done from Update Manager.

---

### Post by Peter09 on 2009-03-14
Have the same problem after and upgrade this morning when Upgrade manager closed unexpectedly. No crash dump because of 'lack of available memory'. Issuing the command shown previously results in a segmentation fault.

Edit: trying for a crash report results in a crash...

Edit: Section of Syslog

> ar 14 08:14:55 toshsat kernel: [  100.656610] update-manager[3848]: segfault at e649e100 ip b7f54613 sp bffc818c error 4 in libc-2.9.so[b7edd000+15c000]
Mar 14 08:15:11 toshsat kernel: [  117.217068] apt-check[3867]: segfault at e8bf9100 ip b7f66613 sp bffdbd8c error 4 in libc-2.9.so[b7eef000+15c000]
Mar 14 08:16:59 toshsat kernel: [  224.472238] aptitude[3982]: segfault at e8891100 ip b7a4e613 sp bf94ab2c error 4 in libc-2.9.so[b79d7000+15c000]
Mar 14 08:17:02 toshsat /USR/SBIN/CRON[4049]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 14 08:20:01 toshsat /USR/SBIN/CRON[4194]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Mar 14 08:20:04 toshsat kernel: [  410.157910] apport-gtk[4186]: segfault at e6abe100 ip b7f4a613 sp b6281eec error 4 in libc-2.9.so[b7ed3000+15c000]
Mar 14 08:20:05 toshsat kernel: [  411.239895] apt-check[4331]: segfault at e8c58100 ip b7f3d613 sp bfeb280c error 4 in libc-2.9.so[b7ec6000+15c000]
Mar 14 08:20:38 toshsat kernel: [  444.043967] apport-gtk[4479]: segfault at e649c100 ip b7dcd613 sp b5c5feec error 4 in libc-2.9.so[b7d56000+15c000]
Mar 14 08:21:34 toshsat kernel: [  500.121574] apport-gtk[4561]: segfault at e62ec100 ip b7ec5613 sp b5aafeec error 4 in libc-2.9.so[b7e4e000+15c000]

---

### Post by thegodsquirrel on 2009-03-14
I am running the code now I will let you know if it fixes UM.

The update only wanted to remove 4 packages, I could not get a copy before they were removed from the terminal

---

### Post by shamusl on 2009-03-15
> **taavikko said:**
> Update via CLI,
there's been several upgrades on update-manager, I've personally havent used U-M a long time.

```
sudo aptitude update && sudo aptitude full-upgrade
```
If it wants to remove any packages, please let us know, so we can tell you if it's wotrh going through

Didn't try to remove anything, but the update manager now works, thanks!

---

