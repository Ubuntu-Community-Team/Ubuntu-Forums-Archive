---
title: "Lotus notes 8.5.2 crashing"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by LnxLotus on 2010-09-25
Hi ,

As a newbie I installed Lotus notes 8.5.2 in my Ubuntu 10.4,the first time it worked fine ,but now I am having a serious issue where I open Lotus Notes and it crashes. I checked the logs from IBM_TECHNICAL_SUPPORT folder which is in my home folder \home\David\lotus\notes\data and the contents below: Dis anyone have the same issue?

-------------------------------------------------------------------
INFO: Generating binary list file ./nsd.David/nsd_Release_8.5.2_cache.ins.lst
INFO: Generating cache file ./nsd.David/nsd_Release_8.5.2_cache.ins
**ERROR 48: couldn't access shared memory key '0xf8474000' - (2) No such file or directory**
Script Version  : /opt/ibm/lotus/notes/nsd.sh 8.5.20.0203
Notes Version   : Release 8.5.2 August 04, 2010              (32-bit)
Notes Base      : 8.52
Data Dir        : /home/David/lotus/notes/data
Notes Exec Dir  : /opt/ibm/lotus/notes
Keyview Version : 10.8.0.0
Search Path     : /opt/ibm/lotus/notes /opt/ibm/lotus/notesapi
Library Path    : 
Debugger        : /usr/bin/gdb
Debugger Version: GDB
MEMCHECK Version: Memcheck Version: 8.5.20.0203
Script Dir      : /opt/ibm/lotus/notes
Host Info       : Linux David-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
User            : David (David)
Date            : Sat Sep 25 09:08:50 CST 2010
Last file mod   : Fri Jul 23 11:01:49 2010
Input arguments : -hang -wrapper


WARNING: You are not the owner of the running Notes processes
WARNING: notes_ps: No Notes processes seem to be running

<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>
Section: Notes Process Info (Sat Sep 25 09:08:50 CST 2010)
<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>

Searching for javacore under /home/David/lotus/notes/data/workspace/logs...
Please inspect the workspace/logs directory under your Lotus Notes data directory for possible jvm dump, heap dump, or system core files.
Sleeping for 15000 milliseconds

<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>
Section: Notes Process Info (Sat Sep 25 09:09:10 CST 2010)
<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>

Searching for javacore under /home/David/lotus/notes/data/workspace/logs...
Please inspect the workspace/logs directory under your Lotus Notes data directory for possible jvm dump, heap dump, or system core files.
delay value is 15000
repeat value is 2

<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>
Section: Summary (Sat Sep 25 09:09:15 CST 2010)
<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>


Note: 
	You can set the environment variable NSD_LOGDIR to point
	to the directory where you want your logs/cores to be
	automatically saved

Run /opt/ibm/lotus/notes/nsd.sh -help for more info on new options/features

Script started at: Sat Sep 25 09:08:47 CST 2010
Script ended   at: Sat Sep 25 09:09:15 CST 2010


Generated Info/Warnings/Errors: 
  (1) INFO: Generating binary list file ./nsd.David/nsd_Release_8.5.2_cache.ins.lst
  (2) INFO: Generating cache file ./nsd.David/nsd_Release_8.5.2_cache.ins
  (3) WARNING: You are not the owner of the running Notes processes
  (4) WARNING: notes_ps: No Notes processes seem to be running

---

### Post by tintamarre on 2010-11-09
Hello,

I've got the same issue here (Lotus Notes 8.5.2 on Ubuntu 10.10 x86):
```
ERROR (48): couldn't access shared memory key '0xf8c26000'
```

Did you manage to solve it ?

I had to go back to 8.5.1 ...

Martin

---

