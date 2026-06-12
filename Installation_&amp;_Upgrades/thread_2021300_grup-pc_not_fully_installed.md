---
title: "grup-pc not fully installed"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by lewis91 on 2012-07-09
hey ubuntuforums,

I just started at a new company and we are using ubuntu now (I used debian in the past). 

I just want to update an important server but grup-pc replies with a error.

Server:
```
root@aruba-ng:~# uname -a
Linux aruba-ng 2.6.32-39-server #86-Ubuntu SMP Mon Feb 13 23:15:11 UTC 2012 x86_64 GNU/Linux
```

apt-get install -f
```
root@aruba-ng:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 77 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu13) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

dpkg
```
root@aruba-ng:~# sudo dpkg --configure -a
Setting up grub-pc (1.98-1ubuntu13) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
```

apt-get check
```
root@aruba-ng:~# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

I really searched the whole web and I found a lot of threads with this problem but the all couldn't help me. I really don't want to purge grup-pc and reinstall it because I heard that this might be a bad idea.

Thanks in advance.

daniel

---

### Post by darkod on 2012-07-09
Purging and reinstalling grub-pc can't be a bad idea, especially when not working.

But before that, did you try something like:
```
sudo dpkg --configure grub-pc
```

I think it will give an error also, but it's worth trying.

---

### Post by lewis91 on 2012-07-09
hey I tried it before (was in one of the other forums I searched before)

same result:

```
root@aruba-ng:~# dpkg --configure grub-pc
Setting up grub-pc (1.98-1ubuntu13) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
```

I know but I saw some users who couldn't reinstall grup-pc after purging it..

Is there really no other way to solve this problem?

daniel

---

### Post by Lyfang on 2012-07-09
How were you able to boot Ubuntu without grup-pc not fully installed? Have you tried to reinstall GRUB 2 from the Terminal? Reminder: Is done at your own risk (as usual)!:

```
sudo apt-get purge grub-pc && sudo apt-get update && sudo apt-get install grub-pc
```Logged in as a superuser (root):
```
apt-get purge grub-pc && apt-get update && apt-get install grub-pc
```

---

### Post by lewis91 on 2012-07-09
Hey thanks for your reply.

the server is running for over 100 days and I just started at the company a week ago. So I don't know if the server starts normally. 

daniel

---

