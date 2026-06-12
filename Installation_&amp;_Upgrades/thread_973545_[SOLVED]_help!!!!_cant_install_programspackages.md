---
title: "[SOLVED] help!!!! cant install programs/packages"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by chrismarsh1987 on 2008-11-06
Thumbs down  error code 1 trouble, please help
so im trying to get past the error codes in my previous post, and trying to get pcakages and programs and im getting the following

administrator@andromeda:~$ sudo apt-get install autoconf
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
automake autotools-dev m4
Suggested packages:
autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc libtool
gettext
The following NEW packages will be installed
autoconf automake autotools-dev m4
0 upgraded, 4 newly installed, 0 to remove and 31 not upgraded.
Need to get 0B/1248kB of archives.
After this operation, 4153kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/m4_1.4.11-1_i386.deb (--unpack):
failed in buffer_read(fd): files list for package `python-dbus': Input/output error
Errors were encountered while processing:
/var/cache/apt/archives/m4_1.4.11-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

if someone can look back on my other thread, and help me out with either of these, please help me, im on msn if that would be easier as i am a total newbie to this and have no idea what im really doing and step by step help would be highly appreciated

thanks people. other than the complexity of it all...UBUNTU ROCKS!!!!

oh and running ubuntu 8.10 on imb thinkpad t23 (covered in other thread

---

### Post by pytheas22 on 2008-11-06
Because it's complaining about 'input/output errors', I wonder if one of the cached package files that you downloaded got corrupted somehow.  If so, it may help to clear your packages cache:
```

sudo rm -rf /var/cache/archives
sudo mkdir /var/cache/archives
```

Then try installing your package again using:
```

sudo apt-get update
sudo apt-get install autoconf
```


[Note that I am telling you to run 'sudo rm -rf', which in certain situations can be very destructive, but I promise that I'm not being malicious.  If you would like me to explain specifically what those commands do before you run them, let me know.]

---

### Post by chrismarsh1987 on 2008-11-10
> **pytheas22 said:**
> Because it's complaining about 'input/output errors', I wonder if one of the cached package files that you downloaded got corrupted somehow.  If so, it may help to clear your packages cache:
```

sudo rm -rf /var/cache/archives
sudo mkdir /var/cache/archives
```

Then try installing your package again using:
```

sudo apt-get update
sudo apt-get install autoconf
```


[Note that I am telling you to run 'sudo rm -rf', which in certain situations can be very destructive, but I promise that I'm not being malicious.  If you would like me to explain specifically what those commands do before you run them, let me know.]



Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  automake autotools-dev m4
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc libtool
  gettext
The following NEW packages will be installed
  autoconf automake autotools-dev m4
0 upgraded, 4 newly installed, 0 to remove and 61 not upgraded.
Need to get 0B/1248kB of archives.
After this operation, 4153kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/m4_1.4.11-1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `python-dbus': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/m4_1.4.11-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@andromeda:/var/cache/apt/archives# 


 is what happened

not really much closer to fixing any of the issues i seem to have with this operating system. thanks for the attempt tho

---

### Post by pytheas22 on 2008-11-10
I saw while researching your problem that you've posted a question here about it as well.  I would try running those commands suggested by Arnaudus.  If they don't help, please let us know.

The other possibility here is that the problem is caused by hard-disk failure or file-system corruption--which would explain the bits about input/output errors.  Are you experiencing any other weird problems with your system?  If possible, make sure BIOS is running checks on your hard drive to detect failure when the system boots (this usually involves enabling 'S.M.A.R.T' in BIOS).  Is it an old drive?

---

### Post by chrismarsh1987 on 2008-11-10
> **pytheas22 said:**
> I saw while researching your problem that you've posted a question here about it as well.  I would try running those commands suggested by Arnaudus.  If they don't help, please let us know.

The other possibility here is that the problem is caused by hard-disk failure or file-system corruption--which would explain the bits about input/output errors.  Are you experiencing any other weird problems with your system?  If possible, make sure BIOS is running checks on your hard drive to detect failure when the system boots (this usually involves enabling 'S.M.A.R.T' in BIOS).  Is it an old drive?

unusual symptoms on all installations, audio codecs, packages, updates and upgrades, plugins ect have tried commands, null fixes. problem persists

---

### Post by chrismarsh1987 on 2008-11-11
> **pytheas22 said:**
> I saw while researching your problem that you've posted a question here about it as well.  I would try running those commands suggested by Arnaudus.  If they don't help, please let us know.

The other possibility here is that the problem is caused by hard-disk failure or file-system corruption--which would explain the bits about input/output errors.  Are you experiencing any other weird problems with your system?  If possible, make sure BIOS is running checks on your hard drive to detect failure when the system boots (this usually involves enabling 'S.M.A.R.T' in BIOS).  Is it an old drive?



arnaudus's commands did not imporve situation, problem persists, thanks arnaudus, good try.

---

### Post by pytheas22 on 2008-11-11
Sorry this is still not solved and for not replying faster.  Please post the output of:
```

cat /var/lib/dpkg/info/python-dbus.list
ls /var/cache/apt/archives
```

---

### Post by chrismarsh1987 on 2008-11-12
> **pytheas22 said:**
> Sorry this is still not solved and for not replying faster.  Please post the output of:
```

cat /var/lib/dpkg/info/python-dbus.list
ls /var/cache/apt/archives
```


hey no problem heres the data you require

administrator@andromeda:~$ cat /var/lib/dpkg/info/python-dbus.list
drwxr-xr-x root/root         0 2008-06-12 16:55 ./
drwxr-xr-x root/root         0 2008-06-12 16:54 ./usr/
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/lib/
drwxr-xr-x root/root         0 2008-06-12 16:54 ./usr/lib/pkgconfig/
-rw-r--r-- root/root       282 2008-06-12 16:54 ./usr/lib/pkgconfig/dbus-python.pc
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/lib/python-support/
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/python2.5/
-rw-r--r-- root/root     10120 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/python2.5/_dbus_glib_bindings.so
-rw-r--r-- root/root    120752 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/python2.5/_dbus_bindings.so
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/python2.4/
-rw-r--r-- root/root     10120 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/python2.4/_dbus_glib_bindings.so
-rw-r--r-- root/root    120720 2008-06-12 16:55 ./usr/lib/python-support/python-dbus/python2.4/_dbus_bindings.so
drwxr-xr-x root/root         0 2008-06-12 16:54 ./usr/include/
drwxr-xr-x root/root         0 2008-06-12 16:54 ./usr/include/dbus-1.0/
drwxr-xr-x root/root         0 2008-06-12 16:54 ./usr/include/dbus-1.0/dbus/
-rw-r--r-- root/root      3571 2008-06-12 16:54 ./usr/include/dbus-1.0/dbus/dbus-python.h
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/share/
drwxr-xr-x root/root         0 2008-06-12 16:54 ./usr/share/doc/
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/share/doc/python-dbus/
-rw-r--r-- root/root      1076 2007-08-01 21:38 ./usr/share/doc/python-dbus/README
-rw-r--r-- root/root      1568 2008-06-12 16:53 ./usr/share/doc/python-dbus/copyright
-rw-r--r-- root/root     74247 2007-12-10 15:14 ./usr/share/doc/python-dbus/changelog.gz
-rw-r--r-- root/root      5407 2007-12-10 15:09 ./usr/share/doc/python-dbus/NEWS.gz
-rw-r--r-- root/root     11377 2008-06-12 16:53 ./usr/share/doc/python-dbus/changelog.Debian.gz
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/share/python-support/
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/share/python-support/python-dbus/
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/share/python-support/python-dbus/dbus/
-rw-r--r-- root/root      1622 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/lowlevel.py
-rw-r--r-- root/root       488 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/types.py
-rw-r--r-- root/root       109 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/_version.py
-rw-r--r-- root/root      1795 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/glib.py
-rw-r--r-- root/root      4200 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/__init__.py
drwxr-xr-x root/root         0 2008-06-12 16:55 ./usr/share/python-support/python-dbus/dbus/mainloop/
-rw-r--r-- root/root      1773 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/mainloop/glib.py
-rw-r--r-- root/root      2336 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/mainloop/__init__.py
-rw-r--r-- root/root     17995 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/bus.py
-rw-r--r-- root/root      9580 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/_dbus.py
-rw-r--r-- root/root      1150 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/dbus_bindings.py
-rw-r--r-- root/root     14670 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/decorators.py
-rw-r--r-- root/root     24550 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/proxies.py
-rw-r--r-- root/root     34946 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/service.py
-rw-r--r-- root/root      3164 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/gobject_service.py
-rw-r--r-- root/root     26114 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/connection.py
-rw-r--r-- root/root      3164 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/exceptions.py
-rw-r--r-- root/root      3386 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus/_expat_introspect_parser.py
-rw-r--r-- root/root        33 2008-06-12 16:54 ./usr/share/python-support/python-dbus/dbus_bindings.py
administrator@andromeda:~$ ls /var/cache/apt/archives

been making very slow progress with installing apckages manualy afer downloading them and moving them into the archive

---

### Post by pytheas22 on 2008-11-12
That information unfortunately didn't provide the clue I was hoping for--your python-dbus package doesn't seem to be corrupted in any way.  But it is strange that your /var/cache/apt/archives directory is empty.  Did you empty it on purpose?

Also, what have you been doing regarding manually downloading packages and moving them into the archive?  How were you installing them after you manually downloaded them?  If you did something strange, that could have been what broke the package manager.

---

### Post by chrismarsh1987 on 2008-11-13
> **pytheas22 said:**
> That information unfortunately didn't provide the clue I was hoping for--your python-dbus package doesn't seem to be corrupted in any way.  But it is strange that your /var/cache/apt/archives directory is empty.  Did you empty it on purpose?

Also, what have you been doing regarding manually downloading packages and moving them into the archive?  How were you installing them after you manually downloaded them?  If you did something strange, that could have been what broke the package manager.



actually it was that wich got the pythos bus running and about 6 other packages, but thers still 61 to go. i'll drop back later with the little manual i got on what im doing.

---

### Post by triva911 on 2010-08-06
[COLOR=#000000]I  had a similar problem, I could not install it, I constantly had the  same error "sudo: / etc / sudoers is owned by uid 1000, should be 0
[/COLOR]sudo: sudoers no valid sources found, quitting "and I eventually managed to fix it ..
Here's how:

Run Terminal and login as root typing
su
password

and finally type this to fix it
chown root:root /etc/sudoers

---

