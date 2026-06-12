---
title: "/var/log became huge"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by liorwohl on 2009-03-14
hello,

i have a separate /home partition so i left only 7GB for root, and now this partition is almost full because i have 2.6GB of logs.. this folder is usually tiny, so it's looks weird to me.

there are 4 log files there that take most of that space:
user.log (68MB)
syslog (68MB)
user.log.0 (1.2GB)
syslog.0 (1.2GB)

what should i do and is it a bug?

thanks

---

### Post by Kevbert on 2009-03-14
Looks like you have some serious problems which need looking at. Are you using the new ext4 format or the old ext3 ? Kubuntu or Ubuntu ?
I'm using both Ubuntu and Kubuntu with ext3 (since Alpha1) and the largest log file is under 1Mb.

---

### Post by liorwohl on 2009-03-14
i'm using ext3 and ubuntu 64bit

---

### Post by MJWitter on 2009-03-14
Using ext3 and Ubuntu and have the same issue, 790MB of logs, user.log.0 and syslog.0 being just over 700MB between them..

---

### Post by liorwohl on 2009-03-14
i opend the 68MB files file and they full of this:
> Mar 14 11:02:27 liorwohl-desktop pulseaudio[4128]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058053646096212 bytes (418284241651 ms) Most likely this is a Linux bug. Please report this issue to the ALSA developers.(~274000 lines like that on each file)

when i tried to open the 1.2GB file it took all my ram and swap so i killed it


(i installed fresh install of alpha 6 just yesterday)

---

### Post by t.alex on 2009-03-14
here is the bug report
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/320875](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/320875)

---

### Post by sahabcse on 2009-03-14
For removing the log information run

echo " " >/var/log/user.log

---

### Post by liorwohl on 2009-03-14
i don't see the files growing, so do i need to delete them and see if they became huge again?

edit:

liorwohl@liorwohl-desktop:~$ sudo echo " " >/var/log/user.log.0
bash: /var/log/user.log.0: Permission denied
liorwohl@liorwohl-desktop:~$ sudo echo " " >/var/log/user.log
bash: /var/log/user.log: Permission denied
liorwohl@liorwohl-desktop:~$ echo " " >/var/log/user.log.0
bash: /var/log/user.log.0: Permission denied
liorwohl@liorwohl-desktop:~$ echo " " >/var/log/user.log
bash: /var/log/user.log: Permission denied
liorwohl@liorwohl-desktop:~$

---

### Post by Kevbert on 2009-03-14
It may be worth adding a comment to the bug report (noted in post #6).  It looks like it is still work in progress, so even if you delete the large log files you'll generate new (large) ones. To delete the files enter
```
sudo rm /var/log/user.log
sudo rm /var/log/user.log.0
```
[B]Be very careful with the 'rm' command as it could screw up the operating system if you get the command wrong...
[/B]
Alternatively use the command shown in post #7 prefixed with 'sudo'.

---

### Post by KrazyPenguin on 2009-03-14
xdiskusage is a cool program that quickly shows you where you memory has gone.

I had this problem with 8.10 , and yes, just delete them.

---

### Post by sahabcse on 2009-03-14
Hi

Log in to the root user

sudo bash

Then run echo " " >/var/log/user.log.0

---

### Post by Ng Oon-Ee on 2009-03-14
I have the exact same problem. I just deleted the logs, since I don't have time now to track it down. Am on 32bit as well, and never had this problem in intrepid or prior to that.

---

### Post by Kevbert on 2009-03-14
> **Ng Oon-Ee said:**
> I have the exact same problem. I just deleted the logs, since I don't have time now to track it down. Am on 32bit as well, and never had this problem in intrepid or prior to that.

Please remember that Jaunty is still in Alpha. A lot of the code has been imported from Debian/Lenny (from which Ubuntu is derived) rather than re-used from Intrepid.

---

