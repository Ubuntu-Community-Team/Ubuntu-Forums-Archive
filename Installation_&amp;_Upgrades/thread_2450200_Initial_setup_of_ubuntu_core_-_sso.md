---
title: "Initial setup of ubuntu core - sso"
date: 2020-09-09
forum: Installation &amp; Upgrades
---

### Post by kmlugg on 2020-09-09
Hello,

Newbie: I have recently set up ubuntu core on a nuc following this procedeure: [https://ubuntu.com/download/intel-nuc](https://ubuntu.com/download/intel-nuc). 

I was not prompted for a root/admin user or password. Is all I get remote ssh? Which anyway did not work. Trying to log in remotely with putty I was prompted for a password. I think I got the public/private key right, because when I changed the key on the sso web account, I got a key error message in putty. 

How is this working? Can anyone please explain a newbie the mechanism here?

Thanks in advance. 

Kind regards,

Kyrre

---

### Post by TheFu on 2020-09-09
There isn't any GUI on Ubuntu core. They are meant for embedded devices and if you are completely new to Linux/Unix, it would be a huge battle to begin learning on that platform.

I've not used it for a number of reasons - the mandatory Canonical fingers in access controls is just one issue. When I saw that, I stopped looking any further into the platform.

[https://core.docs.ubuntu.com/en/guides/manage-devices/](https://core.docs.ubuntu.com/en/guides/manage-devices/) seems to have instructions for your question. I'll assume you've seen that guide already to build the image with pre-seed keys already.

The normal methods to setup key-based ssh are well understood between Unix systems. Sounds like Ubuntu Core decided NOT to follow those methods ... or more likely ... to insert themselves in the middle.

Normal ssh setup guide: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Sorry if this isn't helpful.  Perhaps in the next few days someone with direct knowledge will answer.

---

### Post by tea for one on 2020-09-09
> **kmlugg said:**
> Hello,

Newbie: I have recently set up ubuntu core on a nuc following this procedeure: [https://ubuntu.com/download/intel-nuc](https://ubuntu.com/download/intel-nuc). 

I was not prompted for a root/admin user or password. Is all I get remote ssh? Which anyway did not work. Trying to log in remotely with putty I was prompted for a password. I think I got the public/private key right, because when I changed the key on the sso web account, I got a key error message in putty. 

How is this working? Can anyone please explain a newbie the mechanism here?

Thanks in advance. 

Kind regards,

Kyrre

I think that you have been deceived by Ubuntu nomenclature?

The web page you mentioned states:- > There are two install options for the Intel NUC: Ubuntu Core or Ubuntu Desktop This page is for Ubuntu Core.

Did you want to install Ubuntu Desktop, which will allow you to set up users, passwords, add applications etc?

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

