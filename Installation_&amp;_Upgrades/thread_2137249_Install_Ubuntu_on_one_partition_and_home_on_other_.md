---
title: "Install Ubuntu on one partition and /home on other partition?"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by Malmberg on 2013-04-20
Gents, The Newbie has a new problem :-)
On my harddrive I have made a 30GB partition and a 470GB partition.
I THINK I have installed the OS on the small partition and /home on the large partition!
How do I check this?

Thanks in advance
Malmberg

---

### Post by Cheesemill on 2013-04-20
What's the output of...
```
df -h
```

---

### Post by Malmberg on 2013-04-20
> **Cheesemill said:**
> What's the output of...
```
df -h
```

```
sbm@NX9420:~$ df -h
Filsystem      Størr Brugt  Tilb Brug% Monteret på
/dev/sda1        29G  3,1G   25G   12% /
udev            494M  4,0K  494M    1% /dev
tmpfs           201M  1,1M  200M    1% /run
none            5,0M     0  5,0M    0% /run/lock
none            502M   80K  502M    1% /run/shm
/dev/sda3       429G   51M  407G    1% /home


```

---

### Post by Cheesemill on 2013-04-20
Yep, you have / on a 29GB partition and /home on a 429GB partition.

---

### Post by Malmberg on 2013-04-20
Hi Cheesemill,
Thanks!
Im not sure what to do when (not IF, but when) I need to reinstall the OS?
How do I keep my /home during reinstall?
Or- shall I start a new thread with this question?
Cheers

---

### Post by oldfred on 2013-04-20
You have to use Something Else or manual install. You choose sda1, select format as ext4, and mount as / (root). That partition will be totally reformatted & new install will be there. And you select sda3, mount as /home but DO NOT format it. Then it will not change anything other than add updates.

Still best to have good backups. If you install a lot of apps, you may want to make a list with dpkg to make it easy to reinstall.
I also have made a few manual system changes to files in /etc. Those would get overwritten, so I make copies into my /home so my backup saves them, but do not auto copy back as a new install may or may not need them or may need different. But since I may want them it is worth saving.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by Malmberg on 2013-04-21
Hi Oldfred,
Thanks - Ill print this, so I know what to do when I mess my OS up!

Cheers

---

