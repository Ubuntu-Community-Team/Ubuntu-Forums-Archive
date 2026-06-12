---
title: "How to access onedrive in ubuntu 16.10"
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-11-25
just like it says, google only references earlier versions.

Henry

---

### Post by vasa1 on 2016-11-25
Via your browser?

---

### Post by Hewjr100 on 2016-11-25
Yes I do that, but I want to sycn files from ubuntu.  Currently when I down load files to save, I save them in onedirve folder from ubuntu.  But they don't sync until I boot up windows 10.  Really I use ubuntu all the time, once a week, usually tuesday I boot windows and run updates, then reboot to ubuntu.  But I am boooting windows every day in order to sycn files I created, or dowloaded.

Henry

PS I see in google talk about one-D

---

### Post by howefield on 2016-11-25
> **Hewjr100 said:**
> ...I see in google talk about one-D

That project is dead as far as I am aware, but the fork "*onedrive*" looks a bit more promising.

[https://github.com/skilion/onedrive](https://github.com/skilion/onedrive)

There is not, as you are probably aware, an officially supported Linux client.

---

### Post by Hewjr100 on 2016-11-25
Ok Thanks for your help.  Did not no about other client.

Henry

---

### Post by Hewjr100 on 2016-11-25
Alright I installed dmd as directed, then ran make install and got the following error message:

```
henry@wyatt:~/Downloads/onedrive-1.0$ ls -a
.  ..  .gitignore  INSTALL.md  LICENSE  Makefile  onedrive.conf  onedrive.o  patch  README.md  src
henry@wyatt:~/Downloads/onedrive-1.0$ sudo make install
dmd -O -release -inline -boundscheck=off -ofonedrive -L-lcurl -L-lsqlite3 -L-ldl patch/etc_c_curl.d patch/std_net_curl.d src/config.d src/itemdb.d src/main.d src/monitor.d src/onedrive.d src/sqlite.d src/sync.d src/util.d
patch/std_net_curl.d(295): Deprecation: Implicit string concatenation is deprecated, use "\x0d\x0a" ~ "\x0d\x0a" instead
patch/std_net_curl.d(4047): Deprecation: module core.stdc.string is not accessible here, perhaps add 'static import core.stdc.string;'
/usr/bin/ld: cannot find -lcurl
/usr/bin/ld: cannot find -lsqlite3
collect2: error: ld returned 1 exit status
Error: linker exited with status 1
Makefile:19: recipe for target 'onedrive' failed
make: *** [onedrive] Error 1
henry@wyatt:~/Downloads/onedrive-1.0$
```

---

### Post by howefield on 2016-11-25
There are dependencies which you need to satisfy...

```
/usr/bin/ld: cannot find -lcurl
/usr/bin/ld: cannot find -lsqlite3
```

---

### Post by Hewjr100 on 2016-11-25
Tried to install -lcurl got the following:

```
henry@wyatt:~/Downloads/onedrive-1.0$ sudo apt install -lcurl
E: Command line option 'l' [from -lcurl] is not understood in combination with the other options.
henry@wyatt:~/Downloads/onedrive-1.0$ 
```

Same thing with -lsqlite:

```
henry@wyatt:~/Downloads/onedrive-1.0$ sudo apt install -lsqlite3
[sudo] password for henry:          
E: Command line option 'l' [from -lsqlite3] is not understood in combination with the other options.
henry@wyatt:~/Downloads/onedrive-1.0$
```

Henry

---

### Post by howefield on 2016-11-25
Those aren't the package names required.

I'm not sure what ones you need but they aren't named -lcurl and -lsqlite3. The git page holding the onedrive code might have some information on it.

I'm currently having a look at rclone.. lot easier to get going but possibly more "manual" to use.

---

### Post by Hewjr100 on 2016-11-25
Thanks howfield. I guess I'll wait for something better (gui) based.

Henry

---

### Post by Hewjr100 on 2016-11-25
Btw see my new signature!  Yes, after 26 years of windows I quit.  After I started this post I went and did a clean install of ubuntu 16.10 and kissed windows goobye.

Henry

---

### Post by oldos2er on 2016-11-25
The dependencies and how to install them are listed in the README.md file.

---

### Post by Hewjr100 on 2016-11-25
I will give it a shot.

Henry

---

### Post by howefield on 2016-11-26
> **Hewjr100 said:**
> Thanks howfield. I guess I'll wait for something better (gui) based.

Sure, a gui can make things a little easier but I have to say rclone is pretty decent and learning a few commands is all you need.

It can also sync to and from multiple "cloud" solutions.

---

