---
title: "Encrypted Private Directory No Longer Auto-Mounting at Logon"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-20
As of today's updates to ecryptfs, my encrypted private directory no longer mounts automatically when I log in.

```
:~$ ecryptfs-mount-private
Enter your login passphrase: 
Inserted auth tok with sig [a57d8e97476acaf1] into the user session keyring
:~$ cd ~/Private
:~/Private$ ls
Documents  eBooks  Pictures
```

Mounting it myself works fine. Anyone else having this issue?

---

### Post by neferty on 2009-07-21
Yup, having the same issue ([http://ubuntuforums.org/showthread.php?p=7651579#post7651579](http://ubuntuforums.org/showthread.php?p=7651579#post7651579)). Took me time to figure out why my gnome wasn't loading :)

Someone has any ideas on this?

---

### Post by tekstr1der on 2009-07-21
@neferty: I filed [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/402222]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/402222") regarding this issue. Definitely a big deal if your entire /home is encrypted.

---

### Post by neferty on 2009-07-21
Okay. Seems work is in progress on this one :)

---

### Post by tekstr1der on 2009-07-22
This bug was fixed with today's updates in the package ecryptfs-utils - 77-0ubuntu1

---

### Post by neferty on 2009-07-24
hmm.. I have updated this package to the latest version, however it's still not auto-mounting correctly here... does someone else have this issue?

---

