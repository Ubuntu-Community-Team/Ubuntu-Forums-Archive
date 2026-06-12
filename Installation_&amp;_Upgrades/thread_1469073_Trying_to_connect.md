---
title: "Trying to connect"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by TheStoneCold on 2010-05-01
Ok, I have set up Ubuntu 9.10 and when I try to connect via SSH using PuttY I get connection refused on port 22. Can anyone tell me why or does anyone have a soloution?
Thanks.
Note: It is a VPS linux server, so I can't do stuff like GeEdit. ect.

---

### Post by TheStoneCold on 2010-05-01
Bump.

---

### Post by iponeverything on 2010-05-01
Is ssh installed on the server?

---

### Post by TheStoneCold on 2010-05-01
If you mean did I type this, then yes.

sudo apt-get install openssh-server openssh-client

---

### Post by iponeverything on 2010-05-02
are there iptables rules present on the machine?

```
sudo iptables -L -n
```

---

### Post by TheStoneCold on 2010-05-02
I get.

```
root@imageshark:/# sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by iponeverything on 2010-05-02
that looks good. what happens when you

```
ssh localhost
```

---

