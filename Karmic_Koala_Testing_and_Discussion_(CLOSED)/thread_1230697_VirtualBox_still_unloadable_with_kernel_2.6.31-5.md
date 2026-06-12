---
title: "VirtualBox still unloadable with kernel 2.6.31-5"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-08-03
My VirtualBox does not work with the latest kernel
```
2.6.31-5-generic
```

Filled the bug here:
[https://bugs.launchpad.net/ubuntu/+bug/408594](https://bugs.launchpad.net/ubuntu/+bug/408594)


------

Fixed!

The last update 05/08/09 today from 
```
#VirtualBox
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```

---

### Post by phenest on 2009-08-03
Is this the OSE version? It doesn't look it. I'm using the OSE which is the same version in Karmic, and that loads up fine.

---

### Post by jfernyhough on 2009-08-03
$ sudo /etc/init.d/vboxdrv start

and repeat until it loads. :)

On mine it normally loads on the second or third attempt.

---

### Post by dentaku65 on 2009-08-03
> **phenest said:**
> Is this the OSE version? It doesn't look it. I'm using the OSE which is the same version in Karmic, and that loads up fine.

No is not. Is the one from sun repos.
BTW with the mainline kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc5/)
it works well
:confused:

---

### Post by kingborel on 2009-08-03
I'm having issues after the -5 kernel came through

> borrell@borrell-laptop:~$ uname -a
Linux borrell-laptop 2.6.31-5-generic #24-Ubuntu SMP Sat Aug 1 12:48:18 UTC 2009 i686 GNU/Linux

borrell@borrell-laptop:~$ sudo apt-get install virtualbox-ose virtualbox-ose-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose is already the newest version.
virtualbox-ose-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

borrell@borrell-laptop:~$ sudo modprobe vboxdrv
FATAL: Could not open '/lib/modules/2.6.31-5-generic/updates/dkms/vboxdrv.ko': No such file or directory
borrell@borrell-laptop:~$ 


There is no /etc/init.d/vboxdrv file, just an /etc/init.d/vboxdrv.dpkg-bak file

> borrell@borrell-laptop:~$ sudo /etc/init.d/vboxdrv.dpkg-bak setup
 * Stopping VirtualBox kernel module                                                                                                            *  done.
 * Recompiling VirtualBox kernel module                                                                                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
borrell@borrell-laptop:~$ 

> borrell@borrell-laptop:~$ cat /var/log/vbox-install.log 
/etc/init.d/vboxdrv.dpkg-bak: 364: /usr/share/virtualbox/src/vboxdrv/build_in_tmp: not found


---

### Post by setherd on 2009-08-04
doesn't work for me either.
and "sudo /etc/init.d/vboxdrv start" doesn't work

dmesg gives me this:
[ 3508.591003] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 3508.591008] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 3508.591010] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

---

### Post by budluva04 on 2009-08-04
sudo modprobe vboxdrv
sudo modprobe vboxnetflt

worked for this guy...

---

### Post by setherd on 2009-08-04
$ sudo modprobe vboxdrv
FATAL: Error inserting vboxdrv (/lib/modules/2.6.31-5-generic/updates/dkms/vboxdrv.ko): Invalid argument

that's all I get. 

I found a similar thread at the virtualbox forums:
[http://forums.virtualbox.org/viewtopic.php?f=7&t=19952](http://forums.virtualbox.org/viewtopic.php?f=7&t=19952)

---

### Post by mariner09 on 2009-08-04
I just applied the updates last night and I'm able to load vboxdrv.  I have to do it manually, can't seem to get it to auto-load at boot.

---

### Post by budluva04 on 2009-08-04
ok, well how about this...what are you guys getting when you run

```
$ sudo /etc/init.d/dkms_autoinstaller start 2.6.31-5-generic
```

should rebuild all dkms modules, nvidia, any wireless modules, vbox modules...

---

### Post by shakaran on 2009-08-04
Nothing, It is broken yet.

```

$  sudo /etc/init.d/dkms_autoinstaller start 2.6.31-5-generic
 * Running DKMS auto installation service for kernel 2.6.31-5-generic           
 *  vboxdrv (3.0.2)...                                                          vboxdrv (3.0.2): Already installed on this kernel.
                                                                         [ OK ]
 *  vboxnetadp (3.0.2)...                                                       vboxnetadp (3.0.2): Already installed on this kernel.
                                                                         [ OK ]
 *  vboxnetflt (3.0.2)...                                                       vboxnetflt (3.0.2): Already installed on this kernel.
                                                                         [ OK ]
```

---

### Post by mariner09 on 2009-08-05
I think that's the output you should see when running that command, however, I was only able to get that when running /etc/init.d/dkms_autoinstaller start.

---

### Post by dentaku65 on 2009-08-05
Fixed!

The last update 05/08/09 today from
```
#VirtualBox
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```

---

### Post by kingborel on 2009-08-05
I was able to get it going again by purging virtualbox-ose-source and reinstalling it

---

### Post by shakaran on 2009-08-05
VirtualBox 3.0.4 is out! It solve the problem!

---

### Post by setherd on 2009-08-05
it worked for me too!!!
:)
it also solved my display corruption issues (I think caused by Qt libraries)

---

