---
title: "Problem with scp"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by gazza7 on 2013-02-09
Hi

I'm having a problem with scp on a local network.
I can connect with ```
ssh -p 2222 and username@192.168.0.1
``` with no problems.

If I try to ```
 scp -p 2222 file1 username@192.168.0.4:/home/username/file1 
```

I get ssh: connect to host 192.168.0.4 port 22: Connection refused

Do I need to set the port for scp somewhere else? or does it does it pick it up from /etc/ssh/sshd_config file as with the server?  I'm sure I only set ip up for the ssh sever in the past.

---

### Post by fj401971 on 2013-02-09
I believe it is:

```
scp -P 2222 file1 username@192.168.0.4:/home/username/file1
```

With a capital P

---

### Post by sudodus on 2013-02-09
> **gazza7 said:**
> Hi

I'm having a problem with scp on a local network.
I can connect with ```
ssh -p 2222 and username@[COLOR="Red"]192.168.0.1[/COLOR]
``` with no problems.

If I try to ```
 scp -p 2222 file1 username@[COLOR="red"]192.168.0.4[/COLOR]:/home/username/file1 
```

I get ssh: connect to host 192.168.0.4 port 22: Connection refused

Do I need to set the port for scp somewhere else? or does it does it pick it up from /etc/ssh/sshd_config file as with the server?  I'm sure I only set ip up for the ssh sever in the past.
- Are those two different computers?

- Are you running scp in linux? Then you should have capital -P for port number

---

### Post by gazza7 on 2013-02-09
Hi

Thanks

I was just looking at the help and I didn't notice its a capital P for scp compared with a lowercase p with ssh.  Sometimes you can't see the wood for the trees.

Thanks again to you both for your help, its now working.

---

