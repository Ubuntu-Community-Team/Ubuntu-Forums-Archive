---
title: "sshd2_config"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by Red Rebel on 2011-01-14
Hi all, 

I am reading a book on OpenSSH and I need some help on sshd2_config . I cannot locate this file. The author claims that it should be in /etc/ssh2/. I don't see the ssh2 directory either. Is this another component that is not installed? Since the book is an implementation book, it doesn't give all the details as to what it is. It assumes you know. Any helpful explanation would be greatly appreciated. 

I am running Ubuntu server 10.04LTS.

---

### Post by sikander3786 on 2011-01-15
It should be under /etc/ssh/sshd_config and not ssh2.

Make sure you installed openssh-server by,

```
sudo apt-get install openssh-server
```

And unless you want to tweak it, you don't need to edit the configuration files. Once installed, it is ready to use.

From another machine:
```
ssh username@ip-address
```

---

### Post by Red Rebel on 2011-01-15
Yes, I have the ssh directory and the sshd_config file. I am not sure what he is talking about in the book. It looks like it is a seperate daemon to control the sshd_config daemon or something. I was just wondering if anyone knew anything about it, thanks....



rr

---

