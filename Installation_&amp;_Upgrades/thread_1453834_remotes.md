---
title: "remotes"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by kr651129 on 2010-04-13
trying to get my remote to work 100% with xbmc so Ive installed lirc

now I need to learn the commands from the following

```

user@computer:~$ sudo -s ## you have to be root for this part
[sudo] password for user:
root@computer:~# cd /etc/lirc
root@computer:/etc/lirc# irrecord --driver=irman --device=/dev/ttyS0 MyRemote ## use the driver that you chose in the previous part. /dev/ttyS0 = first com port

```

BUT I don't know what /dev/? my remote is, helpppppppppppp

---

