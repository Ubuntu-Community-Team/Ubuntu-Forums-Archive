---
title: "Lucid, scp, error"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by amindomao on 2010-05-26
good day.
I installed ubuntu lucid yesterday and now have such problem.
Before installing lucid (i had 9.10) i've backup'd my data to backup server via scp (some big .tar files). Now, when i try to get it back i see on my laptop:

amindomao@sc:~$ scp [email]amindomao@10.20.30.8:docu.tar[/email] .
amindomao@10.20.30.8's password: 
docu.tar                                                                                                                                                             0%    0     0.0KB/s   --:-- ETA
Corrupted MAC on input.
Disconnecting: Packet corrupt
lost connection

and on server side:

May 26 14:29:50 bu sshd[4367]: Accepted password for amindomao from 10.20.30.5 port 35906 ssh2
May 26 14:29:50 bu sshd[4367]: pam_unix(sshd:session): session opened for user amindomao by (uid=0)
May 26 14:29:51 bu sshd[4369]: fatal: Write failed: Broken pipe
May 26 14:29:51 bu sshd[4367]: pam_unix(sshd:session): session closed for user amindomao

what can it be?

---

### Post by hoover67 on 2010-09-22
Me too, same issue here on Linux Mint 9 which is based on 10.04 I believe. Sometimes, the transfer fails at the exact same place, sometimes randomly. 

I'm on an HP desktop, 32bit system, system is current and up-to-date patch-wise. 

Uwe

---

### Post by efflandt on 2010-09-22
Maybe it is a configuration issue somewhere or permissions of ~/.ssh (which should be 700) or files in it (which should be 600 permission).

Did you check the file after you originally uploaded it to make sure it was the proper size?  Does everything work normally when you ssh to that server?

I don't think anything major changed in ssh recently.  This is an scp example of the largest file I had on an old SuSE box (Celeron 300) that has not even been rebooted since July 2006:

SuSE---modem/router---wireless/router . . . Zyxel as wireless client---Lucid 64-bit

efflandt@efflandt-wd160:~/Downloads$ scp mainpc:sandiegopoint.iso .
sandiegopoint.iso 100% 21MB 701.9KB/s 00:31    
efflandt@efflandt-wd160:~/Downloads$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
efflandt@efflandt-wd160:~/Downloads$ ssh mainpc
Last login: Wed Sep 22 20:36:29 2010 from 172.16.0.68
Have a lot of fun...
efflandt@realhost:~> cat /etc/*release
SuSE Linux 8.2 (i586)
VERSION = 8.2
efflandt@realhost:~> ls -l /var/log/boot*
-rw-r-----    1 root     root            0 2003-05-17 18:03 /var/log/boot.log
-rw-r--r--    1 root     root        20461 2006-07-20 16:00 /var/log/boot.msg
-rw-r--r--    1 root     root        24670 2006-07-20 04:45 /var/log/boot.omsg

---

