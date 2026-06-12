---
title: "saslpasswd2 crashes (core dumped)"
date: 2009-02-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hurenkam on 2009-02-04
While trying out Jaunty (initial install with alpha 3), I wanted to install postfix with sasl authentication. So I followed the tutorial here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) and got it mostly running, however sending mail with sasl authentication still didn't work.
Browsing the internet, someone suggested to use saslpasswd2 to set the password for the user, so I gave that a try:

root@jaunty:~# saslpasswd2 -c hurenkam
Password: 
Again (for verification): 
Segmentation fault (core dumped)

Now there may be a something still wrong with my configuration, but saslpasswd2 segfaulting is something I had not expected.

dmesg shows the following:
[ 9467.832422] saslpasswd2[20361]: segfault at 0 ip 0000000000000000 sp 00007fff70889c28 error 14 in saslpasswd2[400000+3000]
[11568.376959] saslpasswd2[21306]: segfault at 0 ip 0000000000000000 sp 00007fffeda8be28 error 14 in saslpasswd2[400000+3000]

root@jaunty:~# saslpasswd2 -v

This product includes software developed by Computing Services
at Carnegie Mellon University ([http://www.cmu.edu/computing/](http://www.cmu.edu/computing/)).

Built against SASL API version 2.1.22
LibSasl version 2.1.22 by "Cyrus SASL"


Hope you can do something with this info, let me know if you need more.

Any hints/tips how to solve/work around this problem, are very much appreciated.

Warm regards,
Mark.

---

### Post by hurenkam on 2009-02-04
Ok, figured out what was wrong with my config, saslauthd was not creating the socket in the chroot dir. Got my mail working now with sasl, and don't seem to need saslpasswd2 (which still segfaults btw...)

---

