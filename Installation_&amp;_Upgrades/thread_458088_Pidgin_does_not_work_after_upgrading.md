---
title: "Pidgin does not work after upgrading"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by madelman on 2007-05-29
I had Pidgin 2 working without problems in 6.06 then I upgraded to 6.10 and 7.04 and now it is not working and I get this message :

ssl support is needed for MSN accounts in pidgin

I had this problem with 6.06 while installing and it was fixed so I was able to install and use MSN accounts with SSL support. I just downloaded pidgin again and installed it and still gives me this error.

do you know what library is missing or why is not working in this version?

---

### Post by herald on 2007-05-31
Install libssl-dev.  It'll work then.

---

### Post by gizmoarena on 2007-06-19
installing libssl-dev didn't work :(

---

### Post by Marcelo Ramone on 2007-10-21
Yesterday i experienced a problem with Gaim: When i open the application, don't works because when the connection is complete, MANY windows appears and the desktop is FREEZE. 

I purge application, and reinstall, but the problem persist.

Today, i upgraded to 7.10, and the process was PERFECT, but the only issue is with Pidgin, the same issue persist (like gaim) I already purge Pidgin and reinstall but is not working...

Can anybody help me please?


Thanks in advance,
Marcelo.-

P.D: Sorry for my bad English, I speak Spanish.- :)

---

### Post by Sef on 2007-10-21
> I had this problem with 6.06 while installing and it was fixed so I was able to install and use MSN accounts with SSL support. I just downloaded pidgin again and installed it and still gives me this error.

Do you download Pidgeon from Pidgeon's website, or use what comes installed with Ubuntu?

> P.D: Sorry for my bad English, I speak Spanish.- 

Your English is fine.  I can understand it.

---

### Post by Marcelo Ramone on 2007-11-10
[B]Using the pidgin that includes Ubuntu 7.10 and I can not even use it. I uninstalled and purged  the application and after make a "sudo locale pidgin" and  removed all pidgin data in the system. 

But when I re-install and open Pidgin begin to open hundreds of the application windows in the taskbar and hangs all around. 

 What's going on? 

Do I have no way to re-use this program?

Thanks in advance,
Marcelo Ramone.-
[/B]

---

### Post by potentia on 2007-11-11
[http://ubuntuforums.org/archive/index.php/t-436651.html](http://ubuntuforums.org/archive/index.php/t-436651.html)

The essence:

In a couple of Really Easy Steps:

Open Synaptic Package Manager, search for and install 'libgnutls-dev'

When you run ./configure to build Pidgin, do './configure --enable-gnutls=yes', 

do sudo make install (as normal) to finish.

---

### Post by shadowboxer_k on 2007-12-21
hi,

i have the same problem with pidgin. i followed your directions, installed the libraries, but when i get to the ./configure command i get an error. what am i doing wrong?

thanks!

---

