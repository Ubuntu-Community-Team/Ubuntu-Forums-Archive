---
title: "Highpoint Rocketraid 1740 install issues"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by kmfdmz3 on 2008-10-31
I followed the steps from this archived thread:
[http://ubuntuforums.org/showthread.php?t=558543&highlight=rocketraid&page=3](http://ubuntuforums.org/showthread.php?t=558543&highlight=rocketraid&page=3)

Removed sata_mv.ko as stated later on in the thread. Module is showing up under modprobe but the drives are not showing up when I do a 'fdisk -l' I had this installed and working now it doesn't. I'm trying to install this on ubuntu 8.04.1 kernel 2.6.24-19-server. Any help would be much appreciated!

---

### Post by hans.hook on 2008-12-25
The following does the trick for me:

apt-get -y install build-essential
apt-get -y install linux-headers-$(uname -r)
cd rr174x/product/rr1740pm/linux/
make clean
make KDIR=/lib/modules/$(uname -r)/build
mkdir -p /lib/modules/$(uname -r)/kernel/drivers/scsi/rr174x/
cp rr174x.ko /lib/modules/$(uname -r)/kernel/drivers/scsi/rr174x/
depmod -a
echo 'blacklist sata_mv' >> /etc/modprobe.d/blacklist
update-initramfs -k "$(uname -r)" -c

Hope it helps!

Regards 

Hans Höök

---

