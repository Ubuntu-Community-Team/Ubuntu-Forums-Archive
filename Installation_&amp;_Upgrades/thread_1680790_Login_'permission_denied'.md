---
title: "Login 'permission denied'"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by StephaneLenclud on 2011-02-03
Hi,

I did an upgrade from 9.10 to 10.04 LTS. Got a couple of errors towards the end of the process and after reboot I simply cannot login. It keeps giving me 'permission denied' error when I provide the correct password.

I can still login as root using the recovery console. After some quick search on the Internet I tried fiddling with my /etc/gdm/gdm.conf which was not there actually. There was only a backup copy of it in that directory so I copied the backup to /etc/gdm/gdm.conf but that didn't help.

Any suggestion would be appreciated.

Cheers,
S.

---

### Post by ajgreeny on 2011-02-03
You could try a reset of your user password  
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
which may do the job, but if not I can't help any more, I'm afraid.

---

### Post by StephaneLenclud on 2011-02-03
Tried it it does not help. I'm also using PAM btw.

---

### Post by matt_symes on 2011-02-03
Hi

Try adding a new user at the console and then see if you can login as that user at gdm logon screen. Use the adduser command.

There is a way to reset your password to nothing by editing the files directly.

I will see if i can dig out the information for it.

Kind regards

---

### Post by StephaneLenclud on 2011-02-03
Don't worry I'll do a clean install... Thanks for helping though.

---

### Post by matt_symes on 2011-02-03
Hi

That's what i would do. Backup data and clean install. Good luck.

Kind regards

---

