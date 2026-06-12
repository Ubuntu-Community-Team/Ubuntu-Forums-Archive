---
title: "etter.dns"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by LHYX on 2010-04-18
Hey,
I'm trying to configure my   /usr/share/ettercap/etter.dns
for dns spoofing with ettercap. but when I change the file and try to save it ubuntu says permision deneight :(
Even when I try doing this from the terminal with sudo.
It seems there is know way to change the file.
Any ideas ? :confused:

---

### Post by tom4everitt on 2010-04-18
Yes, some files are even write-protected for sudo. Try running:

sudo chmod u+w /usr/share/ettercap/etter.dns

and then try to edit it. Beware though, since there is probably a reason the file is write protected - probably that it is not normally supposed to be edited. But the more dangerous you live, tbe more you will learn :) (depending how much you depend on the system youre running of course)

---

### Post by LHYX on 2010-04-19
I just had to do this:
sudo gedit /usr/share/ettercap/etter.dns

But thnx anyway :)

---

### Post by tom4everitt on 2010-04-19
Oh, I thought you said it didn't work with sudo from the terminal :P

---

### Post by LHYX on 2010-04-19
Yeah,
I was being stupid :P
I was doing
sudo /usr/share/ettercap/etter.dns

---

