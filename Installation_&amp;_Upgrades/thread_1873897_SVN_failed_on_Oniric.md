---
title: "SVN failed on Oniric"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by tanoloco on 2011-11-02
Hello,

after upgrading to Lubuntu 11.10 Oneiric I can't use svn anymore:

- RabbitCVS is not working:
(any suggestion on how to make it working? on rabbitcvs.org they say it could work but I can't figure out how to do it)

- Any other svn client like WorkBench or RapidSVN can't resolve my host: on "checkout" or "update" command it says "Can't Resolve Hostname - Host Not Found".

Everything works great on Lubuntu 11.04

Any suggestion on how to fix it in 11.10?

Many thanks

---

### Post by infinitybot on 2011-11-02
Is the OS 64 bit?

---

### Post by alco75 on 2011-11-02
Can you reach the host if you ping the IP in a terminal or paste the IP into a browser?

What happens if you run **svn update** in a terminal (assuming you have the **subversion** package installed)?

---

### Post by tanoloco on 2011-11-02
> **infinitybot said:**
> Is the OS 64 bit?
Hi, thanks for your reply.
No, the os is 32 bit

---

### Post by tanoloco on 2011-11-02
> **alco75 said:**
> Can you reach the host if you ping the IP in a terminal or paste the IP into a browser?

What happens if you run **svn update** in a terminal (assuming you have the **subversion** package installed)?

Hello, thanks for your post.

The url of the repository is in the format:
```
http://svn.xxyyzz.local/projectname/trunk
```

If I copy and paste this into a browser it says me it can't find svn.xxyyzz.local

If I ping it into a terminal
```
ping svn.xxyyzz.local
```

 it says me:
```
Can not find svn.xxyyzz.local.
```

Everything is going fine if I ping it through its IP

:confused:

If I run **svn update** in a terminal it says me:
```
svn: OPTIONS di 'http://svn.xxyyzz.local/projectname/trunk': Unable to resolve hostname «svn.xxyyzz.local»: Host not found (http://svn.xxyyzz.local)

```

I do have subersione installed
```

sudo dpkg -l subversion

ii  subversion     1.6.12dfsg-4ub Advanced version control system

```

---

### Post by tanoloco on 2011-11-04
For what concerned Workbench I solved using the ip of the machine.
Rabbitvcs is still not working for me.

Any suggestion in this direction would be appreciated.
In the meanwhile I mark this thread as solved,
because in fact I can use svn on 11.10 :)

Thanks

---

