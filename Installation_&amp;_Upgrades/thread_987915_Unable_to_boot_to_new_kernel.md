---
title: "Unable to boot to new kernel"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by ub007 on 2008-11-20
Hi,

I installed a new kernel by doing the following

wget [http://www.kernel.org/pub/linux/kern....2.6.26.6.tar.gz](http://www.kernel.org/pub/linux/kern....2.6.26.6.tar.gz) 

> #mv linux-2.6.26.6.tar.gz /usr/src
#cd /usr/src
#tar zxvf linux-2.6.26.tar.gz 
#cd linux-2.6.26.6 
linux-2.6.26.6 #make menuconfig //didnt make any changes
linux-2.6.26.6#make dep
linux-2.6.26.6#make
linux-2.6.26.6#make modules_install
linux-2.6.26.6#make install

Now when i check /booot,i find the foll entries for the new kernel.

> config-2.6....
System.map-2.6....
vmlinuz-2.6.....

I'm not seeing the **[COLOR="Red"]initrd... [/COLOR]**file.Theres one entry -initrd.img-2.6.24-19-generic ,which is for the old kernel.

Now I add this stanza to /boot/grub/menu.lst
title Ubuntu
root (hd0,3)
kernel /boot/vmlinuz-2.6.26.6 ro root=LABEL=/

//[COLOR="Red"]initrd /initrd.img-2.6.24-19-generic [/COLOR]- I couldnt make an entry corresponding to this as theres **no initrd **file in the /boot dir for the new kernel

Gives me error msg-kernel panic'

What am i missing here?


Cheers
David

---

