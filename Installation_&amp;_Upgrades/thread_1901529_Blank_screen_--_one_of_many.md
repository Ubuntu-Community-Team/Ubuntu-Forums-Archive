---
title: "Blank screen -- one of many"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by jgauthier on 2011-12-28
Wow, so it looks like many people have a blank screen after upgrading to 11.10.  Well, me too. My scenario seems to be a little different, but I have two system that I upgraded in tandem with the same results.

First, I opted to use GDM one both systems when given the choice.
However, it looks like GDM seg faults on startup.

Dec 28 16:18:26 jgauthier-bedroom kernel: [  114.610916] unity-greeter[3020]: segfault at 0 ip 00007f6114b25b70 sp 00007fff80904888 error 4 in libgio-2.0.so.0.3000.0[7f6114a8c000+13b000]
Dec 28 17:47:53 jgauthier-bedroom kernel: [ 5481.293962] gdm-simple-slav[3442]: segfault at 0 ip 00007fad80a6a1e5 sp 00007fff6f5512b0 error 4 in libnss_compat-2.13.so[7fad80a66000+8000]

There is a bug for this out there.  Okay, so what. I reconfigure the machines to use lightdm instead:

dpkg-reconfigure gdm


However, nothing happens when I start it.
If I run X manually:

X -verbose
I do not get any errors at all.  It looks like it is working fine! However, nothing on the screen.

If I run startx, I get a desktop.

So, what is going on that I cannot get this to work with lightdm?

Thanks!

---

### Post by jgauthier on 2011-12-28
So, it looks like unity-greeter is segfaulting as well... With lightdm.

Dec 28 18:29:53 jgauthier-bedroom kernel: [ 2059.298650] unity-greeter[3908]: segfault at 0 ip 00007f403334cb70 sp 00007fff9b64c5a8 error 4 in libgio-2.0.so.0.3000.0[7f40332b3000+13b000]


So, I currently have two unusable desktops.  Guh.  Is there a solution?

---

