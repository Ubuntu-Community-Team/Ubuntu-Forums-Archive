---
title: "mounting problem - only root can do that"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by tracystravels on 2007-12-20
I am trying to force mount my secondary hard drive using the command:

mount -t ntfs-3g/ dev/ sdb1/media/K_T Private Drive -o force

I get the reply

mount: only root can do that

How do I get to root. Also, will the command I used work for a drive named "K_T Private Drive" with the nomenclature I used.

Thank you in advance,
Tracy

---

### Post by Partyboi2 on 2007-12-20
Put sudo in front
```
sudo mount -t ntfs-3g/ dev/ sdb1/media/K_T Private Drive -o force
```more on sudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Edit: I am not sure if you can have spaces between K_T Private Drive.

---

### Post by tracystravels on 2007-12-20
the actual of the name of the drive is "K/T Private Drive". How would I put that in the command?

Thank you,
Tracy

---

### Post by delphiguy on 2007-12-20
The Name of the Drive doesnt matter in this case, what you want to get is
the Device name of the Drive.

if you do 
sudo fdisk -l

it should give you a list of all harddisk that are in your system.

Using your Example, i assume that the drive is /dev/sdb1
so to mount it you would type
sudo mount -t ntfs-3g /dev/sdb1 /media/mydrive

Of course mydrive should exist in your /media directory.  If not you have
to create it by doing:
sudo mkdir /media/mydrive

Of course you can change mydrive to anything that you prefer.

hope this helps.

---

### Post by tracystravels on 2007-12-20
Thank you so much!!! That resolved the problem, now I can go drink!

Tracy

---

### Post by delphiguy on 2007-12-20
Your very much welcome.

---

