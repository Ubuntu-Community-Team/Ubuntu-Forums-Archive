---
title: "Server 10.04 Advanced Install from LiveCD (Raid or LVM)"
date: 2012-08-02
forum: Installation &amp; Upgrades
---

### Post by marcjpo on 2012-08-02
Hi All,

Iv'e used remastersys to create a livecd server distro. Everything works perfect with 1 exception!! I cannot get the system to boot if I choose to install to a raid or lvm  setup. I have followed 3 different tutorials online using the official Ubuntu LiveCD and it has worked flawless...can anyone tell my why this is?? What would be the difference in my remastersys iso??

After rebooting...I get this message 

"ALERT! /dev/disk/by-uuid/* does not exits. Dropping to shell.
initramfs"

Thanks,
MarcJPo

(*NOTE it does install correctly if you choose to use the whole disk option in the installer -and- I can perform all the same functions as the tutorials suggest without getting any errors)

---

### Post by PyroSamurai on 2012-10-10
Try installing the RAID or LVM after the initial installation. Also is that all of the error code? About 10 or so more lines above this code would be more helpful to grasp the situation.

---

### Post by marcjpo on 2012-10-11
Hi, Thanks for the reply! I have gotten busy and forgot that I had posted this here... I figured out what I needed to do or at least it worked...lol  

Commands for Raid
1) sudo mount /dev/md0 /target/
2) sudo mount &#8211;bind /dev/ /target/dev/
3) sudo mount &#8211;bind /sys/ /target/sys/
4) sudo mount &#8211;bind /proc/ /target/proc/
5) sudo cp /etc/mdadm/mdadm.conf /target/etc/mdadm/
6) sudo chroot /target/
7) sudo update-initramfs -u
8) exit

Here you can visit the project site for more info
[http://www.mattpyers.com/hyperbox/?page_id=115](http://www.mattpyers.com/hyperbox/?page_id=115)

---

