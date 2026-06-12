---
title: "pppd only as root. SHOWSTOPPER!"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by beauman on 2008-10-26
[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289575](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289575)

---

### Post by mindwarp on 2008-10-26
How about doing an 'ls -la /usr/sbin/pppd' and paste it here

---

### Post by Eclipse. on 2008-10-26
Nominated it for intrepid so it hopefully gets some attention.

---

### Post by glasen on 2008-10-26
Your user must be in the group "dip" :

ls -l /usr/bin/pppd

-rwsr-xr-- 1 root dip 273064 2008-10-16 03:51 /usr/sbin/pppd


cat /etc/group | grep "dip" :

dip: x:30:glasen

---

### Post by beauman on 2008-10-26
Ok, I opened "System"-->"Administration"-->"Users and Groups".
Under "Manage Groups", there is no group "dip".
So I created it and added my user. Then I rebooted. 
That didn't work.


I also tagged the bug report with: intrepid ibex showstopper

---

### Post by lswb on 2008-10-26
Looking at the same error messages posted in the bug report you linked to, it appears the only thing wrong is that pppd is not in the user's path, or at least not in the path that gnome-ppp is using. Try this in a terminal:

PATH=/usr/sbin:$PATH gnome-ppp

or, based on the error messages in the bug post, 
"specify a "PPPD Path" option in wvdial.conf"
That would be referring to /etc/wvdial.conf See man wvdial for correct syntax for the path statement in wvdial.conf.

/usr/sbin really should be in the default path. The system wide default path is set in /etc/environment. Make sure that /usr/sbin is included, or add it to your .profile in your home directory

---

### Post by beauman on 2008-10-26
> **glasen said:**
> 

cat /etc/group | grep "dip" :

dip: x:30:glasen

The group id really must  be "30". Then it works.
I first tried "1001", the number the 
"New group"-dialog proposed me.


The connection log still reports some problems:

--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied

But it works now.

```

yo@LosBastardos:~$ which pppd
/usr/sbin/pppd

```


Friendly regards,
beauman

---

