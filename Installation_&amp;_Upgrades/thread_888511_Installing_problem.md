---
title: "Installing problem"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by cravetec on 2008-08-13
Hi, I just installed Ubuntu on my laptop and whenever I try to install something I get the following :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have had Ubuntu installed on my Desktop PC for a couple of months now and have never come across this problem. I really have no idea where to start to fix it. Everything else seems fine.

---

### Post by sayakb on 2008-08-13
Open up a termninal (Applications->Accessories->Terminal)
And type in:
```
sudo dpkg --configure -a
```

---

### Post by lisati on 2008-08-13
Go to the terminal (it's on the Applications->Accessories menu), and type in
```
sudo dpkg --configure -a
```
You will be asked for your password - it won't show (for security reasons), use the same password as the one you logged in with.
This should fix the problem. 
If you have any more questions, feel free to ask them!

---

### Post by cravetec on 2008-08-13
tried that. Laptop took a while and then I got this message 

Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135


what now??

---

