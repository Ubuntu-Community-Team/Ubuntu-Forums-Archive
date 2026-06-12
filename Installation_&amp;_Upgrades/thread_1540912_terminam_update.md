---
title: "terminam update"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by mirinamulhaq on 2010-07-28
hello
i have recently installed karmic koala.i wanted to upgrade it through terminal,but it is always showing me error as unable to connect to archive.ubuntu.com with some numbers in bracket like (189. etc).synaptic and and my internet connection is working fine
how can i solve this problem

---

### Post by zvacet on 2010-07-28
Why don´t you try to upgrade with update manager?

---

### Post by mirinamulhaq on 2010-07-28
because i wantto install somesoftwares through terminal,and i am suffering this problem.
second thing is that i wanted to install artha (dictionary) through software manager but again there is dependency problem.

---

### Post by robinzolb on 2010-07-29
I try  to upgrade with update manager, but i get a error:A signature verification error occurred.what's problem?

---

### Post by mirinamulhaq on 2010-07-29
i m a ne bie to it ,i dont know about it

---

### Post by zvacet on 2010-07-29
@ **mirinamulhaq**

Are you trying to get Karmic up to date or you want to upgrade to Lucid?

```
sudo apt-get update && sudo apt-get upgrade
```
 
Post output here.


@ **robinzolb**

```
sudo apt-get update
```

---

### Post by mirinamulhaq on 2010-07-30
i am trying to update my karmic(not upgrade).although i am able to browse internet and open archive .ubuntu.com from mozilla ,but when i am trying to update through terminal by doing sudo apt-get update,then after 5 to 7 minutes i am getting an error reading unable to connect to archive.ubuntu.com(although i am able to open it through my browser)

---

