---
title: "afs on lucid"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ssam on 2010-03-22
if you are using AFS (openafs) to access files and update to ubuntu lucid, the you may be bitten by the following error when you authenticate 

```

sam@oberon:~$ kinit 
Password for user@host: 
sam@oberon:~$ aklog
aklog: Couldn't get host AFS tickets:
aklog: unknown RPC error (-1765328184) while getting AFS tickets

```

this is apparently because "MIT Kerberos 1.8 disables DES by default"
[http://thread.gmane.org/gmane.comp.file-systems.openafs.general/26973](http://thread.gmane.org/gmane.comp.file-systems.openafs.general/26973)

the solution is to add the line
```

allow_weak_crypto = true

```

to the ```
[libdefaults]
``` section of your ```
/etc/krb5.conf
```


also if you get

```
aklog: unable to obtain tokens for cell hep.man.ac.uk (status: 11862788).
```

you may need to rebuild your openafs module
```
sudo dpkg-reconfigure openafs-modules-dkms
```
and restart the openafs-client
```
sudo /etc/init.d/openafs-client restart
```

---

