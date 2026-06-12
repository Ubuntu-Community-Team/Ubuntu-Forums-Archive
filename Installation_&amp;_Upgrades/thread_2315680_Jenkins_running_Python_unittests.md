---
title: "Jenkins running Python unittests"
date: 2016-03-01
forum: Installation &amp; Upgrades
---

### Post by Matthew_H._Wagner on 2016-03-01
I am attempting to use Jenkins to run our Python unittests on Ubuntu 14.04.  I've run into a file permission problem and being new to Linux admin, would like to know the best practice for solving this problem.

Python 2.7 is installed by default as shown:
```
gups@gups-xxxxxxxxxx:~$ ls -la /usr/lib | grep python
-rw-r--r--   1 root root        68232 Jan 16 20:42 libqgispython.so.2.8.6
drwxrwxr--  26 root root        12288 Feb 12 08:03 python2.7
drwxr-xr-x   3 root root         4096 Feb 23  2014 python3
drwxr-xr-x  33 root root        20480 Feb  4 05:16 python3.4
```

My users then by default do not have access to Python.  I can add my login user 'gups' and the Jenkins system account 'jenkins' to the root group, but I would rather not use the nuclear option.  What is a better, safer alternative?

Do I install another copy of Python in /usr/local/lib?  Do I change the group owner of /usr/lib/python2.7 to something else and all users to that group?

EDIT:
I've been looking into using [virtualenv]("https://pypi.python.org/pypi/virtualenv") which seems like a nice solution.  I ran virtualenv to create an environment in my jenkins user's home directory, but it does not include /var/lib/python2.7/dist-packages.  This is a problem.

---

