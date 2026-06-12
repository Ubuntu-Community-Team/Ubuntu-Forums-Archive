---
title: "system hangs exiting apt-get install"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by ezacon on 2008-02-02
I have just installed a new Ubuntu 7.10 server in an old amd machine.
Everiting goes just fine except that the system hangs most of the times when i install some package with apt-get install. It d'ont happens always. Maybe 3 of 5.
It's anoiyng because i am configuring the server with ssh from home, and i have to go to office to reset server each time it hangs.
After reboting, there is nothing relevant in syslog.
It always happens at the end of the instalation process. The packages are downloaded, uncompressed and configured and just before returning to shell prompt, the session freeze. Some seconds after, the ssh session is disconected and the server no longer answer to ping. Before reseting server, i verify that system console does not respond, and there is nothing on screen after login: prompt.
Next time i whant to use apt-get, i need to issue a "dpkg --configure -a" before.
If i d'ont use apt-get, the system works fine for days. I use Samba to share files, dns server bind9 and openvpn. The system does not hang with normal use, only when i do apt-get install


Any idea how to troobleshot this one?

---

### Post by ajgreeny on 2008-02-02
Don't know if or why it might make a difference but have you tried aptitude instead of apt-get?  This assumes aptitude is installed and its use is possible in a server system, which I think it should be.

---

### Post by ezacon on 2008-02-03
Never used aptitude. I will install it and test.
Anyway, i would sleep beeter if i can discover where the problem is.
Thanks

---

