---
title: "NFS mount issues using ubuntu 9.10 (Access Denied)"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by egandt on 2010-01-16
Ok first off I administer about 40 Unix Servers, and of them this is the only system I can not connect to the NFS mount in question.  The NFS server is on an ubuntu 8.04LS server (fully updated), other systems can connect include Gentoo, ubuntu 8.10, ubuntu 8.04LS, Redhat 5 ... all are on the same subnet as the  ubuntu 9.10 box is located.  Thus I'm sure the NFS share is correct and is valid.  I've ensured it is not an issue with the command as even cutting and pasting it from a working system to the ubuntu 9.10 system did not help.

I have installed to correct packages and even force a reinstall of them.  nfs-common, nfs-kernel-server portmap ... 
I have also fully updated the OS as of this morning.  
I have rebooted post installation of updates
I have turned off AppArmor and UFW in case these were causing issues.
I know portmap is ok based on running "rpcinfo -p"


Simple put as far as the server is concerned the ubuntu 9.10 box never even attempts to connect as on an attempt from any other server I can monitor the connection in the logs.  All I get from the ubuntu 9.10 system is "access denied by server while mounting ..."  Yet there is no connection made to the remote server as I have said.  Using -v in the mount command I also see a failure: "mount.nfs mount (2): Permission denied" this is the actual error that needs to be resolved. 

 
My best guess is that the issue is the permissions one and the other is the generic error message and means nothing in this case, but I can not understand why I'm getting a permission error and on what?

Any ideas?
ERIC

---

### Post by roboa1983 on 2010-09-10
egandt:
Were you able to solve the problem? I have virtually the same, but actually between a 9.04 which is able to mount fine and two recently upgraded 10.04 machines, where I am unable to mount...

---

