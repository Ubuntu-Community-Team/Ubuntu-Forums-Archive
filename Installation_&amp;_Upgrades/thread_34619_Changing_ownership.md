---
title: "Changing ownership"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by derkins1 on 2005-05-15
N00b

I have to type 'startadsl' in a terminal window to connect, fine I don't want it on at boot up. However as I had to install the modem software as root, I can only start it from root. I know I need to use 'chown' to enable my general username to be able to run it but how do I find 'startadsl'?

Thanks.

---

### Post by alastair on 2005-05-15
You can find a program by typing :

which <program>

or 

locate <program>

---

### Post by derkins1 on 2005-05-15
Thanks again.

I found it but considered that changing ownership might not be the best thing. It is in root@ubuntu:/usr/local/sbin

-rwxr-xr-x  1 root root  1603 2005-05-14 18:20 startadsl
-rwxr-xr-x  1 root root   852 2005-05-14 18:20 stopadsl

I thought this meant that any user could execute it but maybe it depends on the paths username looks in?. However 'sudo startadsl' works.

But further investigation also found the files in [username]@ubuntu:/usr/local/sbin however it won't run ?-
[username]@ubuntu:/usr/local/sbin$ ls
eagleconfig       eaglectrl  eaglestat     fctStopAdsl  _startadsl_  _stopadsl_
eagleconnect.tcl  eaglediag  fctStartAdsl  pppoa        startmire
[username]@ubuntu:/usr/local/sbin$ startadsl
bash: startadsl: command not found
[username]@ubuntu:/usr/local/sbin$

---

### Post by Sam on 2005-05-15
[QUOTE=derkins1]Thanks again.

I found it but considered that changing ownership might not be the best thing. It is in root@ubuntu:/usr/local/sbin

-rwxr-xr-x  1 root root  1603 2005-05-14 18:20 startadsl
-rwxr-xr-x  1 root root   852 2005-05-14 18:20 stopadsl

I thought this meant that any user could execute it but maybe it depends on the paths username looks in?. However 'sudo startadsl' works.

But further investigation also found the files in [username]@ubuntu:/usr/local/sbin however it won't run ?-
[username]@ubuntu:/usr/local/sbin$ ls
eagleconfig       eaglectrl  eaglestat     fctStopAdsl  _startadsl_  _stopadsl_
eagleconnect.tcl  eaglediag  fctStartAdsl  pppoa        startmire
[username]@ubuntu:/usr/local/sbin$ startadsl
bash: startadsl: command not found
[username]@ubuntu:/usr/local/sbin$[/QUOTE]
Try
```
$ cd /usr/local/sbin
$ ./startadsl
```
or
```
$ /usr/local/sbin/startadsl
```

---

