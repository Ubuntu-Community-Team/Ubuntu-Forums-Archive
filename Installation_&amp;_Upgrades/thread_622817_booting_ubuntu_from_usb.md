---
title: "booting ubuntu from usb"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by karatchov on 2007-11-25
hy

My question is a little bit unusual ...

I had windows xp on my computer, I installed ubuntu 7.04 x386 and recently ubuntu 7.10 x64 each on a different partition. As a home computer, I don't want to install grub on the main drive, I just want the computer to boot directly to xp. (which is the case right now)

To acess the ubuntu systems, I wish to use a flash disk ...

so the question is:
 * how can I install grub and configure it correctly to a flash disk, to be able to boot into linux partition (installed on the main hard drive)

so that way i just have to connect my usb flash disk on boot to get the grub menu with my ubuntu systemss, otherwise, the system boot directly to xp


---
Please don't suggest to change the grub menu time out, or to install the whole ubuntu to the flash, I already have read those solutions

thanx

---

### Post by dips_xe on 2007-11-25
how is it booting directly to xp if you have two ubuntu installs on there? where is grub currently?

---

### Post by Pumalite on 2007-11-25
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by karatchov on 2007-11-25
grub is currently uninstalled, I used the xp fixmbr 

Pumalite, could you please be more specific ......

---

### Post by Pumalite on 2007-11-25
If you can boot a Live CD, please post::
sudo fdisk -lu

---

### Post by meierfra on 2007-11-25
It can be done.  Here are the main steps. Let me know if you need more details.

0) Boot into ubuntu .

1)  Mount  a partition from your flashdrive to the folder (say) /flash.


2)   Install grub to the MBR of the flashdrive: 

```
sudo grub-install --root-directory=/flash /dev/sdb
```

This assumes that your flash drive is /dev/sdb. Use "sudo fdisk -l" to find out the actual device name


3)  Copy  the file  /boot/grub/menu.lst  from you ubuntu partition to  /flash/boot . 

4) Edit  /flash/boot/grub/menu.lst: Say your ubuntu partition is the third partition on the first harddrive. Then you will need to change all "root (hd0,2)" to "root (hd1,2)"

5) Reboot  from your flash drive

---

### Post by V-600 on 2007-11-25
This is exactly what i was looking for. Thanks.

Further to this though can I just run this by people. If when I installed ubuntu I didn't install grub, would I be right in assuming that no /boot/grub would be created, and thus no /boot/grub/menu.lst

How then would i create the relevant grub settings without first installing grub to the MBR which is what I was looking to avoid in the first place.

This is more of a theoretical problem rather than a practical one as I can just use a different computer to sort everything and then write my own grub entry. Is there an easier way though.

Thanks

---

### Post by meierfra on 2007-11-25
> how then would i create the relevant grub settings without first installing grub to the MBR 


Just one extra step:

Create the folder /boot/grub in the ubuntu partition. Then

```
sudo update-grub
```

This creates "menu.lst".

---

### Post by karatchov on 2007-11-27
Thanx meierfra, that is what I'm looking for
i tried it from a live cd, and it works correctly
:D

just another question if you don't mind :
 * I found only 1 menu.lst file (the x386 system) but can find it in the Ubuntux64 partition, and the update-grub seems to miss this partition, so what shall I do ?

thanx anyway

---

### Post by meierfra on 2007-11-27
I'm  not quite sure for which version of ubuntu you are missing the menu.lst. But suppose you are missing the menu.lst for the partition /dev/sda1.  Then chainroot into that partition:


```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu
sudo update-grub
exit 
```

You now can find "menu.lst" in  the folder /ubuntu/boot/grub. Just copy and paste the relevant items to your "menu.lst" on the flash drive. Change all "root (hd?,?) as  before

---

### Post by karatchov on 2007-12-02
thanx a lot

---

