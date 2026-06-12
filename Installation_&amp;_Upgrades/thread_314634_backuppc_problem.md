---
title: "backuppc problem"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by c2y on 2006-12-07
i want to use ubuntu as backupserver and give backuppc a try. i was able to install backuppc successfully but i got this problem backing up a linux box using the rsync method.:


Running: /usr/bin/ssh -q -x -l root 192.168.6.50 /usr/bin/rsync --server --sender --numeric-ids --perms --owner --group --devices --links --times --block-size=2048 --recursive --ignore-times . /home/
Xfer PIDs are now 5508
Rsync command pid is 5508
Fetching remote protocol
Got remote protocol 1953722184
Fatal error (bad version): Host key verification failed.

Checksum seed is 2036689696
Got checksumSeed 0x79656b20
Read EOF: Connection reset by peer
Tried again: got 0 bytes
fileListReceive() failed
Done: 0 files, 0 bytes
Got fatal error during xfer (fileListReceive failed)
Backup aborted (fileListReceive failed)


Please help.

---

### Post by jBilbo on 2006-12-20
Seems related to ssh connection. You should put your backuppc's ssh key (from server) to authorized_keys file on the client.
This way you can connect to client machine without "ask password" prompt.

---

### Post by jBilbo on 2006-12-20
See this: [http://backuppc.sourceforge.net/faq/ssh.html#how_do_i_setup_openssh](http://backuppc.sourceforge.net/faq/ssh.html#how_do_i_setup_openssh)

---

