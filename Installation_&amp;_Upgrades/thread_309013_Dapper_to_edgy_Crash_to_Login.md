---
title: "Dapper to edgy: Crash to Login"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by DarkDancer on 2006-11-29
I'm having trouble with Edgy and Dapper before it. I was using Dapper, and I think the last upgrade that I got (not sure which one that is) before I installed edgy, caused dapper to, on login, get to the desktop, and then crash back to the login screen a random number of times before letting me in.  I did the upgrade (I upgraded rather than doing a fresh install, because I can't get an edgy boot disk to work) and the behavior followed. 

I decided that I would just reload Dapper, not let it install any of it's own updates and then upgrade to edgy. It still happens. Any advice? A clue? Anything? What do you need to know?

---

### Post by DarkDancer on 2006-11-29
Bump.

---

### Post by DarkDancer on 2006-11-29
Anyone? Anything at all? Not a clue? Did I stump you all?

---

### Post by DarkDancer on 2006-11-29
Bump

---

### Post by bapoumba on 2006-11-30
Is there any error message ?

When the logging screen is up, <CRTL> + <ALT> + F1 will get you to a tty screen, no graphics mode. Loggin + pwd : do you have any error message ?
Can you post the output of **hostname** ? (just a wild guess).

<CRTL> + <ALT> + F7 will get you back to the X session.

---

### Post by DarkDancer on 2006-11-30
Oh, if I go to the non-graphical login screen (ctrl-alt-f7) and login there from first boot, it takes me right to my prompt, no error messages. hostname=darkdancers. When I do ctrl-alt-f7, it takes me back to the graphical log in. When I login there, it takes me to the desktop, then crashes back. If I try to do another ctrl-alt-f1 the login screen gets real big and freezes, I have to reboot.

---

### Post by DarkDancer on 2006-12-01
Bump.

---

### Post by bapoumba on 2006-12-01
Another wild guess : do you have enough room on your partitions ?
**df -h** will let you know.

---

### Post by DarkDancer on 2006-12-11
darkdancer@darkdancers:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             4.9G  3.0G  1.6G  66% /
varrun                379M   88K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   18M  362M   5% /lib/modules/2.6.17-10-386/volatile
/dev/hda2             4.9G  4.2G  400M  92% /home
/dev/hda1              20G  9.6G   11G  49% /media/hda1
/dev/hda6             203G   32G  171G  16% /media/hda6
/dev/hdb1              75G  1.1G   74G   2% /media/hdb1
/dev/hdc              4.3G  4.3G     0 100% /media/cdrom0

---

### Post by bapoumba on 2006-12-11
> **DarkDancer said:**
> 
/dev/hda2             4.9G  4.2G  400M  92% /home


Just look up in your /home what is filling it, back up your files and make some room ;)

---

