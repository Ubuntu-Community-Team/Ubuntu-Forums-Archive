---
title: "Update Manager Completly Borked"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-03-14
I did initially post in this thread but now I think they are not related.

[http://ubuntuforums.org/showthread.php?t=1095612](http://ubuntuforums.org/showthread.php?t=1095612) 

Updated this morning and Update Manager failed near the end with Unexpected Exit. No crash report because crash report crashes....

Trying to run again gives -- Update Manager fails with segmentation fault.


Syslog now shows

> Mar 14 08:14:55 toshsat kernel: [  100.656610] update-manager[3848]: segfault at e649e100 ip b7f54613 sp bffc818c error 4 in libc-2.9.so[b7edd000+15c000]
Mar 14 08:15:11 toshsat kernel: [  117.217068] apt-check[3867]: segfault at e8bf9100 ip b7f66613 sp bffdbd8c error 4 in libc-2.9.so[b7eef000+15c000]
Mar 14 08:16:59 toshsat kernel: [  224.472238] aptitude[3982]: segfault at e8891100 ip b7a4e613 sp bf94ab2c error 4 in libc-2.9.so[b79d7000+15c000]
Mar 14 08:17:02 toshsat /USR/SBIN/CRON[4049]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 14 08:20:01 toshsat /USR/SBIN/CRON[4194]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Mar 14 08:20:04 toshsat kernel: [  410.157910] apport-gtk[4186]: segfault at e6abe100 ip b7f4a613 sp b6281eec error 4 in libc-2.9.so[b7ed3000+15c000]
Mar 14 08:20:05 toshsat kernel: [  411.239895] apt-check[4331]: segfault at e8c58100 ip b7f3d613 sp bfeb280c error 4 in libc-2.9.so[b7ec6000+15c000]
Mar 14 08:20:38 toshsat kernel: [  444.043967] apport-gtk[4479]: segfault at e649c100 ip b7dcd613 sp b5c5feec error 4 in libc-2.9.so[b7d56000+15c000]
Mar 14 08:21:34 toshsat kernel: [  500.121574] apport-gtk[4561]: segfault at e62ec100 ip b7ec5613 sp b5aafeec error 4 in libc-2.9.so[b7e4e000+15c000]

---

### Post by Peter09 on 2009-03-14
anyone suggest a fix for this?

---

### Post by taavikko on 2009-03-14
> **Peter09 said:**
> anyone suggest a fix for this?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Peter09 on 2009-03-14
Nope the above code just gives segmentation errors.

---

### Post by taavikko on 2009-03-14
> **Peter09 said:**
> Nope the above code just gives segmentation errors.

So the commands doesn't produce any erros (dpkg)
it just segfaults while handling the command?

Output from cli would help greatly...

---

### Post by paul_in_london on 2009-03-14
Try:

sudo rm -vf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade

Sometimes aptitude gives a segfault when apt-get doesn't so try that as well.

If this doesn't work, reboot and try repeating the above commands.

Another thing to try is reboot in recovery mode and select fix broken packages or whatever it's called.

As part of that process it'll do the equivalent of an apt-get update. You should then be able to apply any available updates before you resume the boot.

---

### Post by Peter09 on 2009-03-15
Thanks Paul that seems that have done the trick.

---

