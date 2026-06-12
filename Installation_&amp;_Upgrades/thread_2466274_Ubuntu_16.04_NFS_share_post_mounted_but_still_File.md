---
title: "Ubuntu 16.04 NFS share post mounted but still Filesystem says read-only"
date: 2021-08-24
forum: Installation &amp; Upgrades
---

### Post by devopsall90 on 2021-08-24
Hi All,

I ve a device which is been build under **Ubuntu 16.04,  **where **NFS** share is visible and post mounted the Filesystem says **read-only **even though the exported share has **read-write **permission from Netapp.  

Both the NFS services are in below state,

[FONT=&amp][B]nfs-server.service  - active/exited
[/B]**nfs-client.target  - - active/active**


Error message while touch a file in NFS share path.

** touch: cannot touch 'f1': Read-only file system**

[FONT=Verdana]Kindly advise to help.

[/FONT]
[/FONT]

---

### Post by SeijiSensei on 2021-08-24
16.04 is no longer supported. You need to upgrade to 20.04 or later.

Try mounting the share from the command line with
```
sudo mount -vvv /mountpoint
```
assuming the NFS share is defined in /etc/fstab.  Otherwise
```
sudo mount -vvv server:/share /mountpoint
```

---

### Post by ActionParsnip on 2021-08-25
Isn't Xenial end of life......not supported?

---

### Post by not-published on 2021-08-25
There are two NFS client / servers.  You need to know if your using the Kernel ones or the software-installable ones.  The kernel ones have the bug of freezing the PC if used incorrectly.

I'm unsure how "things are done now".  In the past linux used fstab (software nfs).  (note i've altered the hostname and client address)

# /etc/fstab
127.0.0.1:/mnt/foo /mnt/foo       nfs     rw,addr=127.0.0.1    0 2
127.0.0.2:/mnt/foo2 /mnt/foo2       nfs     rw,addr=127.0.0.2    0 2

so if you mount that it mount will see it and use the 'rw'.  if you wanted 'ro' you'd have to "remount" it.  as far as -vvv, idk.  ask someone else on that.  I'm not 100% sure nfs allows re-mounting.  You might need the 'rw' before the nfs driver is asked to mount it.  mount -o ro /mnt/foo

in /etc/hosts.allow i would have to have  "rpc.nfsd" listed if I used the inetd client, though I omit the full howto on that here, and i think "inetd" has been cancel cultured (gone).  another way was to run the rpcd daemon (when not built-in to the kernel, which i suggested is safer)

Remember I haven't done this recently - that was older linux ok?

---

### Post by not-published on 2021-08-25
I forgot to say that's a daemon question not "installation or upgrade".  You should really post only installtion or upgrade questions in this thread.

---

