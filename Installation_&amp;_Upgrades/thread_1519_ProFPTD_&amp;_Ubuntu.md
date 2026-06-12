---
title: "ProFPTD &amp; Ubuntu"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by Novocaine on 2004-10-21
Help 
I can't start my ftp server :p
novo@ubuntu:~ $ sudo proftpd restart
localhost.localdomain - error converting stdin to IPv6 socket: Socket operation on non-socket
localhost.localdomain - fatal: Socket operation on non-socket


HELP ME ! :D :D

---

### Post by cybrjackle on 2004-10-21
> 4.4 "Fatal: Socket operation on non-socket"

You have ProFTPD configured to run in inetd mode rather than standalone. In this mode, ProFTPD expects that it will be run from the inetd super-server, which implies that stdin/stdout will be sockets instead of terminals. As a result, socket operations will fail and the above error will be printed. If you wish to run ProFTPD from the shell, in standalone mode, you'll need to modify your proftpd.conf configuration file and add or edit the ServerType directive to read:

ServerType standalone


[http://linux.tnc.edu.tw/techdoc/proftpdfaq-full.htm](http://linux.tnc.edu.tw/techdoc/proftpdfaq-full.htm)

sudo apt-get install vsftpd

 :lol:

---

### Post by FLeiXiuS on 2004-10-21
cybrjackle has provided you with a FAQ, but I'll go ahead and tell you anyways!  Its much easier coming from someone who has done it plenty of times then someone who is trying to be Linux Literate.

First off, 

Open your ProFTP configuration file with your favorte editor ($EDITOR)
```
sudo $EDITOR /etc/proftd.conf
```

Search for ```
ServerType inetd
```

Then change the inted to standalone.
```
ServerType standalone
```

Save file!

Last but not least make sure nothing is already running on port 21.
```
netstat -nap|grep 21
```

If all is good, ```
sudo proftpd -c /etc/proftpd &amp;
```

---

### Post by cybrjackle on 2004-10-21
Well, I assumed if he/she was using proftpd they knew how to edit the config :)

---

### Post by Novocaine on 2004-10-22
Euh ... :D I'm a beginner in the world of linux :p :p

Ok it's running but what are the differencies between vsftpd and proftpd ?? 

ps : i'm a frenchy so my english is not perfect ;) ;)

---

### Post by cybrjackle on 2004-10-22
Just a personel preference, 

vsftpd has been said to be faster and more secure (as secure as ftp can get) ;)

With vsftp if you allow your users to login, you can jail them to only view/get in there home dir and no were else.  I'm not sure if you can do that with proftpd or not, been awhile since I used it.

A lot of Distros/mirrors/kernel.org use vsftpd because they all feel that it is faster and more secure than the rest.

Keep this in mind if your allowing your users to login in through ftp, you better not be using your first user you created with "sudo" access, otherwise everybody  is watching your password being sent in CLEAR text.  Well, you just gave them sudo to your system 8)

I either use annoymous for download only or dummy accounts for uploads.

---

### Post by cybrjackle on 2004-10-22
Linux Literate  &lt;---- that cracks me up :lol:

---

### Post by FLeiXiuS on 2004-10-22
Well, if he recalls him being a *newbie* then he/she wouldn't know what to do.  We were all once newbs in the world of linux.  I remember I had forgotten where the configs were located...and when your experiences linux you have to learn how to use your great web searching tools to solve problems.  I may suggest that all new linux users would refer to googling first.


cybrjackle. really good point about FTP.  I wouldn't use your primary account as FTP login. :lol:

---

### Post by Novocaine on 2004-10-23
I use google but I can't find the informations I need :p

So I've post here ;)

Thx 

PS : i'm a guy :)

---

