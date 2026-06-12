---
title: "ssh: Pub key log on"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by rimshot21 on 2006-07-16
I have followed the instructions in the wiki (Dad Showed me) to setup an ssh tunnel with public key. I'm still asked for my password on the remote machine when ever I ssh into it.](*,) 

Can anyone suggest why this might not be working??

---

### Post by infoburner on 2006-07-16
when you generated the key, it asked you to enter a passphrase, right? all you have to do is do it again, only this time leave the passphrase empty. then you can just do 'ssh hostname' and it should go strait in. (this method is not recommended if security could be an issue)

---

### Post by rimshot21 on 2006-07-16
Thank you for the fast reply.

I didn't put in a passphrase but I tried it again anyhow.
This is what happens when I try and copy the key to the other machine:

```

rimshot@mr004:~$ ssh-copy-id -i /home/rimshot/.ssh/id_dsa.pub rimshot@192.168.0.2
29
rimshot@192.168.0.2's password:

```

Thanxs

---

### Post by infoburner on 2006-07-16
yeah, it needs your password to copy the key in the first place, but once it's there, you should be able to ssh into it without the password. i think...

---

### Post by rimshot21 on 2006-07-16
Yes that is what I thought too.

Do you know what the 29 means?


Thank You very much

---

### Post by infoburner on 2006-07-16
> **rimshot21 said:**
> Yes that is what I thought too.

Do you know what the 29 means?


Thank You very much
no idea

---

