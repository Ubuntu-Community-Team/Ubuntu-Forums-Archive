---
title: "Need help reinstalling deleted file"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by bull8042 on 2007-05-08
OK, I admit it, I am a MORON! Toggling between sendmail and postfix to get a working configuration for my laptop, I deleted the sendmail and postfix shell scripts in /etc/init.d in an effort to start from scratch. Now I realize that these are default files apparently included in the base OS install. How screwed am I? Does anyone know how to get these files off of the installation CD or where to download them?
I am running Feisty on a Dell E1505 and really don't want to have to reinstall the complete OS just for these two files.
Thanks in advance for assisting with my incompetence.

---

### Post by spin2cool on 2007-05-09
There's no reason that you should have to reinstall.  You should be able to reinstall the packages for those particular programs.  I'm not at my Ubuntu box right now, but I'd guess that something like this would do the trick.
```

sudo apt-get remove sendmail
sudo apt-get install sendmail

```

---

### Post by bull8042 on 2007-05-09
That is what I thought as well. But that is apparently not the case because the install of postscript fails because of the missing file in init.d.

---

### Post by bull8042 on 2007-05-09
Is there not a single person on here that might offer to email a copy of the 2 files they have on their computer? All of the shell scripts should be the same.

[email]reaton3@gmail.com[/email]

PLEASE.......

---

