---
title: "Running wxdownload fast"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by duongthaiha on 2007-06-25
Hi 
I am trying to run the wxdowload fast however when i tried to run it it show me the error

root@duongthaiha-desktop:/home/duongthaiha/Desktop# wxdfast 
wxdfast: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory

Can you please tell me what should i do in these case? Thanks a lot in advance.  I am quite new to Linux to please forgive me if the question is not appropriate.

Kind regards

---

### Post by jboehm on 2007-07-02
I'm having the same problem so I'll bump your message -- Jon

---

### Post by masiver on 2007-07-12
Same problem.
Try:

sudo aptitude install libwxgtk2.6-0

aptitude will manage dependencies.
Then reinstall wxdfast.
:)

---

### Post by sergiodlc on 2007-10-16
The solution is here: [http://forum.digital-digest.com/archive/index.php/t-81066.html](http://forum.digital-digest.com/archive/index.php/t-81066.html) though it seems that you have to install the wxWidgets packages. Run Synaptic, search for wx and install wx-common, libwxbase2.6 and libwxgtk2.6 as well as the dev packages.

Hope this helps

Sergio

---

