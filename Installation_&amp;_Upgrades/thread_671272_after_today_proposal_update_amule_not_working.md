---
title: "after today proposal update amule not working"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by e_defranco on 2008-01-18
Hi, 

I have a strange problem: today I have applied the proposal package update (my last update, yesterday) and when all finished, amule crash with this error starting from a terminal:

Initialising aMule
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 405 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

The strange thing is that if I start amule from remote with xdmcp loggin as the same user (or every other user) all working fine !!!

I tried to uninstall amule and re-install but no positive effect ... not working from local console !!

My system is xubuntu 7.10 ..

Ideas ??

I don't know what package are updated (I know, is stupid, but I don't remember exactly what package  was proposed for update) .... maybe there are a tip to uninstall last package update ??

Thank in advance,

Emilio

---

### Post by PmDematagoda on 2008-01-18
The proposed update is not the problem, it is the Xorg security update causing the problem. The update is currently being worked on and a fix should be released for it soon which should fix your problems.

The problem with the Xorg update is that all Java applications malfunction, so you may have to use as many non-java applications as possible until the update is fixed.

---

### Post by AlanR8 on 2008-01-18
Similar here.


After the update VLC and Filezilla will not launch. Everything else SEEMS to be OK

---

### Post by e_defranco on 2008-01-18
mmmhhh .... ok, thank you for the fast reply and the info.

So, if I have correctly understand, there are "working in progess" about this topic ... but when the fix wille be ready, it will be automaticaly proposed by system update or is need that I will download it from a specific location ?

Thank again, 

emilio

---

### Post by oscarsfriend on 2008-01-18
The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Presumably someone will post there when everything is sorted.  Currently the offending files have been removed, and I presume the fix will show up as an update.  Failing that, you can always try downgrading as detailed here: [http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)

---

### Post by PmDematagoda on 2008-01-18
As to when the update is to be released, I cannot be sure, but it will be available as a normal update.

---

### Post by e_defranco on 2008-01-18
ok, thank you :-)

I have downgrade as you have suggested and after sudo /etc/init.d/gmd restart all working fine again.

Very, very well !!!

thank again,

emilio

---

