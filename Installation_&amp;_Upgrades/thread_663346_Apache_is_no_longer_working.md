---
title: "Apache is no longer working"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by studio56 on 2008-01-10
I just did an upgrade from 6.04 to 7.10 using the update manager. After I did so apache stopped working. When I try to manually start apache I do not even get an error message. It does not say it's trying to start apache, or anything at all. I am using apache2. I have searched on google and in the the forums and have not had any luck. Please help me if you can.

---

### Post by studio56 on 2008-01-10
I fixed it today. I used the:
root@Ubuntu:~# apt-get install --reinstall apache2apt-get install --reinstall apache2

command and kept my config files and now apache is fine. Just as a side note, I also had to reinstall php5 and php5-mysql for my web server to be 100% back up and running. Hopefully this can help someone else so they don't have to sweat with a web server down.

---

### Post by zipperback on 2008-01-10
> **studio56 said:**
> I fixed it today. I used the:
root@Ubuntu:~# apt-get install --reinstall apache2apt-get install --reinstall apache2

command and kept my config files and now apache is fine. Just as a side note, I also had to reinstall php5 and php5-mysql for my web server to be 100% back up and running. Hopefully this can help someone else so they don't have to sweat with a web server down.



Can you mark this thread as [solved]? it might be useful for others to know it has been resolved.

- zipperback
:popcorn:

---

