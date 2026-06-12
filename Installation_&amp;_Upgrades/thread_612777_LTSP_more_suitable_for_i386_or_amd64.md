---
title: "LTSP more suitable for i386 or amd64"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by marisdembovskis on 2007-11-14
Hi. 
I want to setup LTSP on my amd 64 bit box. 

And I'm thinking what is better:

--- install as server i386 version or amd64 all Gutsy Ubuntu.
because I sometimes get tired of workarounds with amd64, or should I use amd64 in this case.



thank you guys ltsp automatization under ubuntu.
m.

---

### Post by marisdembovskis on 2007-11-15
i installed amd64 server.
but which files I need to change becaus thin client says can not find 
it gets address than stops. 


I edited /etc/lpt/dhcpd.conf and changed i386 to amd64 in every place it was there is there anything else i need to change?

thank you.
m.

---

### Post by marisdembovskis on 2007-11-15
Ok. 
I reinstalled server then i got on thin client this message:



Loading vmlinuz .............
Loading inittrd.img .....................
Ready.

Your CPU does not support long mode. Use a 32 bit distribution.



Does it mean, that my thin client will work only on 32 bit Gusty?

will appreciate any help.
thanks.

---

### Post by PmDematagoda on 2007-11-15
Yes, as given by the Live CD, your PC only supports 32 bit and not 64 bit, and by the way, Ubuntu 7.10(Gutsy) is not an LTS(Long Term Support) version, it is Ubuntu 6.06(Dapper) that is the LTS version.

---

### Post by Lem on 2007-11-15
You can run 32 bit clients on 64 bit LTSP server.

You need to build your client as 32 bit though.

Prob best to clear out your old build;

Look in /opt/ltsp the 32 bit directory is called i386. Dont know what the 64bit version gets called so you'll have to check. Assuming its 'amd64' then;
```

sudo rm -rf /opt/ltsp/amd64
```

to clear it out and then;
```

sudo ltsp-build-client --arch i386
```
to build a 32-bit client.

---

### Post by Lem on 2007-11-15
> **PmDematagoda said:**
> Yes, as given by the Live CD, your PC only supports 32 bit and not 64 bit, and by the way, Ubuntu 7.10(Gutsy) is not an LTS(Long Term Support) version, it is Ubuntu 6.06(Dapper) that is the LTS version.

Think you've somewhat misunderstood this thread, dude. LTSP = Linux Terminal Server Project

---

### Post by PmDematagoda on 2007-11-15
Ooops, my bad, really sorry for the misunderstanding. Thanks for the info Lem:).

---

### Post by marisdembovskis on 2007-11-22
thanks 
sudo ltsp-build-client --arch i386
worked great, only Gutsy is very slow itself, at least for me.

---

### Post by Lem on 2007-11-22
That's odd.. gutsy and the ltsp clients are really snappy running on a el cheapo 100Mbit test router. I have a router with 1000Mbit uplink on order.

You might have a networking issue.

---

### Post by marisdembovskis on 2007-11-23
Thanks, Lem.
Well LTSP issue is solved. 
But I don't really understand why my server Gutsy is slow. I already turned off visual effects. 
I have 3200 AMD 64 512 Ram. 
huh, will try to get it faster ...

---

### Post by marisdembovskis on 2007-11-26
Hi. 
Now it's faster. 
I reinstalled and did not install videocard driver. 
Pc is pretty fast now. 
I choose plug and play and may resolution, before I installed nvidia or something driver. 
:)

---

### Post by marisdembovskis on 2007-11-27
One more thing!

How to make LTSP keyboard for thin client the same as on server. 
on server /etc/X11/xorg.conf 
I specified my needed keyobard, but on thin client there is some other layout than I specified on /etc/X11/xorg.conf



how to make on thin client the same keyboard?
thank you folks.
m.

---

