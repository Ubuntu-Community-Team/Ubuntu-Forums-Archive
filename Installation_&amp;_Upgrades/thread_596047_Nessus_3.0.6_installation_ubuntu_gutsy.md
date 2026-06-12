---
title: "Nessus 3.0.6 installation ubuntu gutsy"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by McFranco on 2007-10-29
Hello everybody,

I want to install nessus 3.0.6 under Ubuntu gutsy (7.10), but it fails.
Nessus 3.0.6 ran perfect under Ubuntu 7.04.

There comes an error message up, when I use the Packet installer:
Error: Dependency is not satfisfiable: libssl0.9.7

I've installed the current version of libssl: libssl0.9.8

Do anybody have the same problem, or is there a way to install Nessus 3.0.6 on Ubuntu Gutsy?

Thanks for any help!

McFrank

---

### Post by freesnowcone on 2007-10-30
I am also having the same problem.  I have the libssl0.9.8 package installed however when I try to install Nessus 3.0.6 it gives me the same error message as McFranco.

Error: Dependency is not satfisfiable: libssl0.9.7

I think we could both use some help.  Please help!

---

### Post by ruggersway on 2007-11-01
I experienced the same result as both of you.  While I can't speak to the correctness of this solution, perhaps someone with more knowledge can explain the possibility of conflicts if there are any, the following has worked for me.  And as yet, I've seen no ill effects.

Download libssl for 7.04
[http://mirrors.kernel.org/ubuntu/pool/universe/o/openssl097/libssl0.9.7_0.9.7k-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/o/openssl097/libssl0.9.7_0.9.7k-3_i386.deb)

$ sudo dpkg -i libssl0.9.7_0.9.7k-3_i386.deb

Download 3.0.6 from Nessus and install.

Register and update
$ sudo /opt/nessus/bin/nessus-fetch --register your-code-here-xxxx-xxxx

Create SSL cert (I don't remember having to do this in the past but nessus complained when I tried to start it so I went with it)
$ sudo /opt/nessus/sbin/nessus-mkcert

Start Nessus
$ sudo /opt/nessus/sbin/nessusd start

Install optional Nessus Client for gui interface if you want...


...hope that helps.

---

### Post by McFranco on 2007-11-04
Hi ruggersway!

This works!
Thanks a lot.

McFranco

---

### Post by eastpole on 2008-02-19
[QUOTE=ruggersway;3685471]I experienced the same result as both of you.  While I can't speak to the correctness of this solution, perhaps someone with more knowledge can explain the possibility of conflicts if there are any, the following has worked for me.  And as yet, I've seen no ill effects.

Download libssl for 7.04
[http://mirrors.kernel.org/ubuntu/pool/universe/o/openssl097/libssl0.9.7_0.9.7k-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/o/openssl097/libssl0.9.7_0.9.7k-3_i386.deb)

$ sudo dpkg -i libssl0.9.7_0.9.7k-3_i386.deb


Awesome -- thanks ruggersway. This solution also appears to help those who wanted to install the ancient and beautiful email program pine from a .deb provided by U Washington.

For their googling pleasure, I say: pine_4.64_i386.deb

 I'll touch base if I see a serious downside to installing libssl 0.9.7.  

eastpole

---

