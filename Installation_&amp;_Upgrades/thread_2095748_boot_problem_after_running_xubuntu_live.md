---
title: "boot problem after running xubuntu live"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by nomadlite on 2012-12-17
My laptop have windows and ubuntu 12.04 dual boot.

I try to install xubuntu to replace ubuntu. I go back and forth in the installation program try to decide what to do, then a error message show up something about unmount sba. I don't know what to do so I went to the menu and choose shutdown the computer. I figure I did not start the installation yet so things should be ok.

After restart, when I run the installation program, the live CD did not detect Ubuntu and only detect Vista. so I stop the live cd and restart to GRUB.

Everything still listed on grub, I can still start vista. But when I try to start Ubuntu and ubuntu recovery, I got (initramfs)

Gparted show partition, with boot flag, have list of "cluster accounting failed at xxxxx(0xxxxxx): extra cluster in $bitmap."

Any ideas

---

### Post by nomadlite on 2012-12-19
I don't know what to do so I decided to take some risk and installed Xubuntu anyway.

I backed up all my vista file

ran Windows Check Disk program. 

Using Gparted, repartition and format original Ubuntu partition for new Xubuntu installation

install Xubuntu and installation warned about no swap partition, laptop's ram is 4GB so I am assuming no swap will be needed.

installation is complete and everything is ok. Xubuntu just replaced Ubuntu

---

