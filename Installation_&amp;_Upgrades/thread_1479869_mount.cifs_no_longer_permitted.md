---
title: "mount.cifs no longer permitted"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by radiognome on 2010-05-11
I used to have some samba-shares in fstab with a credentials-file and such, so I could mount and unmount them without 'sudo' in cron-jobs, scripts etc...

This worked for years until I upgraded to 10.4 (skipped 9.10)
I now get:
mount error(1): Operation not permitted

(and a full partition on my server because all automatic backups were written at the mount-point in the directorystructure since the upgrade)

When I 'sudo' the mount, it works, but hey, that was not what I wanted.

Apart from this, upgrading to 10.04 LTS 64-bit worked like a charm.

When I get this issue solved, I would mark 10.04 a :KS:KS:KS:KS:KS

---

### Post by mehturt on 2010-05-12
try:
sudo chmod +s `which mount.cifs`
I am not sure whether this is the proper solution.
EDIT: I just found a bug about this.. [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805)

---

### Post by radiognome on 2010-05-12
Thanks mehturt,

Silly I didn't find this launchpad bugentry myself. Probably used all 'just not the propper mix of searchwords' before giving up.

Will try this as soon as I get back at the office on friday. Not having proper automated database-dumps starts getting itchy :)

---

### Post by GrokIt on 2010-05-18
I had the same problem and I fixed it with these 2 commands
```

sudo chmod +s /sbin/mount.cifs
sudo chmod +s /sbin/umount.cifs
```
Works just like before now.

---

### Post by radiognome on 2010-05-18
Thanks GrokIt

I used the same commands, and since then forgot about it.

Funny... Don't know why this set-bit suddenly causes trouble sincd 10.04 and don't know why people are against it (see bug-report). Hope this gets settled proper and for all.

---

### Post by GrokIt on 2010-05-18
Yeah it looks like a security problem from what I see.  I hope it's just something that can be fixed.  This will drive new users batty. 
Someone on the Kubuntu list is asking almost the same thing, except he has a gui problem.  It's nice to able to spread the help.

---

### Post by Ganton on 2010-05-26
All was done on purpose to avoid security attacks.

Instead of changing the "setuid bit"... use first "sudo visudo" and later "sudo".

More information in:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805/comments/10](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805/comments/10)

---

### Post by lotharmat on 2010-08-27
> **GrokIt said:**
> I had the same problem and I fixed it with these 2 commands
```

sudo chmod +s /sbin/mount.cifs
sudo chmod +s /sbin/umount.cifs
```
Works just like before now.

Thanks for this!  - It was driving me insane

Using..

sudo mount.cifs

was leaving me unable to copy files into the mounted share! (unless I used the terminal and prefixed the mv command with sudo too.

---

### Post by war59312 on 2013-02-10
Not working for me:

> Couldn't open /etc/fstab for reading!

Whoops, just realized this thread is really old... whoops.. cant delete it seems..

sorry..

ok i see it wont be fixed, ever. for good reasons.. oh well

see: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805)

---

### Post by oldos2er on 2013-02-10
Old thread closed.

---

