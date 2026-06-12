---
title: "sort of a catch22 with upgrade"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by ulao on 2012-06-08
I ran my do release upgrade and it stalled on 

W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

i read up on this and I here its a bug. the fix was basically to remove mdadm and grub then reinstall grub. I dont use any md's anyways. 

Here is the catch... To remove the mdadm I'm told by apt-get to complete the current upgrade installs ( using re configure all ). To install the current upgrade I need to remove mdadm, how can I fix this? I gather reboot will keep me from getting back in to my os.

Is there a way to purge the apt-get install list and start the upgrade over once I remove mdadm? I use ide drives no raid or sata.

---

### Post by ulao on 2012-06-08
I was thinking this was a common problem, surely that has to be a way around this?

So I tried dpkg --purge mdadm and now dpkg configure initramfs and stopped. If I try to run the upgrade it says up to date. Maybe its good?

---

