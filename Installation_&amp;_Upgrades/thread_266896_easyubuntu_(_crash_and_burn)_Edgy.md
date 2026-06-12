---
title: "easyubuntu ( crash and burn) Edgy"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by zpro on 2006-09-27
Well, thought I would try to install this cool app,
NOPE, can someone tell me how to fix it?

Here is the output:

--22:28:57--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
           => `easyubuntu-3.023.tar.gz'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92,653 (90K) [application/x-tar]

100%[======================================================================>] 92,653        99.75K/s

22:28:58 (99.54 KB/s) - `easyubuntu-3.023.tar.gz' saved [92653/92653]

rick@64bit:~$ tar -zxf easyubuntu-3.023.tar.gz
rick@64bit:~$ cd easyubuntu
rick@64bit:~/easyubuntu$ sudo python easyubuntu.in
Password:
System sanity check: PASSED!
amd64 detected
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "easyubuntu.in", line 51, in ?
    main()
  File "easyubuntu.in", line 48, in main
    qtfrontend.launcher(datadir, confdir)
  File "/home/rick/easyubuntu/EasyUbuntu/qtfrontend.py", line 172, in launcher
    pkglist = minidom.parse(os.path.join(datadir, 'packagelist-%s.xml' % codename()))
  File "xml/dom/minidom.py", line 1915, in parse
  File "xml/dom/expatbuilder.py", line 922, in parse
IOError: [Errno 2] No such file or directory: './packagelist-edgy.xml'
rick@64bit:~/easyubuntu$ cd ..
rick@64bit:~$   
---------------------------------------------
it looks like it does not like edgy,
can I just delete the folder easyubuntu?
and/or is there a special version for edgy?

Thanks -
:(

---

### Post by x64Jimbo on 2006-09-28
Yep, that'll happen. Easyubuntu is not made for Edgy - it specifically says Breezy/Dapper on their site. [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)
Fixing it will be out of my league, but I can tell you that installing apps on a system they're not designed for is a bad idea.

---

### Post by zpro on 2006-09-28
So, can I remove the folder easyubuntu ?
without fear ?

Thanks-
I'll wait for the edgy version.
:-D

---

### Post by itchanddino on 2006-09-28
Yep, just get rid of it.

---

