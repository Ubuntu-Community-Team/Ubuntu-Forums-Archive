---
title: "Root Problems"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by bluehige on 2004-12-16
I have a weird problem, when i've installed Ubuntu, i haven't seen anywhere an option asking me to insert a root password, so now, i'm trying to mount 2 other slave HDD formatted on ext3, but the konsole ask me to insert a root password, for the root account ( that i don't think to have created  :? ).

Sorry if it's a stupid question, but i'm quite noob on linux. ( i ve installed and used ubuntu today for my first time  8-[  ) before i were on mandrake 9 and suse 9.1 

Thanks for any answer :)

---

### Post by gheorghe_pop on 2004-12-16
Hello!
You don't need a root acount!You just use sudo!So if you want to mount anything you just type:'sudo mount .......' in a terminal.
I would recomand you taking the unoficial ubuntu starter guide(It's very easy to use).You could find it here:[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

---

### Post by bluehige on 2004-12-16
thx, coz i come from suse, and each time to mount is : 

su
pass
mount.....

i ll try what u said :) thx

btw, for ext 3 hdd, theres an option to include while mounting? eg : 

sudo mount -"..." /dev ..........

---

### Post by bluehige on 2004-12-16
thx, coz i come from suse, and each time to mount is : 

su
pass
mount.....

i ll try what u said :) thx

btw, for ext 3 hdd, theres an option to include while mounting? eg : 

sudo mount -"..." /dev/"my hdd" /mnt/"folder where to mount"

---

### Post by gheorghe_pop on 2004-12-16
i don't know.
I allways use simple mount for mounting my drives:)

---

### Post by bluehige on 2004-12-16
ok, so if my hdd is on /dev/hda and i want to mount it on /mnt/hdd1 i just type

bash # sudo mount /dev/hda /mnt/hdd1

thats right?

---

### Post by nemin on 2004-12-16
[QUOTE=bluehige]ok, so if my hdd is on /dev/hda and i want to mount it on /mnt/hdd1 i just type

bash # sudo mount /dev/hda /mnt/hdd1

thats right?[/QUOTE]

yeah, usually that's enough :)

---

### Post by bluehige on 2004-12-16
thx i ll try when ill be at home :)

---

### Post by gheorghe_pop on 2004-12-16
depends on how many partitions you have on it.
For more than one partition yo have to use hda(1),hda(2).....hda(n).
But i asume that you know that.;)

---

