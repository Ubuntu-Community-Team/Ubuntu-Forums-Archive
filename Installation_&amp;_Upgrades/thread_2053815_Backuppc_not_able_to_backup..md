---
title: "Backuppc not able to backup."
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2012-09-06
Hello folks.

I have installed Backuppc on a ubuntu 11.10 system. When I want to start a backup this is the message I get in my log.

2012-09-06 09:16:07 full backup started for directory /etc/bind
2012-09-06 09:16:08 Got fatal error during xfer (Unable to read 4 bytes)
2012-09-06 09:16:13 Backup aborted (Unable to read 4 bytes)

Does anyone have any experience with this? And yes I have googled the whole web for this problem but the solutions do not work.

Things I have done:

Backuppc Server(Ubuntu 11.10):
Installed backuppc rrdtool and rsync

Added a user: backuppc

Generated a ssh public key with: sudo ssh-keygen -t rsa -C "backuppc"

Added user backuppc to the list of sudoers with: sudo echo "backuppc ALL=NOPASSWD: /usr/bin/rsync" >> /etc/sudoers

Transfered the public key from the backuppc server to the client.
sudo ssh-copy-id backuppc@clienthostname

Client(Ubuntu 11.10):

Installed rsync.

Added a user: backuppc

Added user backuppc to the list of sudoers with: sudo echo "backuppc ALL=NOPASSWD: /usr/bin/rsync" >> /etc/sudoers

Changed the permission rights of ~/.ssh/*.
sudo chmod -R go-rwx ~/.ssh/*


I can login from backuppc server to the client via ssh, without entering a password.
If I forgot anything please let me know.

Thanks in advance

---

### Post by MocroNL on 2012-09-07
Anyone?

---

