---
title: "build-essential installation"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by i_ubun89 on 2010-09-30
I've been trying to install build essential on my wubi using synaptic manager and the live cd.. but whenever i click on install, it pops a message, asking me to insert the disk labeled 'ubuntu 9.0_karmic_koala release i386 (20091028.5)', even after i've inserted the cd. 

i tried mounting the cd manually, using:
```
sudo mount -t iso9660 /dev/cdrom0 /media/cdrom
```
and got the following error:
mount: block device /dev/sr0 is write protected;
mounting read only

i tried this as well:
```
/dev/scd0/media/cdrom0 auto user,noauto,exec,utf8 0 0
```
and got:
bash: /dev/scd0: permission denied

Also, i don't have internet on my machine. What do i do?

---

### Post by i_ubun89 on 2010-09-30
no help?? :(

---

### Post by realzippy on 2010-09-30
Did you enable the UbuntuCD in Synaptic/Settings/Repositories?

---

### Post by i_ubun89 on 2010-09-30
i did...

---

### Post by realzippy on 2010-09-30
...might be a wubi problem then.
Btw,linux without internet is a sad story...

---

### Post by oldos2er on 2010-09-30
If you have access to another machine with internet, you can try Keryx. [http://keryxproject.org](http://keryxproject.org)

---

### Post by i_ubun89 on 2010-10-01
> **oldos2er said:**
> If you have access to another machine with internet, you can try Keryx. [http://keryxproject.org](http://keryxproject.org)
i tried kerix.. i downloaded build-essential in another machine... but when i try installing it in my machine, it still looks for an internet connection.

---

