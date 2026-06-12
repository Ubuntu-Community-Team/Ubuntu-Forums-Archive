---
title: "Stuck at BusyBox v1.1.3 prompt while installing from UBS"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by manav_gupta on 2008-01-27
Ok, so I'm trying to install ubuntu 7.10 on my Thinkpad t61p (dual core CPU@1.7 Ghz, 4 GB RAM, 300 GB HDD), while booting from USB pen drive.

I have the USB drive with all files from "syslinux" copied on the root folder of the pen drive, as well as vmlinux and initrd.gz

The installer takes me to the BusyBox console, and Alt+F1 shows the following messages:

Loading, please wait...
cp: unable to open '/root/var/log' : No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

I fail to understand a simple OS installation would be so difficult.

Any ideas anyone?

Thanks
m

---

### Post by manav_gupta on 2008-01-27
I cannot believe installing a frigging OS would eat up the entire weekend... this is precisely the reason why end-users find it so hard to migrate to Linux..

---

### Post by inaety on 2008-01-27
It appears that you are missing files.  Check your USB stick to make sure all the files are available, and you google for the correct way to do this.  Installing from a burned disc with a checked MD5 Checksum should allow you to get past Busybox.

Installation can take time because not every system has been perfected.

---

### Post by manav_gupta on 2008-01-28
The files being used are from a fresh download of 7.10 iso.

I do not have a CD drive on my laptop at the moment. 

The installation is being attempted from a USB pen drive, however, I will check the md5 checksum and post again.

---

### Post by manav_gupta on 2008-01-28
Btw, does anyone know what to do once you do get redirected to the Busybox console?

---

### Post by joealanb on 2008-04-11
I installed Ubuntu 7.10, loved it.  Did a dual boot with Vista 32bit, and that killed grub. Now Ubuntu won't install run and I am stuck a the busybox v1.1.3.  I am fairly inexperienced... any ideas?

---

### Post by missbliss on 2008-04-11
i seem to have a similar problem.  except i am booting ubuntu 7.10 i386 from a mounted e:// drive mounted by magiISO.

the dual boot screen comes up with option to boot windows xp or ubuntu.

when i choose ubuntu, the boot screen comes up and the bar goes back and for for a minute or two and then i get this:

Busybox v1.1.3 (Debian 1:1.1.3-5 ubuntu 7) Built-in Shell (ash)
Enter 'help' for a list of built in commands
(initramfs)



not trying to thread jack, but just trying not to create another thread in a busy forum if it's not needed!

---

### Post by bmfgeorgin2 on 2008-04-12
I have the same problem please help!

(directed at post 7)

---

### Post by shamittomar on 2008-04-26
I am suffering same problem too. WHAT IS BUSYBOX????????
WHAT SHOUL I DO NOW. I checked the MD5 hash. It is same.

---

