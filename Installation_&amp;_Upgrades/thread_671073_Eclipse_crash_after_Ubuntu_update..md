---
title: "Eclipse crash after Ubuntu update."
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by ksmster on 2008-01-18
Hi.
After today Ubuntu 7.10, Gutsy Gibbon update my Eclipse(3.3) will crash with: 


The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 805 error_code 11 request_code 145 minor_code 5)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

I try to reinstall Eclipse but the result is same.


Can you help me?

---

### Post by kellemes on 2008-01-18
Have you tried **un**installing it first?
```

apt-get remove --purge eclipse

```

---

### Post by GolanTrevize on 2008-01-18
--purge eclipse won't lead anywhere in this case. 

It's not an eclipse-only question but hits many java-applications

see [http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)

it is necessary to backgrade the xserver

regards

---

### Post by mscherzer on 2008-01-18
Hi,
To get eclipse working follow the instructions in this thread.

[http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)

cheers

Marcel

---

### Post by oneiota on 2008-01-18
Same here.  I installed an eclipse plugin today and it worked initially.  Later I rebooted and now Eclipse crashes as soon as I start it:

[INDENT]The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 433 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/INDENT]


Can anyone who has tried the downgrade of xserver-xorg-core, confirm this solved the problem?

---

### Post by GolanTrevize on 2008-01-18
confirmed: yes this will solve the problem

everythings running smooth again

---

### Post by oneiota on 2008-01-18
Thanks very much.

The downgrade plus a restart of Ubuntu solved the problem for me too!

---

### Post by Lord Illidan on 2008-01-18
Thanks, my friend was having this issue too. I don't know how packages like this make their way to the repos..clearly testing is not good.

---

