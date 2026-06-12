---
title: "Backup using rsync and DeltaCopy"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by LoermansA on 2008-01-24
Hi all,

I have a ubuntu server at home which serves my media and acts as a backup server. For this I have rsync running as backup server. On my windows clients I'm using deltacopy to create and run backup profiles.

The problem I'm having is with rights of the files that are backed up. If I backup a directory tree, the top level tree gets its rights just as I'd expect them (based on rsyncd.conf) but the second level of files get reduced rights and the third level of files/directories get 0000 as rights mask.

The only way I can make backups is by running rsyncd as root (see conf file) so that it at least has enough rights to create subdirectories and create files several levels down the directory tree.

Why is rsync creating files and directories with different rights depending on the level in the directory tree it has to backup? How can I correct this?

This is my rsyncd.conf:
```

motd file = /etc/motd
log file  = /var/log/rsyncd.log
pid file  = /var/run/rsyncd.pid
lock file = /var/lock/rsync.lock

[laptop]
  path         = /mnt/backup/laptop
  comment      = RSync backup voor laptop
  uid          = 0
  gid          = 0
  read only    = no
  list         = yes
  auth users   = arjan
  secrets file = /etc/rsyncd.secrets

[pc]
  path         = /mnt/backup/pc
  comment      = RSync backup voor pc
  uid          = 0
  gid          = 0
  read only    = no
  list         = yes
  auth users   = arjan
  secrets file = /etc/rsyncd.secretsroot

```

Ideally this is what I want: rsyncd should backup to both /mnt/backup/laptop and /mnt/backup/pc as user 'arjan'. This user has all necessary rights in these folders.

Tia,

Arjan

---

### Post by chips43 on 2008-04-26
I had the same problem as you. The only difference in configuration was that my uid and gid were my username and not 0.

My solution was to upgrade rsync.exe in the deltacopy folder to 2.6.9 . (support.svi.nl/wikifiles/rsync_269.zip). There are newer version of rsync out there, but I didn't want to install cwRsync. 

Next step was to include the following switch to the additional parameters option:
--chmod=u+rwX

This makes all directories drwx------ so at least writable for user.

---

