---
title: "LAN not detected"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by Hiuhu on 2012-11-17
I have a lenovo g580 and it does detect wired network I downloaded a LAN driver named ckmake-2012-07-03.log.bz2 in the desktop and when I try to install it this is what happens :
jemoh@Lenovo-G580:~$ tar -xvf ckmake-2012-07-03.tar.bz2
tar: ckmake-2012-07-03.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
What could be the problem with my installation procedure ?

---

### Post by NikTh on 2012-11-17
Hi , 

Please open a terminal (CTRL+ALT+T) and execute bellow commands with order. (Active Internet connection required)

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
sudo ./wirelessinfo
```The last command will produce a file named **netinfo.txt** inside your /home folder.
Click on "New Reply" and attach the file. [See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

_Above is a script for debugging proposes. All your sensitive data are hidden for security reasons. _

Thanks

---

### Post by Hiuhu on 2012-11-17
Ok thanks thats what I get

---

### Post by Hiuhu on 2012-11-17
Thats what I get but the LAN is still not working

---

### Post by NikTh on 2012-11-17
Hi , 

try this command 
```
sudo rfkill unblock all
``` 

is wireless OK now ? 

Thanks

---

