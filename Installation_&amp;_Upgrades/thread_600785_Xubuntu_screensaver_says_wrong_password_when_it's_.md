---
title: "Xubuntu screensaver says wrong password when it's correct"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by AncientPC on 2007-11-02
I'm upgrading from 7.04 -> 7.10 through Xubuntu on an old laptop (450Mhz Celeron, 64MB RAM).  The screensaver kicks in, however when I give it my username and password it says that my password is incorrect and refuses to clear the screen saver.

However if I switch to one of the consoles (tty2) my username and password just fine.  Does anyone know the screensaver process so I can kill it from the console?

Also, why is it aptitude dist-upgrade doesn't work and I have to upgrade through the GUI?

---

### Post by Bierstrich on 2007-11-02
Same problem for me:
It's not possible to unlock gnome screensaver. After entering my password, it's flickering 2-3 times and rejects my password, which is definitely correct, because I can logon on the console. To continue working I must kill the process.
> 
Does anyone know the screensaver process so I can kill it from the console?

```

bierstrich@P2003:~$ ps aux | grep screen
bierstrich    5889  ...   22:37   0:00 gnome-screensaver
bierstrich    5910  ...   22:37   0:00 gnome-screensaver-dialog --away-message=  --enable-switch
bierstrich@P2003:~$ kill -9 5889

```
Killing the dialog-process 5910 is not enough.

Any ideas? TIA

---

### Post by bapoumba on 2007-11-02
> **AncientPC said:**
> 
Also, why is it aptitude dist-upgrade doesn't work and I have to upgrade through the GUI?
Could you please post the error message ?

---

### Post by AncientPC on 2007-11-02
> **bapoumba said:**
> Could you please post the error message ?
There's no error message, but I'll be running 7.04 and try sudo aptitude dist-upgrade and it just acts like it's fully upgraded / nothing higher exists.

---

### Post by bapoumba on 2007-11-03
> **AncientPC said:**
> There's no error message, but I'll be running 7.04 and try sudo aptitude dist-upgrade and it just acts like it's fully upgraded / nothing higher exists.
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by AncientPC on 2007-11-03
Ahh . . . I don't have it anymore.  I just killed the computer with a hard reset and installed from 7.10 alternate CD.

However, I have never added / removed anything from the sources list, so it should be default.

---

