---
title: "[SOLVED] pendrivelinux 710 installation"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by jmsjr51 on 2007-12-30
I am trying to install Ubuntu710 onto a pen drive using the tutorial from pendrivelinux.com  I've typed

 cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/ 

and get an error that 

'/media/ubuntu710/' is not a directory:  No such file or directory

Am i suppose to replace "media" with something along the lines of /dev/sdb2 ??

thanks,
trying Ubuntu for first time.

---

### Post by jmsjr51 on 2007-12-30
Sorry, but i must have re-inserted the pendrive into an adjacent usb port.  Redoing the procedure and inserting/removing from the same usb port seemed to work.

---

