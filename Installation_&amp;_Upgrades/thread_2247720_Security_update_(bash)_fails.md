---
title: "Security update (bash) fails?"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by oygle on 2014-10-09
There was a security update this morning, containing bash and rsyslog. Each time I went to install the message is

**This operation cannot continue since proper authorization was not provided**

usually I'm asked for the password.

---

### Post by oygle on 2014-10-09
Fixed with the following ..

```

sudo apt-get update

sudo apt-get upgrade

```

From [http://ubuntuforums.org/showthread.php?t=2123840&p=12625289#post12625289](http://ubuntuforums.org/showthread.php?t=2123840&p=12625289#post12625289)

---

### Post by oygle on 2014-10-27
Got the same message again this morning. I'm using the above code as a workaround. Is it a bug in Muon ?

---

