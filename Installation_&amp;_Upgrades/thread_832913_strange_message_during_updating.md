---
title: "strange message during updating"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by dexter.deepak on 2008-06-18
i am on ubuntu7.10 (server edition)
i was updating my system after a long time and i got the following window msg...but i cant decipher the message...please help !!

window title : debconf om dpak-server
title :vulnerable host keys will not be  generated
 message :configuring open-ssh server
description:
         Some of the OpenSSH server host keys on this system were generated with a version of OpenSSL that had a broken random number generator. As a result, these host keys are from a well-known set, are subject to brute-force attacks, and must be regenerated.

Users of this system should be informed of this change, as they will be prompted about the host key change the next time they log in. Use 'ssh-keygen -l -f HOST_KEY_FILE' after the upgrade has changed to print the fingerprints of the new host keys.

The affected host keys are:

/etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_dsa_key

User keys may also be affected by this problem. The 'ssh-vulnkey' command may be used as a partial test for this. See /usr/share/doc/openssh-server/README.compromised-keys.gz for more details.

---

### Post by PmDematagoda on 2008-06-18
That message is saying that you have vulnerable SSH keys as a result of this [security notice]("http://www.ubuntu.com/usn/usn-612-4"), so you shouldn't use the keys mentioned and should create new ones.

---

### Post by dexter.deepak on 2008-06-18
but this is what i dont understand..what keys are they in my keyboard ??

---

