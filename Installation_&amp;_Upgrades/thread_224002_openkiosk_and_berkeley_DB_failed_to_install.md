---
title: "openkiosk and berkeley DB failed to install"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by peterroots on 2006-07-27
I have been trying to set up an internet cafe using openkiosk.  It tells me it needs berkeley DB 4 inorder to work.
I used synaptic to check and where required install various bits of the berkeley DB eg db4.3 util, libdb4.3, libdb4.3++c2 libdb4.3-dev libdb4.3++-dev .  I thought this should cover it but openkiosk says no berkeley DB.
next I downloaded and installed the tar from sleepycat  - i added --prefix=/usr to the configure command as I had read this was needed on debian systems.
Still no luck.
any suggestions on how to get this to work or any alternative cyber cafe (linux server. linux clients with remote possibility of windows clients)
Thanks

---

### Post by peterroots on 2006-07-31
I started theis porcess weeks ago using Mandriva2006 and failed dismally so tried again using Kubuntu.
A very informative posting from  Sebastian Müsch pointed out various errors in the ./configure file which got me past the configure and make stages but after make install I still could not run nodeview (the openkiosk server).
I have yet to tackle the client software!
Uninstalled and tried again, this tiem I remembered to do as I was told and type ./configure --prefix=/usr but still does not work - cannot open shared object file libdb-4.3.so

---

### Post by david_kt on 2007-01-20
> **peterroots said:**
> Uninstalled and tried again, this tiem I remembered to do as I was told and type ./configure --prefix=/usr but still does not work - cannot open shared object file libdb-4.3.so

Every time you open new terminal, you need to execute:

      export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/BerkeleyDB.4.X/lib

change X in BerkeleyDB.4.X above with your version.
After that, you will be able to execute:

      nodeview

Regards,
DK

---

