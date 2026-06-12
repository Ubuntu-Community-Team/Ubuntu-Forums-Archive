---
title: "how to download ATI drivers via gui?"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by noveevon on 2010-05-14
can anyone tell me how to download the newest 64 bit driver via gui? as after my upgrade from 9.10 i am stuck with gui..

i found codes for installing it in gui so that should be ok, but ive not found any codes for downloading it..although from what ive seen it should not be too hard..

:confused:

---

### Post by dino99 on 2010-05-14
[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

---

### Post by noveevon on 2010-05-14
> **dino99 said:**
> [https://launchpad.net/~xorg-edgers/+archive/drivers-only]("https://launchpad.net/%7Exorg-edgers/+archive/drivers-only")


oki i tried the code:

sudo add-apt-repository ppa: nove/ppa: xorg-edge/drivers-only

and i just get >_ and thats it...

---

### Post by noveevon on 2010-05-14
> **noveevon said:**
> oki i tried the code:

sudo add-apt-repository ppa: nove/ppa: xorg-edge/drivers-only

and i just get >_ and thats it...

think i found a way around it..by using a live cd and then using kdesudo dolphin to move the file to the home folder and install it from there...will try now, if it works i will label this as solved...

---

### Post by noveevon on 2010-05-14
ok, i installed the 10.4 ati drivers, but now my system colapses in gui after a few seconds and gives me:

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda8:clean, 182495/3055616 files, 1915458/12207384 blocks
/dev/sda7: recovering journal
/dev/sda7: clean, 73635/3335808 files, 3387473/13341974 blocks
* starting apparmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

 _                                                                                                        [ok]



and then i cant do anything...i will try supergrub...

---

