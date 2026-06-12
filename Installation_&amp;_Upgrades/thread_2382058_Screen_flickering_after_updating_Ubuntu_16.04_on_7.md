---
title: "Screen flickering after updating Ubuntu 16.04 on 7th January 2018"
date: 2018-01-08
forum: Installation &amp; Upgrades
---

### Post by priyesh17 on 2018-01-08
After automatic update asked me to update my softwares and I said Yes, I am observing screen flicker whenever I change a Tab or Window. The screen flickers for a second and flickering mostly gets triggered when I use ALT+TAB way to navigate.

My System is:
Processor: Intel® Core&#8482; i3 CPU M 370 @ 2.40GHz × 4 
Graphics: Intel® Ironlake Mobile
Memory: 3.7 G
Dell Vostro

I debugged it and found a log file **apport.log **with following message.
```

[I]ERROR: apport (pid 8949) Tue Jan  9 22:53:24 2018: this executable already crashed 2 times, ignoring
ERROR: apport (pid 8973) Tue Jan  9 22:53:28 2018: called for pid 8963, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 8973) Tue Jan  9 22:53:28 2018: executable: /usr/bin/compiz (command line "compiz")
ERROR: apport (pid 8973) Tue Jan  9 22:53:28 2018: debug: session gdbus call: (true,)

ERROR: apport (pid 8973) Tue Jan  9 22:53:28 2018: this executable already crashed 2 times, ignoring
ERROR: apport (pid 9007) Tue Jan  9 22:53:42 2018: called for pid 8985, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 9007) Tue Jan  9 22:53:42 2018: executable: /usr/bin/compiz (command line "compiz")
ERROR: apport (pid 9007) Tue Jan  9 22:53:42 2018: debug: session gdbus call: (true,)
```

Also, **syslog** contains following information.
```

Jan 10 10:29:00 priyesh-Vostro-1440 kernel: [12565.901525] compiz[9021]: segfault at 0 ip 00007f6813af5eb6 sp 00007ffea722b2f0 error 4 in i965_dri.so[7f6813513000+82d000]
Jan 10 10:29:29 priyesh-Vostro-1440 kernel: [12595.795843] compiz[10691]: segfault at 0 ip 00007f7d536deeb6 sp 00007fff1d399410 error 4 in i965_dri.so[7f7d530fc000+82d000]
Jan 10 10:29:34 priyesh-Vostro-1440 kernel: [12599.919900] compiz[10725]: segfault at 0 ip 00007fa003af5eb6 sp 00007ffc9a2f9cb0 error 4 in i965_dri.so[7fa003513000+82d000]
```


[/I]Looks like, **compiz** process is crashing and as a result, when I try to toggle between windows I see screen flicker.

How can I solve this issue. It happened after the recent update on 7th January.

Any help is most appreciated.

---

### Post by RobGoss on 2018-01-09
I am also experiencing screen flickering using 16.04 it's been like that for some time, mine happens at start but they I don't see it until I restart the system

---

### Post by Absque_Nomine on 2018-01-17
OP, may wish to read this...
[https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-updates-2018-01-04-compiz-segfaults](https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-updates-2018-01-04-compiz-segfaults)

---

### Post by decemberpei on 2018-05-31
similar issue here. solved by rolling back kernel , now on 4.10.0-041000-generic and the issue is gone. Hope this helps!

---

### Post by larry2311 on 2018-06-26
I have see this issue as well on all kernels on Ubuntu 16.04, with sections of the screen flickering. On the Lenovo X200 laptop this is resolved by one mouse click in the flickering area.  Going to try 18.04 soon and see if that eliminates it with newer graphics subsystem.

---

