---
title: "Trouble with updating install and startx"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by neilford on 2007-01-11
I installed 6.06 onto my system and it worked fine. I ran the updater to get the
most recent files. After doing this the X windows errors and does not run. I 
booted up in text mode and tried running startx. When I do, I get an error
that it can't find /dev/wacom. I looked in my xorg.conf file and I see that there
is a device wacom that accesses /dev/wacom, but there is no such thing in
my /dev directory. How can I fix this? Thanks.

neilford

---

### Post by scrooge_74 on 2007-01-11
do cd /etc/X11

then 

sudo nano xorg.conf

and in front of those lines with that device mentioned put a # to comment the line out and then try to restart the X server

---

### Post by neilford on 2007-01-11
I tried this and ended up with X-windows still not working. I had to comment out everything relasted to the wacom, but it still failed to boot up X-windows.

Is there a way to reconfigure the xorg.conf file without manually typing. I think I could do this in suse with some kde program. Thanks

neilford


> **scrooge_74 said:**
> do cd /etc/X11

then 

sudo nano xorg.conf

and in front of those lines with that device mentioned put a # to comment the line out and then try to restart the X server

---

### Post by scrooge_74 on 2007-01-11
the command is 

sudo dpkg-reconfigure xserver-xorg

---

### Post by neilford on 2007-01-12
I tried this and failed. The thing is, this problem occurs when I run the updates, which makes me feel that one or more of the updates are creating this problem. Before I run
the update, the wacom input device is in the xorg.conf file and does not error. After
I run the updates, it is still in the file and then I get the problem. I noticed in the updates there is an upgrade for xinit. I was tempted to not run this, since this program directily afects the X-server, but it noted some security issues so I ran it. Could this be cusing the problem and if so how could I fix it? Thanks.

neilford

> **scrooge_74 said:**
> the command is 

sudo dpkg-reconfigure xserver-xorg

---

### Post by scrooge_74 on 2007-01-12
Not sure the reason, but I recommend you start by doing man xinit from a terminal maybe you can learn something from there that could point you in the right direction

---

