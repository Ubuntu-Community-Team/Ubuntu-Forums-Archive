---
title: "Installation / Login Session Error"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by sunra350 on 2007-07-01
I've installed Ubuntu 7.04 the installation went through without any errors. However when I rebooted and tried to log in I got the following error and once I click the ok button it returns to the login screen. Any Ideas on how to correct this?

--Start Of Error--

Your session only lasted 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or you msaybe out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

error details (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmo and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/: 0 Xservers" -h "" -l ":0" "sunra"
/etc/gdm/Xsession: Begining session setup...
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine. h: 554: elf_machine_rel_relative: Assertion `((relo->r_info) & 0xff) == 8' failed!

--End Of Error--

Thanx

---

### Post by Pumalite on 2007-07-01
In your Terminal: df -h  And post it.

---

### Post by sunra350 on 2007-07-01
> **Pumalite said:**
> In your Terminal: df -h  And post it.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  2.0G   12G  15% /
varrun                506M   16K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   88K  506M   1% /proc/bus/usb
udev                  506M   88K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda2              58G  129M   55G   1% /home
/dev/sdb1              75G   64G   11G  86% /media/sdb1

---

### Post by Pumalite on 2007-07-01
Well, you are not out of disk space. Did you try failsafe?

---

### Post by sunra350 on 2007-07-01
> **Pumalite said:**
> Well, you are not out of disk space. Did you try failsafe?

It will boot to text mode as root but I don't know how to resolve the issue

---

