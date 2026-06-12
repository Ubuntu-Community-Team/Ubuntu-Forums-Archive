---
title: "Move Home to other partition"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by klaasth on 2008-05-30
I followed this guide: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Everything went fine, untill I rebooted my pc, then I got the following errors:
[http://users.skynet.be/bs255923/1.jpg](http://users.skynet.be/bs255923/1.jpg)
[http://users.skynet.be/bs255923/2.jpg](http://users.skynet.be/bs255923/2.jpg)

I think it is something wrong with my /etc/fstab/
I added
/dev/sdb5 /home ext3 nodev,nosuid 0 2

What must I change to get it working?

---

### Post by Pumalite on 2008-05-30
Try this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sisco311 on 2008-05-30
> **klaasth said:**
> I followed this guide: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Everything went fine, untill I rebooted my pc, then I got the following errors:
[http://users.skynet.be/bs255923/1.jpg](http://users.skynet.be/bs255923/1.jpg)
[http://users.skynet.be/bs255923/2.jpg](http://users.skynet.be/bs255923/2.jpg)

I think it is something wrong with my /etc/fstab/
I added
/dev/sdb5 /home ext3 nodev,nosuid 0 2

What must I change to get it working?

Post the output from:
```
mount
```
and
```
sudo fdisk -l
```

---

### Post by klaasth on 2008-05-30
sudo fdisk -l ==> what does this command do???

---

### Post by sisco311 on 2008-05-30
fdisk -l lists the partition tables.
read the man page for more info.(man fdisk)

---

### Post by Oldsoldier2003 on 2008-05-30
> **klaasth said:**
> I followed this guide: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Everything went fine, untill I rebooted my pc, then I got the following errors:
[http://users.skynet.be/bs255923/1.jpg](http://users.skynet.be/bs255923/1.jpg)
[http://users.skynet.be/bs255923/2.jpg](http://users.skynet.be/bs255923/2.jpg)

I think it is something wrong with my /etc/fstab/
I added
/dev/sdb5 /home ext3 nodev,nosuid 0 2

What must I change to get it working?

boot into recovery mode and chmod 700 ~/
chmod the .dmrc to 644

then reboot

---

### Post by klaasth on 2008-05-30
sudo chown -hR username /home/username/

==> I redid everything en after the whole process I entered this command!!! It solved my issue

---

