---
title: "deja-dup supports Amazon S3?"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by frankdn on 2011-10-16
11.10 installed fairly smoothly and seems to run fine, and deja-dup looks like a very nice basic backup utility.

But as installed, deja-dup limits me to Ubuntu One.  Nothing against Ubuntu One, but I'd like to configure it to use my Amazon S3 account.  However the GUI does not offer that choice.

How can I configure this?

---

### Post by LinuxT60 on 2011-10-16
You can add it.  You just need to install the [python-boto package]("http://apt.ubuntu.com/p/python-boto")  It should then show up under Backups -> Storage, and will be above Ubuntu One

---

### Post by frankdn on 2011-10-20
Thank you!

(Incidentally, the supplied link to apt.ubuntu does not work with Opera.  The installer dialog does not open.)

---

