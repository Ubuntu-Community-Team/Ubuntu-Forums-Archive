---
title: "Inusertemp - kde install via synaptic"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by linux6994 on 2009-08-02
I am running karmic gnome and installed kubuntu-desktop and kdm, when attempting to bring up kde session I get a call to inusertemp stating I should check installation.

Any ideas, I know we are in Alpha3  and all is in testing but I figured I would give it a try.

I have plenty of room:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             42196172  13623160  26429544  35% /
tmpfs                   513008         0    513008   0% /lib/init/rw
varrun                  513008       320    512688   1% /var/run
varlock                 513008         0    513008   0% /var/lock
udev                    513008       268    512740   1% /dev
tmpfs                   513008       108    512900   1% /dev/shm
/dev/sda2             32346876  14576360  17770516  46% /media/32A8A0A7A8A06B55_

---

### Post by linux6994 on 2009-08-02
Just a bump, any ideas folks?

---

### Post by wayne_cat on 2009-08-02
check you .xsession-errors file. There should be an error message with further information.

The error message should start with:
```

startkde: ERROR:
```

---

### Post by linux6994 on 2009-08-02
startkde: Call to lnusertemp failed (temporary directories full?). Check your installation.

This is all that it says.

---

### Post by wayne_cat on 2009-08-02
do you get more information if you run these 2 commands?
```
lnusertemp tmp

lnusertemp socket

```could you please post the result from

```
ls -la /tmp
ls -la /var/tmp
```

edit: forgot /var/tmp

---

### Post by linux6994 on 2009-08-02
looks like .kde is not there?

dad@dad-laptop:~$ lnusertemp tmp
Error: "/home/dad/.kde/tmp-dad-laptop" is not a link or a directory.
dad@dad-laptop:~$ lnusertemp socket
Error: "/home/dad/.kde/socket-dad-laptop" is not a link or a directory.
dad@dad-laptop:~$ ls -ls /tmp
total 56
4 drwx------ 2 root root 4096 2009-08-02 20:21 kde-root
4 drwx------ 2 dad  dad  4096 2009-08-02 21:01 keyring-FJ0wZP
4 drwx------ 2 dad  dad  4096 2009-08-02 21:29 keyring-ir8xhY
4 drwx------ 2 dad  dad  4096 2009-08-02 21:05 keyring-MC76Vy
4 drwx------ 2 dad  dad  4096 2009-08-02 21:29 keyring-ynNhe9
4 drwx------ 2 dad  dad  4096 2009-08-02 21:32 orbit-dad
4 drwx------ 2 root root 4096 2009-08-02 21:28 orbit-root
4 drwx------ 2 dad  dad  4096 2009-08-02 21:31 plugtmp
4 drwx------ 2 dad  dad  4096 2009-08-02 21:29 pulse-jPCS8qKX8cxb
4 drwx------ 2 dad  dad  4096 2009-08-02 21:29 ssh-TpNtBx7117
4 drwx------ 2 dad  dad  4096 2009-08-02 20:22 virtual-dad.b7Au8K
4 drwx------ 2 dad  dad  4096 2009-08-02 21:02 virtual-dad.DbKB52
4 drwx------ 2 dad  dad  4096 2009-08-02 21:06 virtual-dad.hr234J
4 drwx------ 2 dad  dad  4096 2009-08-02 21:29 virtual-dad.SJhsZp
dad@dad-laptop:~$ ls -ls /var/tmp
total 8
4 drwx------ 3 dad  dad  4096 2009-08-02 10:59 kdecache-dad
4 drwx------ 2 root root 4096 2009-07-24 13:56 kdecache-root
dad@dad-laptop:~$

---

### Post by wayne_cat on 2009-08-02
Gnome works? ... and you can create files in your home folder?

---

### Post by linux6994 on 2009-08-03
Yes GNOME works just great as usual, I can install apps and all is fine except for Kubuntu desktop.

I am will not be back to my Linux laptop for a couple of weeks since my daughter is using it and I am out of town. I was thinking of manually creating the .kde directory manually.

---

