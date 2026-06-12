---
title: "Server and port"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by I_Learning_I on 2010-10-14
Well, first of all I would like to apologyze for using my first post as a request of help, I've visited Ubuntu forums every now and then, but since I wasn't that active on Ubuntu I didn't take the time to register.
Secondly I'm not sure if this belongs in servers sections or installations, since my problem as a little of both.
I've done my research, and even tried to do it by myself, so far nothing, don't take me as a lazy person please.

Up to the problem, I'm required to install a WebServer in my box so I can work in it for classes, I had no problems installing the tools, the main problem is that I had, prior to the LAMP install, installed WebGoat a Penetration test tool, that requires Apache Tomcat.
So I have quite a few problems now, as it does not assume localhost or 127.0.0.1 and therefore I have no webserver.
I can only access it through port 8080 (instead of 80) and it goes to a page related with Apache Tomcat.

A little resume:
I need to install LAMP, not necessarly the lamp-server package, no rpoblem in installing every packs  one by one, just as long as it works ^^.
Need to change listening port back to 80.
Remove Tomcat.

I have seen the ports.conf file and it's set top listen to port 80.
I have done apt-get remove tomcat6 and still there were many files and folders, so I deleted them, however it seems I left some stuff behind =\
I have also installed lamp-server and syscp.

I must also say I'm not very experienced as I only use Ubuntu every now and then, being gradually increasing it's usage.

Thank you all, for your help and time :)

---

### Post by I_Learning_I on 2010-10-19
Hmmmm, sorry for thee bump, but still waiting for an answer...
Anything will be welcome :)

---

### Post by CharlesA on 2010-10-19
Is tomcat still listening or running?

```
sudo netstat -lnp
```

---

### Post by I_Learning_I on 2010-10-21
Thanks for the help, since I had a tight schedule I was forced to uninstall tomcat and every other packages that could influence and re-install.
I've been very busy and could only come here today, sounds silly, since I was in such a rush and seems like all of sudden abandon the post.

---

