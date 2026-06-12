---
title: "NFS won't automount after upgrade from 8.04 to 8.10"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by XezzeX on 2008-11-05
Hi folks. Recently upgraded to Ibex from Heron, and before my two NFS shares being served from an ArchLinux machine would automount on boot. But after upgrading they doesn't automount. Can't see anything during the boot messages explaining the NFS not able to mount.
The following two lines show the two lines I've tried without any luck (the first one worked fine in Heron):
10.0.0.30:/files /files nfs rw 0 0
10.0.0.30:/files /files nfs defaults 0 0
Does anyone have any suggestions to solve this problem?

---

### Post by ajhewett on 2008-11-06
I am having the same problem with 2 from 3 machines which I've upgraded from 8.04 to 8.10.  On one of the upgraded machines the NFS shares mount at boot, on 2 upgraded machines the shares do not mount at boot.  The /etc/fstab entries are the same on all 3 machines.  Networking is OK.  After logging in a 
[INDENT]```
sudo mount -a
```[/INDENT]
will mount the NFS shares without any complaints.  They just don't mount during boot.  I cannot find anything in the logs to indicate an error.
BTW, my NFS server is running Ubuntu 8.04 Server.

Any suggestions welcome.

---

### Post by WhateverFits on 2008-11-09
I hate saying it, but same here. I did, however, just figure it out while I was typing this message. Edit /etc/init.d/mountall.sh and change

```
mount -a -t nonfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs,gfs2 
```
to
```
mount -a -t nonfs,nfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs,gfs2 
```

Note the use of nfs and nfs4. This needs to go in the main line since I have an nfs server configured, not nfs4 yet.

---

### Post by WhateverFits on 2008-11-09
Oops, copy and pasto.

```
mount -a -t nfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs,gfs2
```

---

### Post by marz_cyclone on 2008-11-27
hej,

ich habe das gleiche problem in ibex, d.h. per automounter übers netz gemountete dateisysteme sind nach einem neustart nicht erreichbar. als workaround habe ich in /etc/rc2.d/S99rc.local

/etc/init.d/autofs reload

eingefügt. danach funktioniert der automounter auch nach dem neustart.

grüße

---

