---
title: "[jaunty] encrypted home and ssh public key not working"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chrroessner on 2009-03-16
Hi,

I have setup a server with Jaunty alpha 6. I have chosen an encrypted home partition. Then I copied a rsa key to the existing user support.

If I have logged in via bash, I can ssh into the server from remote, because the home partition is decrypted. But if I logout the bash session, I can no longer login from remote. That is clear, because the authorized_keys file in /home/support/.ssh/ is not readable.

So my question: Can I configure ssh, pam or whatever to decrypt the home partition, if an incoming ssh session is treid to be opened?

Thanks in advance

Christian

---

