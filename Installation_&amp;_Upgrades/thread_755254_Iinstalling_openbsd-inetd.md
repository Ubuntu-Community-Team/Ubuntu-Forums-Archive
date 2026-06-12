---
title: "Iinstalling openbsd-inetd?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by PhilKarras on 2008-04-14
I was trying to start  openbsd-inetd but I kept getting the error "command not found" & a sudo ls /etc/init.d/ found no openbsd-inetd.

I tried sudo apt-get install openbsd-inetd & it installed but now when I try to Telnet to the linux box it hangs & never gets to user/pw prompts & entering anything simply returns me to the DOS prompt.

I can ping the box.

What have I done wrong?

tnx,
pk

---

### Post by PhilKarras on 2008-04-15
OK, I've discovered something else, while the command I used,

sudo apt-get install openbsd-inetd

did in fact install openbsd-inetd it did NOT install it into /etc/init.d and I have no idea where it was installed. It is running but 

sudo ps -ef | grep openbsd-inetd only shows it is running but not from where?

I tried, sudo openbsd-inetd restart and that did not work either.

So, the questions now are, "where is it," and "are the present problems due to it not being in the right place?"

If it is in a different place is it picking up my /etc/inetd.conf file or not?

Since openbsd-inetd is normally in /etc/init.d and the inetd.conf file is in /etc if I find openbsd-inetd & put a copy on the conf file one level lower will Telnet start working?

How do I find where openbsd-inetd is?

---

### Post by Deathrend on 2008-04-15
```

cd /
sudo find -name openbsd-inetd

```

That should search everything for "openbsd-inetd"

---

