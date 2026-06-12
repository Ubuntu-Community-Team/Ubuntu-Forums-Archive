---
title: "NS2 installation in windows 7 using cygwin"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by yugesh on 2011-03-14
Hi i'm trying to install ns-allinone-2.29.2.tar in windows 7 by using cygwin installer..
At the starting i got this message
```

Cygwin detected
Note: Cygwin install is still considered EXPERIMENTAL

Checking Cygwin version is >= 1.3.12... 1.7.8 (should be ok)
Checking filesystems are mounted as UNIX filetype... yes
Checking default mode is binmode... yes
Checking legitimate login name... ok
Checking legitimate path name... ok
Checking for gcc... ok
Checking for gcc-g++... ok
Checking for gawk... ok
Checking for tar... ok
Checking for gzip... ok
Checking for make... ok
Checking for patch... ok
Checking for perl... ok
Checking for w32api... ok
Checking for diff... ok
Checking for X... None found!

Neither Package xorg-x11-base nor XFree86-base is present on your system.

Please install one of it using Cygwin's setup.exe
before trying to install the ns-2 distribution.

The above test indicates that your installation of Cygwin
is probably NOT SUITABLE for installing ns-2 allinone.
(More details can be found in the specific error message above.)

Do you wish to proceed regardless? [y/N]
```


After continuing i got error message


```
In file included from trace/trace.cc:42:
./sctp/sctp.h: At global scope:
./sctp/sctp.h:65: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:78: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:85: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:95: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:104: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:135: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:150: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:162: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:191: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:203: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:209: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:221: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:229: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:241: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:262: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:268: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:273: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:280: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:282: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:291: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:306: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:425: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:431: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:443: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:451: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:458: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:460: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:510: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:516: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:527: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:534: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:553: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:558: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:564: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:571: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:577: warning: `typedef' was ignored in this declaration
./sctp/sctp.h:705: error: extra qualification `SctpAgent::' on member `DumpSendB
uffer'
trace/trace.cc:185: warning: deprecated conversion from string constant to `char
*'
trace/trace.cc:185: warning: deprecated conversion from string constant to `char
*'
trace/trace.cc:185: warning: deprecated conversion from string constant to `char
*'
trace/trace.cc:185: warning: deprecated conversion from string constant to `char
*'
trace/trace.cc:185: warning: deprecated conversion from string constant to `char
*'
make: *** [trace/trace.o] Error 1
Ns make failed!
See http://www.isi.edu/nsnam/ns/ns-problems.html for problems
```

Anybody can help to install it properly..
Urgent..
Please help...

---

### Post by peacefullife on 2011-08-09
Hi, 
Please follow this link to install ns2 in Windows 7.
[http://www.ns2ultimate.com/post/441093095/ns-2-35-works-on-cygwin](http://www.ns2ultimate.com/post/441093095/ns-2-35-works-on-cygwin)

---

