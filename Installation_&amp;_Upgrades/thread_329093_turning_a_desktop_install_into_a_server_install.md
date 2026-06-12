---
title: "turning a desktop install into a server install"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by paridoth on 2006-12-31
ok i am having troubles installing ubuntu server onto my old presario 5441 see the following post for more info
[http://www.ubuntuforums.org/showthread.php?t=327050](http://www.ubuntuforums.org/showthread.php?t=327050)
however the desktop install works just fine, so i was wondering whats the best way to turn my desktop install into a server install? i was figuring just removing X and gnome, all the gui apps, and installing the appropriate server apps to replace them. but i'm not really sure where to start. i'm thinking
```
apt-get remove x11-common
```
is there a better easier way?

thanks

---

### Post by linuchsan on 2007-01-01
I can't see any problem by just disabling all you don't need, unless you have a diskspace issue.

---

### Post by paridoth on 2007-01-01
wait i just got an idea from this wiki article
[https://help.ubuntu.com/community/ServerFaq?highlight=%28server%29](https://help.ubuntu.com/community/ServerFaq?highlight=%28server%29)
could i install the ubuntu server 6.10, then copy a desktop kernel and use the desktop kernel nstead of the "optimized" server kernel which i think is causing the problems?

---

### Post by raul_ on 2007-01-01
Why can't you do a clean install?

---

### Post by paridoth on 2007-01-01
ubuntu desktop installs and runs perfectly, but ubuntu server resets the computer just after grub starts to boot it.

---

### Post by raul_ on 2007-01-01
> **paridoth said:**
> wait i just got an idea from this wiki article
[https://help.ubuntu.com/community/ServerFaq?highlight=%28server%29](https://help.ubuntu.com/community/ServerFaq?highlight=%28server%29)
could i install the ubuntu server 6.10, then copy a desktop kernel and use the desktop kernel nstead of the "optimized" server kernel which i think is causing the problems?

Yes, i think you can install the kernel with apt-get and then it will be available in grub. If it's not, try editing /boot/grub/menu.lst

---

### Post by paridoth on 2007-01-01
sweet, im going to give that a shot, im also going to try the fiesty server from 
[http://cdimage.ubuntu.com/ubuntu-server/daily/20070101/](http://cdimage.ubuntu.com/ubuntu-server/daily/20070101/)

---

### Post by raul_ on 2007-01-01
Btw, did you try the Dapper server install?

---

### Post by paridoth on 2007-01-01
yes, same problem

---

### Post by paridoth on 2007-01-02
ok i tried it, everything worked great, chroot worked perfect and everything, but i cant apt-get, looks like theres no internet conectivity after i chroot, the live cd has internet perfectly, but it looks like the chrooted environment doesnt have internet, as it said it couldnt find the kernel, and a apt-get update returns a bunch of errors about temporary failures resolving.

how can i get internet on the chrooted environment? or can i use the livecd's respos in the chrooted envirironment? or can i download the deb with the live cd then dpkg it in the chrooted environment?

---

### Post by linuchsan on 2007-01-02
How did you chroot?

---

### Post by paridoth on 2007-01-02
mkdir /mnt/tmpserver
mount -t ext3 /dev/hdc1 /mnt/tmpserver
cd /mnt/tmpserver
mount -t proc /proc proc
mount -t sysfs /sys sys
mount -o bind /dev dev
chroot ./
apt-get install linux-image-generic

---

### Post by linuchsan on 2007-01-02
chroot /mnt/tmpserver /bin/bash

---

### Post by paridoth on 2007-01-02
> **linuchsan said:**
> chroot /mnt/tmpserver /bin/bash

instead of ```
 chroot ./
```
correct?

---

### Post by linuchsan on 2007-01-02
Yes

---

### Post by paridoth on 2007-01-02
same problem =/

---

### Post by linuchsan on 2007-01-02
How does you /etc/resolv.conf looks like? (when chrooted)

---

### Post by paridoth on 2007-01-02
looks like i dont have one, could this be because i installed it when the computer wasnt conected to a network?

---

### Post by linuchsan on 2007-01-02
no dns and no gateway...oeps.
Is there internet before you chroot?

---

### Post by paridoth on 2007-01-02
yes the live cd has internet because i moved the computer over to the router so i could get online, but when i installed it it was on the other side of the room away from the router, so i decided to install it without the network then move it over and have it on the network without a monitor and ssh into it with my main computer

i have a resolv.conf from another computer on the same network, can i use it?

---

### Post by linuchsan on 2007-01-02
you could, but by editing resolv.conf you can insert the following:
nameserver your_dns
check if there is a gateway aswell, with route

---

### Post by paridoth on 2007-01-02
its working =) downloading kernel now

---

### Post by linuchsan on 2007-01-02
Good luck :p

---

### Post by paridoth on 2007-01-03
it updated my menu.lst for me, and put the entry in, i chose it at boot, aanndd... it works! horay! the kernel boots and everything, but now i have a new problem -.-

at boot i get a message [```
    79.775771] sis630_smbus  0000:00:01.0: sis630 comp. bus not detected, module not inserted

```
it continues to boot, and finishes, i login, but have no network connection on the server, ifconfig returns only lo.

i'm guessing this has something to do with installing the generic kernel because when it was chrooted it had Internet, and a network connection.

EDIT: fixed, had no entry in /etc/network/interfaces for eth0 -.-

thanks for all your help!

---

