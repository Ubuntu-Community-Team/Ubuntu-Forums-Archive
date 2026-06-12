---
title: "Failed to connect to Windows Share: Software connection aborted"
date: 2020-05-10
forum: Installation &amp; Upgrades
---

### Post by sjmgeezer on 2020-05-10
This SOLVED - information for other 'Not so experienced'
Hope it helps.
I have recently upgrade to Ubuntu Desktop 20.04 LTS.

Have always been able to connect to local NAS and Shares via Ubuntu previous versions.
When connecting get the above error: Failed to connect to Windows Share: Software connection aborted

smb.conf under [Global] heading enter this line if not already there - mine was blank.

>sudo nano /etc/samba/smb.conf                   (or your favourite editor)

Part of file:
[Global]
client min protocol=NT1



Example: smb.conf

#======================= Global Settings =======================

[global]

## Browsing/Identification ###
client min protocol = NT1

# Change this to the workgroup/NT-domain name your Samba server will part of

---

