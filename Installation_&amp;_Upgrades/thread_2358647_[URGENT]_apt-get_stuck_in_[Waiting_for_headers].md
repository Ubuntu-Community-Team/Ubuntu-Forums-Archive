---
title: "[URGENT] apt-get stuck in [Waiting for headers]"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by sed_faster on 2017-04-15
Hello folks,

I really need your help to fix this problem. When I tried update my ubuntu server:

```

Linux headlessgit 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:41 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

I received this error:

```

git@headlessgit:~$ sudo apt-get update
[sudo] password for git: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [247 kB]  
Get:3 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [237 kB]   
Get:4 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [105 kB]  
Get:5 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7428 B]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [7432 B]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2428 B]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [108 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [95.6 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [55.5 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [2748 B]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [2908 B]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [1232 B]
0% [Waiting for headers]          

```

And don't has anymore progress! How can fix this? 
Thanks

However I executed this commands:
```

git@headlessgit:~$ sudo rm -rf /var/lib/apt/lists/
lock     partial/ 
git@headlessgit:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for git: 
git@headlessgit:~$ sudo apt-get clean
git@headlessgit:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [247 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [237 kB]
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [105 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages [7428 B]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [7432 B]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted Translation-en [2428 B]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [108 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [95.6 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [55.5 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages [2748 B]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages [2908 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse Translation-en [1232 B]
0% [Waiting for headers]^C  

```

and...

```

git@headlessgit:~$ egrep -v '^(#|$)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
grep: /etc/apt/sources.list.d/*: No such file or directory

```

What can I do read from this results?
Thanks

---

### Post by robert.sherwood@gmail.com on 2017-04-16
When I have encountered that error, it is usually due to network connectivity issues. What is the output of "ping security.ubuntu.com"?

---

### Post by sed_faster on 2017-04-16
Hello, 

My network it was good! I resolve this error changed the source.list to origin eng or br, just like this:

```

git@headlessgit:~$ egrep -v '^(#|$)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://eng.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
grep: /etc/apt/sources.list.d/*: No such file or directory

```

Supposedly the sources with origins pt don't works well. Why this happen? My solutions it was the best solutions?

[UPDATE]
This domain don't exist. But the domain ubuntu.com exist! And I tested to did ping to this address!

Thanks

---

