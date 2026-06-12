---
title: "[SOLVED] Problem with Synaptic and terminal"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2008-08-16
I have this error message in both Synaptic and the terminal.:-



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Any advice on how to resolve please.:confused:

---

### Post by howefield on 2008-08-16
open a terminal and type 

dpkg --configure -a

Not sure if you need to preface it with sudo...

---

### Post by Dyffo on 2008-08-16
> **howefield said:**
> open a terminal and type 

dpkg --configure -a

Not sure if you need to preface it with sudo...
mike@mike-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
mike@mike-desktop:~$ 

Tried your suggestion, but says I require superuser privilidge !!!!!!!!!!!!! - how do I get this

---

### Post by dje on 2008-08-16
you need to run it with root permission (by preceding the command with sudo) so it should be:
```
sudo dpkg --configure -a
```
also please use the search function in future, there are many many threads on this exact topic ;)

dje

---

### Post by howefield on 2008-08-16
as I said, you may need to preface with sudo, so try

sudo dpkg --configure -a

It will ask you for your password, type it in and hopefully....

---

### Post by Dyffo on 2008-08-16
Thanks Guys problem solved !!!! Sorry about not using the search function - I tried but no results came up - must have entered the wrong question.

---

