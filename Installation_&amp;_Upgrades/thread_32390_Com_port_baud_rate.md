---
title: "Com port baud rate??"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2005-05-07
Having a problem with ttyS0.  In Hoary 5.04, how do I set serial com port parameters like baud rate, bits, etc?

---

### Post by alastair on 2005-05-08
Have a look at "setserial".

---

### Post by ubuntu1sttimer on 2005-05-08
[QUOTE=alastair]Have a look at "setserial".[/QUOTE]

That was what I thought but when I tried it, here is what I got:

root@ubuntu:/ # sudo setserial /dev/ttyS0
sudo: set serial: command not found

Got the same when I tried it without sudo.  Can echo commands to the modem at /dev/ttyS0 ok.  Thus, my question.  Have used setserial when trying to get Debian up and running but no setserial in ubuntu unless I am doing something wrong.

---

### Post by alastair on 2005-05-09
"... unless I am doing something wrong."

Is it installed?

sudo apt-get install setserial

---

