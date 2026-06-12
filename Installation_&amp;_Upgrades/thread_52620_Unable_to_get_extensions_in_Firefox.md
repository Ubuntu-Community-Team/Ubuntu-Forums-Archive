---
title: "Unable to get extensions in Firefox"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by bobbygr on 2005-07-28
I cannot get extensions in Firefox that comes with Ubuntu Linux.  

I've read some stuff on message boards that talks about updating about:config?

Does anyone know where this file is?

Is there a way to get firefox under ubuntu - access to the firefox extensions online?

Thanks,

Bob

---

### Post by gb25 on 2005-07-28
[QUOTE=bobbygr]I cannot get extensions in Firefox that comes with Ubuntu Linux.  

I've read some stuff on message boards that talks about updating about:config?

Does anyone know where this file is?

Is there a way to get firefox under ubuntu - access to the firefox extensions online?

Thanks,

Bob[/QUOTE]
 Type about:config in the address bar in firefox.  At the top there will be a 'filter' bar.  Type in vendorsub and there should be one entry.  I think it's 1.0 by default.  Change it to 1.0.4 then it will work.  You might have to restart firefox.

---

### Post by sunwave on 2005-07-28
[QUOTE=bobbygr]I cannot get extensions in Firefox that comes with Ubuntu Linux.  

I've read some stuff on message boards that talks about updating about:config?

Does anyone know where this file is?

Is there a way to get firefox under ubuntu - access to the firefox extensions online?

Thanks,

Bob[/QUOTE]
 Open Console and type:

apt-get update
apt-get upgrade

This will force your Ubuntu to be up to date - Firefox too.

But Ubuntu only Backport existing Firefox-Package, therefore you need to Change the Vendorsub as described above.

But since a few days Firefox 1.0.6 is out - therefore type in 1.0.6

---

### Post by regebro on 2005-08-16
Update + Edit: I had the same problem, and my vendorsub is correct (1.0.6), but I was using Warty. After upgrading to Hoary, the problem went away.

---

