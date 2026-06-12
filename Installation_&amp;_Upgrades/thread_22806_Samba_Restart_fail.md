---
title: "Samba: Restart fail"
date: 2005-03-29
forum: Installation &amp; Upgrades
---

### Post by hubris on 2005-03-29
Ok

i messed around with samba.
I followed the ubuntu guide on the install.

i made one critical error

i wrote new config files over the backup config file :(

at first the share worked (it's a file share i'm setting up)

a few hours later and a bit more messing about i got this:

```

 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons..                                              [fail]

```



I realised how stupid it was of me to overwrite the file and simply deleted the two config (samba.conf and samba.conf_backup)

I removed Samba from the system with:

```
sudo apt-get remove samba
``` 

Then i did a reïnstall of it:

```
sudo apt-get install samba
``` 

then i got this:

```


Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
  samba-doc
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
Need to get 0B/2300kB of archives.
After unpacking 5984kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 61334 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.7-1ubuntu6.3_i386.deb) ...
Setting up samba (3.0.7-1ubuntu6.3) ...
 * Starting Samba daemons..                                              [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So it still fails to start up the deamons.

Can someone help me?

I really wanna get this up and running

thx
Hubris

---

### Post by hubris on 2005-03-30
Maybe this can help it got mailed to the root account:

```

From root@localhost.localdomain  Sun Mar 27 19:12:14 2005
X-Original-To: root
To: root@localhost.localdomain
Subject: Segfault in Samba
Date: Sun, 27 Mar 2005 19:12:14 +0200 (CEST)
From: root@localhost.localdomain (root)

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for pid 6131 (/usr/sbin/smbd).

Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occured.  You are
encouraged to submit this information as a bug report to Debian.  For
information about the procedure for submitting bug reports , please see
http://www.debian.org/Bugs/Reporting or the reportbug(1) manpage.

(no debugging symbols found)...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0x4022ce43 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x401c3c36 in system () from /lib/tls/i686/cmov/libc.so.6
#3  0x081c2ccf in smb_panic2 ()
#4  0x081c2c5d in smb_panic ()
#5  0x081b1ec2 in dbgtext ()
#6  <signal handler called>
#7  0x401f6969 in mallopt () from /lib/tls/i686/cmov/libc.so.6
#8  0x00000028 in ?? ()
#9  0x402b48a8 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#10 0x00000000 in ?? ()
#11 0x402b4894 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#12 0x402b4884 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#13 0x402b3edc in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0x00000408 in ?? ()
#15 0x00000001 in ?? ()
#16 0x00000400 in ?? ()
#17 0x401f61a4 in mallopt () from /lib/tls/i686/cmov/libc.so.6
#18 0x402b4860 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#19 0x00000016 in ?? ()
#20 0x00000000 in ?? ()
#21 0x00000000 in ?? ()
#22 0x00000002 in ?? ()
#23 0x00000002 in ?? ()
#24 0x00000017 in ?? ()
#25 0x00000048 in ?? ()
#26 0x00000408 in ?? ()
#27 0x402b4860 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#28 0x402b3edc in ?? () from /lib/tls/i686/cmov/libc.so.6
#29 0x402b4860 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#30 0x00000001 in ?? ()
#31 0x00000400 in ?? ()
#32 0x401f5503 in malloc () from /lib/tls/i686/cmov/libc.so.6
#33 0x402b4860 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#34 0x00000400 in ?? ()
#35 0x0828918a in pipe_names ()
#36 0x00000400 in ?? ()
#37 0x082f1b28 in ?? ()
#38 0xbfffeb18 in ?? ()
#39 0x081c2059 in Realloc ()

```


Hopefully someone can help me get this solved

---

### Post by cvmostert on 2005-09-02
HI there, I also have the same problem with samba... restart fails... I must say, i am a newbie with ubuntu and linux. I have a XP laptop and this ubuntu desktop... I have a cable modem and a US Robotics router... both pc's connects fine to the internet through it... but i want a connection between the two computers aswell.. i'm not a network wizz eather.. so i was trying to start samba... to try and see and mount my windows pc...  

thanx for the advice in advance..
Chris

---

