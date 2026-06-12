---
title: "get rid of grub2"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by dura2 on 2015-08-07
Hi!

I'm running several computers diskless - the're booting via the local network, the filesystems are stored on a nfs storage. As I'm booting with pxelinux over the net, I dont want to have grub2 installed. More precisely, grub2 interferes with my installation when something thinks it needs to update / reconfigure grub2 and can't do this as I have no local disk installed. As I don'T need it, I deinstalled grub2 like this: ```
apt-get purge grub-pc
```

Every now and then, when I'm installing updates, something is re-installing grub2.

Is there a way to permanently remove grub2 from my machines and keep it that way? 

with kind regards,
errorsmith

---

### Post by JMB74 on 2015-08-07
You could use '[equivs]("http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=equivs")' to create dummy grub2 packages with slightly newer version than the ones in your ubuntu version. Then install those after purging the genuine ones.

Any change to your system after that that wanted grub2 installed would see the dummy ones as fulfilling the dependency.  So would not install the real ones.

[https://www.google.co.uk/#q=equivs+dummy+dependency](https://www.google.co.uk/#q=equivs+dummy+dependency)

---

### Post by grahammechanical on 2015-08-07
I think this situation is caused by an upgrade to the Linux kernel which prompts the runing of some Grub scripts to update and re-configure the Grub configuration files. I cannot say if this will solve your problem but at least you will become more familiar with the workings of Grub.

There are several scripts used by Grub and they are all allowed to be executed as a program. If those scripts are still on your system then remove the permission to execute as a program. Then they will not run when there is a kernel update.

Locations

/etc/grub.d/
/usr/sbin/update-grub    === runs grub-mkconfig
/usr/sbin/update-grub2  === runs grub-mkconfig 
/usr/sbin/grub-mkconfig

Regards.

---

### Post by dura2 on 2015-08-09
Hi
thank you for reply. I think I'll give equivs a try: I'm concerned if I'll -x the mentioned script ap-get either tries to correct this (by reinstalling grub) oder terminates with an error. I think there should be some configruation switch somewhere to disable the forceful installtion of a bootloader. 

with kind regards

---

