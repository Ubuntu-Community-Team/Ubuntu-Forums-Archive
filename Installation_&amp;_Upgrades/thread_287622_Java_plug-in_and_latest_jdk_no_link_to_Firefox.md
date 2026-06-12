---
title: "Java plug-in and latest jdk no link to Firefox"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2006-10-29
Hi,

The only time that the java plug-in has ever worked for me was during the original install of ubuntu. That set-up got broken when I responded to "update available" and Add/Remove installed Firefox Lite. Since then, I have been reading up on all the posts concerning the java plug-in. Firefox doesn't make things clear because they don't have a plug-ins list like the old Netscape browser did.

I HAVE to have the current JDK on java. Have to. Add/Remove in ubuntu does not see java plug-in 1.6 or java SDK 6.0. That's not terribly important. I must have a version of 1.5 because I want the NetBeans IDE. The code that Eclipse IDE generates doesn't do it for me, especially when I try the java program over on WinOS.

So here is where the mass confusion begins...

1. I've noticed on the maillist postings that the link for the plug-in should be

```
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```

Because Add/Remove does not see the latests and greatest java kits out there I manually downloaded NetBeans from netbeans.org, installed and that prompted I should have Sun jdk_1.5.0_09. "Yeah, I want it."

I have learned -- since reading the mailists and working on all this -- I now have jdk working under

```
/home/**myUserName**/jdk1.5.0_09
```

which doesn't have a plug-in, and yet the Firefox folder has a link to a java folder I don't use for development that *does* have the plug-in.

=====================

How should I approach this? Delete the installed jdk I have going? Delete ALL jdk??? And then, how would I do a manual install? Is it important that I have all of this linking at the /root instead of the /home/user ?

---

### Post by Unterseeboot_234 on 2006-10-29
OK, installed, from Add/Remove, WebStart 1.4, Blackdown Java which starts the splash, then it asks if we need to use Sun 1.5 instead, and then a java class will run. Has to be a link problem. I've got 2x 53meg of JRE on my hard drive I don't really need but I'm afraid to delete. It works.

Sun doesn't make things any better. Their download page all points to the 6.0 SDK. There is no separate java plug-in yet. You gotta take the whole SDK.

Thanks everyone. The Forums is the only reason I have faith that everything ubuntu can and will keep working.

---

