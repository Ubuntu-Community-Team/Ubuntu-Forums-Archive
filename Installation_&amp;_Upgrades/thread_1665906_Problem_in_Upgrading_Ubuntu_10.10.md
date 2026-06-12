---
title: "Problem in Upgrading Ubuntu 10.10"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by bhubi2020 on 2011-01-12
I had upgraded Ubuntu 10.10 and it has completed sucessfully. I got an error message after restarting my PC. then, I cann't login and use this OS.
 
Error Message: " Install Problem 
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator"

---

### Post by sikander3786 on 2011-01-13
Welcome to the forums :-)

Seems like you run out of space on some of your partitions.

Press Ctrl + Alt + F1 at the login screen and login using your credentials. Then post the output of this command.

```
df -h
```

---

### Post by stevemidgley on 2011-01-18
Hi,

I'm having the same problem as the OP. Disk space is not a problem for me (at least). For the device in question, here's the df -h result:

/dev/sda1             142G  7.3G  127G   6% /media/disk

(The rest of the results aren't relevant b/c I'm booted into an external media linux install)

Thanks for any insights into what might be wrong.. Thanks.

---

### Post by stevemidgley on 2011-01-18
Hi,

I'm having the same problem as the OP. Disk space is not a problem for me (at least). For the device in question, here's the df -h result:

/dev/sda1             142G  7.3G  127G   6% /media/disk

(The rest of the results aren't relevant b/c I'm booted into an external media linux install)

Thanks for any insights into what might be wrong.. Thanks.

---

### Post by cmwslw on 2011-01-24
Any updates for this? I turned on my computer today and received the error above and could not login to my desktop. I got this error twice and on the third time I tried restarting the problem is now so bad that I don't even see an error message or a minimal login screen. It just stops at the Ubuntu 10.10 screen with the four dots below it. My last update was on the 20th. I did not turn on my computer after the 20th until two days ago, on the 22nd. There were also no problems yesterday on the 23rd.

sigh

IMPORTANT EDIT: I did end up finding a fix for this here: [http://ubuntuforums.org/showthread.php?p=10394907#post10394907](http://ubuntuforums.org/showthread.php?p=10394907#post10394907)

go to the end and read my latest post.

---

### Post by stevemidgley on 2011-01-25
For me it turned out to be xwindows config file settings. I commented out all the custom lines there that I had added (and strangely had been working but for whatever reason stopped working recently). I was able to reboot and get back into my primary OS. My solution seems pretty different from everyone else's so I wouldn't propose this as a general fix but I thought I should update the thread.

---

