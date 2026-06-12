---
title: "Flash not working"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by perzynskij on 2011-09-21
I recently did a clean install of 11.04 on a laptop and have run into a problem with flash. He is the list of sites that do not work: Google Maps, Youtube, Google Translate, Google New and You+. I have tried flash aid and different browsers Firefox 6.02, Chrome and Epiphany. I am using a DELL 17R with a i7 processor with Ubuntu 64bit. 
Thanks
Jared

---

### Post by vinterkind on 2011-09-21
Hi,

Why don't you try to remove one of your shockwave versions ? 11 or 10.3 ?

do you have a /usr/lib/mozilla .. libflash.so ?
or a /usr/lib64/mozilla .. libflash.so ?

---

### Post by Enigmapond on 2011-09-21
Well you couldn't have run the Flash-Aid addon correctly as it would have uninstalled one of those flash instances. Just remove the version 10 and it should sort out. They are conflicting with each other...11 is the beta version.

---

### Post by vinterkind on 2011-09-21
@Enigmapond

Thx for the info about this plugin. I didn't know that!
Ever handled it manually ... >.>

Any known problems with 32 or 64bit versions ?

---

### Post by perzynskij on 2011-09-21
I currently have both paths and this could be the conflict. I did uninstall all versions of flash and the files are still there. Not sure on how to remove version 10 of shockwave but I did disable it. Installed flash aid but it is not showing any problem. Adobe version test shows that "You have version 11,0,1,98 installed"

---

### Post by vinterkind on 2011-09-21
If unsure just delete the libflash.so 
the plugin should install the file anyway then.

btw. you can concentrate on the /usr/lib64 path as you said you've got ubuntu 64bit.

try *[noparse]about:plugins[/noparse]* in the address bar of firefox

---

### Post by vinterkind on 2011-09-21
funny that :p

```
about:plugins
```

---

### Post by perzynskij on 2011-10-08
Turns out it was not a flash problem but a DNS issue since I am in Japan.
FIXED by doing the following

sudo vi /etc/resolv.conf

and added

nameserver 8.8.8.8 
nameserver 8.8.4.4
nameserver 208.67.222.222
nameserver 208.67.220.220

Google Public DNS.

Jared

---

