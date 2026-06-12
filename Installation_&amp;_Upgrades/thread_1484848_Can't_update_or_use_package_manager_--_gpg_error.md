---
title: "Can't update or use package manager -- gpg error"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by i2000s on 2010-05-16
Code:

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release: Unknown error executing gpgv


Along with the standard messages, apt-get displayed

Code:

gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC


This occurs on using the update manager, package manager, apt-get update, etc. Any ideas? I've tried deleting the cached files, changing my server, checking that my date & time are correct (signing can be time sensitive), updating gpg (it was already at the latest), and maybe some other things I've forgotten.

System: Ubuntu Lucid

---

### Post by i2000s on 2010-05-16
someone said there is something wrong with the libreadline6.
any other solutions?

---

### Post by efittery on 2010-07-02
I have the same problem.  I found the following:

The problem wasn't gpg after all, but libreadline6. Updating it didn't help, but building it manually (md5: a3a5bf025a1b8df869f45f34098ffc6a rather than 2569b5ed629a3e573b0a8f9ec23a37ff) and copying my version to /usr/local/lib/libreadline.so.6 worked!

I would hope a better solution than this exists.

---

### Post by efittery on 2010-07-02
I also found a page that talked about the problem of libreadline.so.6 causing the error:

'readline-6.0' causes "undefined symbol: PC" errors

The web page is located at:

[http://trac.sagemath.org/sage_trac/ticket/7610](http://trac.sagemath.org/sage_trac/ticket/7610)


I downloaded the readline-6.0.p1.spkg which I believe is a patch file that is supposed to fix this problem.

I am not familiar with .spkg files, so I will leave it to somebody else who is to figure out how to use it.

Please post your results.

---

### Post by samicom on 2010-08-31
I fought this problem from synaptic on down to gpg, only to find it was readline all along. My solution was somewhat simpler than building or patching. 

in terminal: 
[SIZE="4"]
ls /usr/local/lib
[/SIZE]
there was a bunch of readline libs in there (libreadline.so.BLAH-BLAH) so i: 

[SIZE="4"]su
mkdir temp
mv /usr/local/lib/libreadline* temp
ldconfig 
apt-get update[/SIZE]

and voila. went without a hitch. then i deleted my temporary directory (rm -rf /usr/local/lib/temp), exited su. 

 ~2 hours fighting to no avail, and for it work with a few seconds of commands... 
I'm not complaining, but it does seem somewhat of a cruel irony.

---

### Post by rdangelojp7 on 2011-02-06
Oh my God! it worked, I can't believe this. Me and most likely many others can't thank you enough!
But don't you need the libreadline files because of dependencies or in any other way (before I delete them)?

---

### Post by wari on 2011-03-14
:O Great!! I had the same error when upgrading from Jaunty, now it seems working :D

---

### Post by nimeis on 2011-06-01
Wow, it really was THAT simple!. Nice work Semicom.

---

### Post by marley07 on 2011-07-15
Hey can we move this to solved?

Thank you SO much for the answer!

---

### Post by robde on 2011-12-16
Many thanks for this, worked for me too!

---

### Post by The Altruist on 2012-03-14
This is an old thread, but I feel it's worth a necro after I found the information I needed.
samicom is dead on, and I'll tell you why.

libreadline.so.6.* is supposed to be in /lib, not /usr/local/lib.
I'd compiled libreadline from the raw source( ./configure && make && sudo make install ). Apparently, this was a bad idea. (It worked OK in MinGW/MSYS.)

I figured I could grab a new copy from the PPA. Seemed like a good idea, but do-release-upgrade still failed.

After some digging I found I still had multiple versions of libreadline running around.

Ubuntu stores libreadline into /lib, but the source compile went to /usr/local/lib/. I killed the source compile copy, and re-ran do-release-upgrade. Success.

---

### Post by meanmrmustard on 2012-05-24
I just began getting this error with my Natty install.
Worked like a charm.
Thanks a million!

---

### Post by oldos2er on 2012-05-24
Old thread closed.

---

