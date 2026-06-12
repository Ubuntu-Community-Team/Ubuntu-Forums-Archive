---
title: "Update Manager Won't Update"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by M3ZuR on 2012-01-03
Hello. I am new to ubuntu and was trying to update the OS and keep getting an "authencation" error saying it requires installation of untrusted packages but wont let me update or install anuyting what so ever. i literally just installed the system

---

### Post by mörgæs on 2012-01-04
Hi, welcome to the fora.

Which release did you install?

What happens if you boot the computer and run 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

one at a time?

---

### Post by M3ZuR on 2012-01-04
its the ubuntu 11.10 and im trying to install the update through the virtualbox. 

should i choose to run the OS as a standalone when i update?

---

### Post by mörgæs on 2012-01-04
Sorry, can't answer that. Have never used Virtualbox.

---

### Post by MAFoElffen on 2012-01-04
> **M3ZuR said:**
> its the ubuntu 11.10 and im trying to install the update through the virtualbox. 

should i choose to run the OS as a standalone when i update?
Start VirtualBox and your virtual Ubuntu... Open Firebox and make sure you have internet connection. Open a terminal session and:
```

sudo apt-get update && sudo apt-get upgrade

```
If it errors, post what that error says.  I'm thinking you either have a corrupt apt-cache or a problem with the Ubuntu authentication keys.

---

### Post by Acharn on 2012-01-23
> **MAFoElffen said:**
> <snip>
```

sudo apt-get update && sudo apt-get upgrade

```
<snip>.
Thank you. I'm not running Virtual Box, but your recommendation solved my problem with updating. Update Manager kept giving me the error message (kernel headers "upstream kernel changes"} but doing it in the terminal worked fine.

---

### Post by gleedadswell on 2012-02-16
Today on several machines running 11.10 I had authentication errors (along the lines of "requires installation of untrusted packages").  One of the machines is running a very fresh (2 days old) install of 11.10 and I haven't messed around with what repositories it looks at, so it would have only been looking at the default ones that are selected after install.

A simple sudo apt-get update solved it, so no real problem.  But this leaves me a bit confused.  Upon starting up wouldn't the update manager invoke apt-get update (possibly after an apt-get clean)?  Why would I need to do this manually?  For people new to Ubuntu this seems likely to cause some frustration.

Also, the default behaviour of update manager in this case seems poor.  It aborts the whole update.  A far better behaviour, especially for noob users, would be for it to do all the trusted updates and then give a list of the updates that didn't happen because of the authentication issues.  If apt-get update is what is needed then a message should be issued to this effect.

---

