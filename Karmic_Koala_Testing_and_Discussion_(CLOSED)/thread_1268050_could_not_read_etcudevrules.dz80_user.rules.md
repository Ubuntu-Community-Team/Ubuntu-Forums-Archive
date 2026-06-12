---
title: "could not read /etc/udev/rules.d/z80_user.rules"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JCoster on 2009-09-16
After finally booting to xserver this morning after upgrading packages and finding that network-manager-pptp had been corrupted (I assume because of the network-manager cockup) I ran a
```
 sudo apt-get install --reinstall network-manager-pptp 
```


After rebooting, I get greeted with:
```

udevd could not read /etc/udev/rules.d/z80_user.rules
```
Any ideas? This occurs in recovery mode or standard.

---

### Post by JCoster on 2009-09-16
*bump*

---

### Post by ayates on 2009-09-16
Check this: [http://ubuntuforums.org/showthread.php?t=1267658](http://ubuntuforums.org/showthread.php?t=1267658)

---

### Post by trulan on 2009-09-16
...and this:
[https://bugs.launchpad.net/ubuntu/+s...ev/+bug/430654]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654")

Looks like this one is no big deal.  I guess we're all a little jumpy after the last round of alpha excitement. ;)

---

### Post by JCoster on 2009-09-17
Thanks for those posts guys.

Only thing is, my system actually hangs on the message?  

It's not a case of the errors just appearing and Ubuntu loading past it.

I think it could be a problem with the permissions of the file?  Some of my other permissions got screwed up with the 'alpha excitement.'  (certainly wasn't too exciting at the time...)

---

