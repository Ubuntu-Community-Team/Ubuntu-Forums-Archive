---
title: "Error 403 Forbidden on libmysqlclient16"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tawmas on 2010-02-16
Hello,

while trying to upgrade, I keep getting this error from APT:

```
Err http://archive.ubuntu.com lucid/main libmysqlclient16 7.0.9-1
  403  Forbidden [IP: 91.189.88.30 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-cluster-7.0/libmysqlclient16_7.0.9-1_amd64.deb  403  Forbidden [IP: 91.189.88.30 80]
```

I think something is wrong with the archives... I'm not sure where to report that, though. Suggestions?

Thank you,
Tommaso

---

### Post by xtoudi on 2010-02-16
> **tawmas said:**
> Hello,

while trying to upgrade, I keep getting this error from APT:

```
Err http://archive.ubuntu.com lucid/main libmysqlclient16 7.0.9-1
  403  Forbidden [IP: 91.189.88.30 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-cluster-7.0/libmysqlclient16_7.0.9-1_amd64.deb  403  Forbidden [IP: 91.189.88.30 80]
```

I think something is wrong with the archives... I'm not sure where to report that, though. Suggestions?

Thank you,
Tommaso

The same here. When I put the URL in FF I've got:
```
Forbidden

You don't have permission to access /ubuntu/pool/main/m/mysql-cluster-7.0/libmysqlclient16_7.0.9-1_amd64.deb on this server.
```

---

### Post by cariboo on 2010-02-16
Try a different server.

---

### Post by MinimalBin on 2010-02-16
The original server sometimes might be throttled - as *cariboo907* said, changing it and you should be fine.

---

### Post by drdjr on 2010-02-16
I've been getting this libmysqlclient16 error today and yesterday.

---

### Post by scradock on 2010-02-17
> **cariboo907 said:**
> Try a different server.
Both the Main and the US server are consistently giving this response - how does one alert their managers? Anyone know?

---

### Post by xtoudi on 2010-02-17
> **scradock said:**
> Both the Main and the US server are consistently giving this response - how does one alert their managers? Anyone know?

And also PL server :-)

---

### Post by flyingstar16 on 2010-02-17
[https://bugs.launchpad.net/ubuntu/+source/libmysqlclient-lgpl/+bug/522225](https://bugs.launchpad.net/ubuntu/+source/libmysqlclient-lgpl/+bug/522225)
Quoted from me:
> 
Last time this happened, it was with python and it was due to a very big bug python had that would crash all machines that upgraded it.
I hope this is not the case, but I suggest NOT to download it from other mirrors in order to prevent problems with your distro.
At least until an official answer.


---

### Post by tawmas on 2010-02-17
Thanks, I subscribed to the bug.

---

### Post by shafin on 2010-02-17
This server works for amd64:

[http://ubuntu.mirrors.tds.net/pub/ubuntu/pool/main/m/mysql-cluster-7.0/libmysqlclient16_7.0.9-1_amd64.deb](http://ubuntu.mirrors.tds.net/pub/ubuntu/pool/main/m/mysql-cluster-7.0/libmysqlclient16_7.0.9-1_amd64.deb)

---

