---
title: "FC4 to Dapper : keeping /home on RAID0?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by remi_2 on 2006-06-07
Hi, 

I would like to migrate my linux Amd64 X2 system from FC4 to Dapper amd64 server.

I'd like to keep the /home partition intact. This partition is on top of a RAID0 device.

On this home partition I have my personal account, which I would like to keep, and I also would like to set as the administrator account (default sudoer) of the system.

How can I tell the Dapper installer to rebuild the RAID0 volume without reformating it, and use my existing account on the existing /home partition as default sudoer account? 

I know there is no root account on Ubuntu/Kubuntu, this is why I'd rather ask some help rather that taking the risk of messing things up.

Thanks alot for your help.

---

### Post by bluenova on 2006-06-07
:EDIT: Sorry just seen you want to use the server version, so my post is pointless.

---

### Post by remi_2 on 2006-06-07
No no don't think its pointless!

it should work more or less the same under desktop or server versions!!!

I have tried to mess around with mdadm and mount and managed to mount the old /home partition in the ubuntu file system under /oldhome, the only problem now is with groups and users, the UID are in total mismatch so that users cannot write or read their own files!

any help appreciated!

---

