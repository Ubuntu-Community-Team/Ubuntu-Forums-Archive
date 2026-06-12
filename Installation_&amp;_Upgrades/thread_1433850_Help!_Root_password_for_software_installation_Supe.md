---
title: "Help! Root password for software installation? Superuser?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by beet133 on 2010-03-19
Hi: I've recently had Ubuntu installed onto my Acer laptop after everything went haywire with it (a long story, which I won't bore you with).  I've used ubuntu for about a year now, and never had this problem before:

I can install programs through the terminal, using sudo apt-get and my user password, but when I try to install anything through the Software Centre I get a message (see attached screenshot) asking for the root password for the 'superuser'.  Now, I don't remember setting such a password, and if I did, I will have used on of my regular passwords (none of which work here).  What's going on, and how can I solve the problem?

Thanks!

---

### Post by oldos2er on 2010-03-19
Does it work if you type in your user password?

---

### Post by Chesamo on 2010-03-19
That's very odd, considering Ubuntu disables root by default (and instructions to enable it are against the rules of this forum). I'm with oldos, have you tried your own password?

---

### Post by sisco311 on 2010-03-19
> **beet133 said:**
> Hi: I've recently had Ubuntu installed onto my Acer laptop after everything went haywire with it (a long story, which I won't bore you with).  I've used ubuntu for about a year now, and never had this problem before:

I can install programs through the terminal, using sudo apt-get and my user password, but when I try to install anything through the Software Centre I get a message (see attached screenshot) asking for the root password for the 'superuser'.  Now, I don't remember setting such a password, and if I did, I will have used on of my regular passwords (none of which work here).  What's going on, and how can I solve the problem?

Thanks!

don't reboot or log out. add your user to the admin group:
```
sudo gpasswd -a **username** admin
```
replace **username** with your login name. 

If you did reboot or log out, then boot in recovery mode and add your user to the admin group: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If the above suggestions did not work then please post the output of:
```
cat /etc/polkit-1/localauthority*/*
```
and```
id
```

---

### Post by beet133 on 2010-03-21
@ sisko311:

Thank you, the first of those suggestions worked!

beet133

---

### Post by beet133 on 2010-03-21
Sorry, sis_c_o311...

---

