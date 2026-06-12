---
title: "waiting for boot file system after compiling the kernel"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by wormite on 2007-01-18
I haven't been able to solve this problem for several days, so I decide post it here.

Because I heard that in the newest kernel , the problem with ndiswrapper conflicting the
nvidia driver (both using IRQ 177) has been fixed. So I decided to compile a kernel myself.
I followed the instruction here:
[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)
Everything worked smoothly till I rebooted. It reported as 
Waiting for boot file system
Alert! /dev/sda2 does not exist.
and dropped me to a fall back shell
I poked around and found when upgrading to edgy or installing to edgy this can happen.
The first suggestion was to use evms_activate in the fallback shell. I tried this cause my
evms folder was not populated.
But it gave this error:
libgcc_s.so.1 must be installed for pthread cancel to work.
But I have installed that and it's in /lib/.
I can't understand why , anyone can help?
Lun

---

### Post by Theimon on 2007-01-18
I suggest you use this HowTo [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) instead of the one you mention in your post. I used the same one once but this one is far better. Also take a good look at the links given.
And make sure you include SATA support in your kernel. You have to select it in the driver section. Your system is waiting for the boot file system cause it can only read ATA drives. The HowTo you used is far too simple to really customize to your own needs.

---

### Post by wormite on 2007-01-18
ok, follow-ups:
I found that in the menu.lst(/boot/grub)
when it's changed to 
 /boot/vmlinuz-2.6.20-rc4-custom root=/dev/hda3 ro quiet splash
sda3->hda3, everything worked,(except for setting sensor limits).

I don't know why that is mounted differently, can I change it back to sda3?
Btw, when X is started. it's still sda3.

---

### Post by wormite on 2007-01-18
Thanks for the reply, I'm reading the link:D
Now I'm gonna recompile the kernel again.

---

### Post by wormite on 2007-01-18
I'm compiling the kernel now. With brand new options set.:D
Btw, how to remove the old compiled kernel cleanly?
I know several places needed to be alter:
/boot/grub/menu.lst
/boot/initr.imgxxxxx
/boot/vmlinuzxxxxxx
/usr/src/linux-headerxxxxxx

anything else?

---

### Post by Theimon on 2007-01-19
Anything in the /boot folder that matches the version your previous custom kernel. And indeed the menu.lst. As far as I know, that should do it. Maybe run update-grub (or something like that, don't know the specific command right now). It's safe to remove the old header and kernel files from /usr/src too. Just to be sure things don't get mixed up, or that maybe you might use the wrong files. 
I doubt it though. The way you are doing it now creates 2 .deb files which you install using dpkg -i. Hard to mess things up that way. If you want to uninstall them for any reason, you can use Synaptic or aptitude etc.

---

### Post by wormite on 2007-01-19
Thanks, I have got the new kernel built, with the new nvidia 8776('cause I'm using the beryl and nvidia newest driver still haven't fixed that video card memory bug)
Now I'm happy:D
For those who just compiled >2.6.19 kernel, this link helps you build the nvidia driver for 8776.
[http://www.nvnews.net/vbulletin/showpost.php?p=1086669&postcount=19](http://www.nvnews.net/vbulletin/showpost.php?p=1086669&postcount=19)
Lun

---

### Post by Theimon on 2007-01-20
So the system gives you no trouble when booting up?

---

### Post by wormite on 2007-01-29
Actually the disk are recognized as hda now, but after changing the grub menu.lst,it's working.
I've followed the advice in post "master kernel", and checked the scsi support(old sata support are deprecated, it's in scsi now,and the config has some note which says that if you wanna boot from scsi, have to check this etc) but it doesn't work, hard disks are still recognized as hda.
I wonder what else I can do.

---

### Post by Theimon on 2007-01-30
You're not using a SCSI disk. You're using a SATA disk. I'll try to make a screenie of the section in the menuconfig which is responsible for the SATA driver tomorrow. Maybe that will clear things up.

---

### Post by Theimon on 2007-01-31
So here we are with a screenie, maybe this makes it clearer where to look for the correct SATA location: [http://members.home.nl/theimon/sata-support-cfg-location.png](http://members.home.nl/theimon/sata-support-cfg-location.png)
Don't worry about saying it's experimental, it works like a charm. Be sure to select the right driver and incluse them in the kernel (so don't compile them as module), it may give you a slightly better performance.

---

