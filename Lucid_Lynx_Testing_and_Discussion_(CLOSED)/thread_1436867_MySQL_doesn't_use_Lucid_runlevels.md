---
title: "MySQL doesn't use Lucid runlevels"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Arlanthir on 2010-03-23
Hm, I'm not sure this changed with Lucid or mysql, I'm hoping to find anyone with a similar issue. If this doesn't belong here (ie, doesn't relate to lucid), please move it.

In Karmic I installed mysql and noticed it autostarted. I removed it from some runlevels (3 and 5, if memory serves me right) and it stopped running everytime.

Now with lucid, mysql autostarts but chkconfig --list mysql states:
```
mysql                     0:off  1:off  2:off  3:off  4:off  5:off  6:off
```

I can't find it in System > Preferences > Startup Applications either. Where can I check more?

---

### Post by feiy on 2010-03-23
edit the /etc/init/mysql.conf

---

### Post by Arlanthir on 2010-03-23
> **feiy said:**
> edit the /etc/init/mysql.conf

I guess I'm supposed to change the lines

```
start on (net-device-up
          and local-filesystems)
```

But I don't know what to put there. Would a comment suffice?

**Edit**: It did the trick, thank you :)

---

### Post by gregh on 2010-03-29
What did you edit in the end?

---

### Post by Arlanthir on 2010-03-29
> **gregh said:**
> What did you edit in the end?

I commented out the quoted lines :)

Snip of the end result:
```
#start on (net-device-up
#          and local-filesystems)
stop on runlevel [016]

```

---

