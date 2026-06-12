---
title: "BPALogin &amp; Bigpond Cable (Australia)"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by bernard on 2005-07-15
Can anyone tell me how to get Ubuntu connected to the Internet with BigPond Cable (Australia). The Debian package 'bpalogin' is required for Linux connections and after downloading this to a floppy and with the wonderful help and guidance provided by the 'Libranet Support' team, I have been successfull in connecting with both Libranet GNN/Linux and Debian. Unfortunately however, using this floppy hasn't worked with Ubuntu although there is every appearance of an authentic connection. If there is anyone with the possible remedy it would be greatly appreciated. [http://ubuntuforums.org/newthread.php?do=newthread&f=56#](http://ubuntuforums.org/newthread.php?do=newthread&f=56#)
 :???:

---

### Post by donvella on 2006-05-07
Im having similar trouble, how about a trade of information :P
[http://bpalogin.sourceforge.net/download/bpalogin-2.0-linux-2.4.bin](http://bpalogin.sourceforge.net/download/bpalogin-2.0-linux-2.4.bin) Will give you the shell script you need to install bpalogin.

All you do is goto console and type 
"sudo ./bpalogin-2.0-linux-2.4.bin" then it will install itself and place itself into 
"/etc/rc.d/init.d/bpalogin and then you just type sudo bpalogin start"

Now i have then typed "update-rc.d bpalogin defaults 20" and i get this message 

"don@linux:~$ update-rc.d bpalogin defaults
 System startup links for /etc/init.d/bpalogin already exist. "

True, it does exist, and there is a S20bpalogin in the rc.d's but it wont load on startup, i must type in the startup script for it every time, little help please.

---

### Post by donvella on 2006-05-07
No worries at all, just use the synaptic package manager to install and walah. :P

---

### Post by elcu on 2006-05-10
What's the recommended way to stop the service?  I'm guessing doing a 'killall bpalogin' is not the best way to do things?

---

### Post by Jason_25 on 2006-05-10
Should be
```

sudo /etc/init.d/bpalogin stop

```
or
```

sudo invoke-rc.d bpalogin stop

```

---

### Post by deanjm1963 on 2006-05-13
I use bpalogin. The easiest way to get it up and running is this.

Install bpalogin

then open a terminal and type
sudo gedit /etc/bpalogin.conf

set your name where is says username **joebloggs** (or whatever your username is)
set your password where it says password **goldilocks** (or whatever your password is)

Then scroll down to the very bottom of the file and uncomment

minheartbeatinterval 60 

maxheartbeatinterval 420

save and close the file

to get it to start automatically

again, in a terminal

sudo gedit /etc/network/interfaces and make the following changes

# The primary network interface
**auto eth0**
iface eth0 inet dhcp
**pre-up /usr/sbin/bpalogin start**

save and close the file. make sure you have a carriage return after the last line.

---

