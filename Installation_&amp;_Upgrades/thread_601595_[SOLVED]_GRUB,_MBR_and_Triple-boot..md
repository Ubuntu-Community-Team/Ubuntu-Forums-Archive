---
title: "[SOLVED] GRUB, MBR and Triple-boot."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2007-11-03
I followed the pointer in this [post]("http://ubuntuforums.org/showpost.php?p=121355&postcount=5") and [this]("http://ubuntuforums.org/showpost.php?p=3471290&postcount=3"). But my case is a slight variant of
these. This is my setup -

I have XP, Ubuntu and CentOS - Installed in the same order.
So, now CentOS took over the GRUB ( which I didn't want to ).

Now, I'm looking for options, as I'd like Ubuntu's GRUB take over
and

1. Chain-loader if possible, so that Ubuntu's GRUB conducts the show and I
choose CentOS, which could either get to me directly to CentOS or to the grub of CentOS

2. If #1 is not fully possible, forget about CentOS's grub and restore Ubuntu's GRUB and then I deal with CentOS. If possible, how ?

I pulled this from the live-cd
> 
$ find /boot/grub/stage1
(hd0,9) ---> Ubuntu
(hd0,11) --> CentOS
and my disk-layout is
> 
http$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda10             19G  854M   17G   5% /
varrun               1008M   96K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  116K 1007M   1% /dev
devshm               1008M   16K 1008M   1% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hda11             19G  173M   18G   1% /app
/dev/hda12             18G  5.0G   12G  30% /centos
/dev/hda14             19G  2.3G   16G  13% /home
/dev/hda1              41G   21G   20G  52% /media/hda1
/dev/hda5              41G  4.3G   36G  11% /media/hda5
/dev/hda6              41G   26G   15G  65% /media/hda6
/dev/hda7              41G  3.8G   37G  10% /media/hda7
/dev/hda8              21G   18G  2.2G  90% /media/hda8
/dev/hda9              21G   16G  4.7G  77% /media/hda9
/dev/hdb5             112G   68M  112G   1% /media/hdb5
/dev/hda15             21G  2.6G   18G  14% /usr
Please advice. Thanks!

---

### Post by mrvertigo on 2007-11-03
mmm odd, grub should be grub...... can you give more detail?

---

### Post by shankariyer on 2007-11-03
I've uploaded the grub files from Ubuntu and CentOS.

---

### Post by meierfra on 2007-11-03
I recommend the following:

1)  Put the the ubuntu grub back in charge:

sudo grub 

and at the grub prompt:

root (hd0,9)

setup (hd0)

quit

2) Add CentOS to your Ubuntu menu.lst at  the very end of the file:

title CentOS
configfile (hd0,11)/boot/grub/menu.lst

(and remove your currrent CentOS item)

This will bring up the CentOS grub menu, but has the advantage that you won't have to edit the Ubuntu menu.lst after each CentOS kernel upgrade.

3)  set  "timeout 1" in the CentOS menu.lst (Just enough time to select the CentOS recovery mode if you ever need to).

---

### Post by shankariyer on 2007-11-03
The good news is Ubuntu's grub took over - You guys rock! Thanks

The bad news is I get the following error, when I choose CentOS
> File name must be either an absolute pathname or blocklist 

Have uploaded the latest grub config file.

---

### Post by meierfra on 2007-11-03
You need to remove the  space between (hd0,11) and /boot/grub/menu.lst.

---

### Post by shankariyer on 2007-11-03
Silly me... That works ! Thanks "meiefra" for your help, appreciate it.

---

