---
title: "how do i reconnect to my home folder partition"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Mickser_52 on 2010-02-24
I did a fresh install of ubuntu 9.10 yesterday while trying to get my wireless working again (a problem for another forum). I have previously put my home folder on a separate partition. Having foolishly assumed that it would pick up the home folder as such after the install. Of course it didn't. The partition is still intact but it is not being recognised as the home folder.

How do I reconnect. Is it just a matter of editing the fstab file?

Any help appreciated.

---

### Post by ndefontenay on 2010-02-24
I saw a how to on moving home to a new partition. Keep looking a bit. It's somewhere on this forum.

I'll look as well.

Nico

---

### Post by Mickser_52 on 2010-02-24
Thanks for response. Just to clarify: I had moved my home folder to a new partition several months ago and it was working perfectly until i did the fresh install.

---

### Post by pmlxuser on 2010-02-24
on installing you were supposed to indicate which partition you want maounte as /home.

however if you have no intention of re installing the easiest is to auto mount the partition you home is on , on startup and i would just remove my current home, create a symbolic link to the partition

---

### Post by Mickser_52 on 2010-02-24
If I knew then what I know now!

Is the best solution to reinstall again or create the symbolic link     (and how would I do that?)

---

### Post by amsterdamharu on 2010-02-24
When you get the login screen do not login.
Press control + alt + F1 and log in there (non graphic)

If you know what partition your home folder is on than you can edit fstab.

```
sudo nano /etc/fstab
#Add the following line:
/dev/sda2 /home               ext3    relatime,errors=remount-ro 0       1
exit

```I am assuming your home partition is /dev/sda2 (first harddisk second partition) and ext3.
Save the file and presst control + alt + F7 and login.

There might be a problem with home not being empty and you cannot mount it then you should first remove all files from home before editing the fstab:

```

sudo su
umount /home
ls -l /home
rm -R /home #make sure home is not mounted to the partition you used
mkdir /home
nano /etc/fstab
#Add the following line:
/dev/sda2 /home               ext3    relatime,errors=remount-ro 0       1
exit
exit

```

---

### Post by Mickser_52 on 2010-02-24
Many thanks,
Editing fstab solved the problem

---

