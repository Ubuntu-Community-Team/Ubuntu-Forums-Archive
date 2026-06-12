---
title: "ssh failed after upgrade to Intrepid"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by buddy_krish on 2008-10-31
Hi,

I upgraded from Hardy to Intrepid today and ran through some installation errors reg. NIS which seemed to be resolved once I removed my old NIS...

Now...I'm unable to do an SSH to my solaris boxes and here is the output of ssh -vvv box.

====================
debug1: Offering public key: /home/USER/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 149
debug2: input_userauth_pk_ok: fp 38:a8:6d:b6:e3:9b:c0:e8:37:02:5a:c0:b4:d3:8a:18
debug3: sign_and_send_pubkey
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/USER/.ssh/id_dsa
debug3: no such identity: /home/USER/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
====================

I have no ida if NIS errors are responsible for this or not..but I need to solve this ASAP before I get a stinky bad boot from my boss :-(

Update: already tried chmod'ing the .ssh directory...copying the same ssh directory as it is from the server....

---

### Post by buddy_krish on 2008-11-02
NO ONE HAS ANY IDEA WHAT's screwing up  :-(
I will be forced to reinstall OS if i cant do this...and I dont want to do it...

ANy mighty soul...that can help me...?????

---

### Post by buddy_krish on 2008-11-03
[Update]
Its looking for DSA key...while Key's I already have are RSA keys...
Now, that poses a new question...

HOW DO I MAKE SSH TO CHECK FOR RSA KEYS INSTEAD OF DSA KEYS??

---

### Post by Chadarius on 2008-11-05
Perhaps it isn't finding the RSA keys where it needs to? Have you tried running ssh-copy-id userid@remote-server command? That will copy the RSA public key to your remote server in the ~/.ssh/authorized_keys file.

---

