---
title: "How to get Ubuntu to boot UFS partition PC-BSD?"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by heavyonion on 2012-09-04
I have partitioned my hard drive and I just install PC-BSD on one of the partitions. It is not recognized in the grub list at startup? Disk utility says it is a UFS partition instead of EXT4.
How do I boot PC-BSD? I would like to try it out.

---

### Post by Beliveme on 2012-09-04
Hi, do you try add somethink as that:

menuentry "FreeBSD" {
   set root=(hd0,3)
   chainloader +1
}

to /etc/grub.d/40_custom ? You must set position of your disk root and partition where is the PcBSD installed. After just run as root u update-grub and it should work :) try it.

---

### Post by heavyonion on 2012-09-04
I have the 40 custum folder open. How do I add the PC-BSD it is installed on /dev/sda4/ ?
Thank you.

---

### Post by oldfred on 2012-09-04
I have both of these in my notes. With sda4 and grub2 it is hd0,4.

[http://forums.freebsd.org/showthread.php?t=5918](http://forums.freebsd.org/showthread.php?t=5918)
menuentry "freebsd 8.0" {
    set root=(hd0,4,a)
    chainloader +1
}

[http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html](http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html)
    menuentry "FreeBSD 7.2-RELEASE i386" {
            set root=(hd0,4)
            chainloader +1
    }

But chainloaders assume more boot code is in the partition boot sector. Is that how freebsd works? I do not know.

I also see grub2 has ufs1.mod and ufs2.mod. You may have to include those like this?

[http://forums.freebsd.org/showthread.php?t=5918](http://forums.freebsd.org/showthread.php?t=5918)
menuentry "freebsd 8.0" {
    insmod ufs1
    set root=(hd0,4,a)
    chainloader +1
}

You can put a couple of versions into 40_custom and on the grub menu use e for edit and experiment with various alternates. If you find one that works then update 40_custom.

---

### Post by heavyonion on 2012-09-04
I am still a newbee, how do I add these entries??
Thank you so much for your help.

---

### Post by oldfred on 2012-09-04
Copy & paste into 40_custom, but you may still have to experiment. Not sure freeBSD then is something for  a new user. That is hard core Unix. 

gksudo gedit /etc/grub.d/40_custom

#update grub menu
sudo update-grub

---

