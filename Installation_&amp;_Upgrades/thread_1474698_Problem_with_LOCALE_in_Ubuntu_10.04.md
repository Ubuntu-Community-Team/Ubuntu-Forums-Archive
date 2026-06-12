---
title: "Problem with LOCALE in Ubuntu 10.04"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by dwaynemac on 2010-05-06
I installed Ubuntu 10.04 from scratch.

I'm getting errors with **locale** in several applications. The following is the most common error message:

```

perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TIME = "es_AR.UTF-8",
	LANG = "en_US.utf8"
    are supported and installed on your system.

```

Any clue how to fix this?

---

### Post by dino99 on 2010-05-06
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by dwaynemac on 2010-05-06
no change

---

### Post by dino99 on 2010-05-06
the message talk about a "perl" complaint, is there any others issues ?

look the logs into system admin log viewer, and .xsession-errors (/home)

---

### Post by jits on 2010-05-24
Hi,

Try this: [http://dchua.com/ubuntu-setting-locale-failed-reinstall-packag](http://dchua.com/ubuntu-setting-locale-failed-reinstall-packag)

Jits

---

