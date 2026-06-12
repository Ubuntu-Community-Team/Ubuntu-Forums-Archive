---
title: "mount HDD external"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2009-11-23
hello all...
i have a issue....with ubuntu 9.10
i plug HDD (USB) on my pc, when i login the HDD appear on my desktop, but when switch user the other person not can use the HDD....
How can I make the HDD is used for all users..??

---

### Post by Claus7 on 2009-11-23
Hello,

plug the usb device and go to:
```
cd /media
```

and type:
```
ls -l
```

then you will see something like:

drwxrwxrwx  1 root  root  4096 2009-07-14 17:38 sda1
drwxr-xr-x  2 root  root  4096 2009-10-29 13:49 sdb1
drwx------ 12 YOUR_USER_NAME root 16384 1970-01-01 02:00 YOUR USB DRIVE

So, in order to change that you have to type:
```
sudo chown root /media/(name of usb drive)
also the:
sudo chgrp root /media/(name of usb drive)
```

I think that this will work.

Regards!

---

### Post by Mr_Lazy on 2009-11-23
I have exactly this problem, but when I try the chown command I get:

```
$sudo chown root /media/LaCie/
chown: changing ownership of `/media/LaCie/': Operation not permitted
```

I am pretty sure my password was correct, in fact I have trieed a few more times to make sure. It is very strange as I thought as an admin, you could get root privileges by using sudo.

---

### Post by chanfle on 2009-11-23
hello all....
i make the process mention claus, but when i loggin first appear my hdd...but if loggin second user not see the hdd....
any comments?

---

### Post by Claus7 on 2009-11-24
Hello,

reading this guide:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I would suggest you then to do:

chmod 777 /media/LaCie/ (where LaCie is the name of your device).

Regards!

---

