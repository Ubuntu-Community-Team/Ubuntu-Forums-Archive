---
title: "Root password"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by satimis on 2006-10-17
Hi folks,

Ubuntu-6.06.1 LAMP server

During installation it did not ask for root password only for adding USER.  I have no way to login as Root to configure the OS and do maintainence.

Please advise.  TIA

B.R.
satimis

---

### Post by aysiu on 2006-10-17
Read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by satimis on 2006-10-17
Hi aysiu,

> Read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

Tks for your link.  I'll test it later on Ubuntu LAMP server.

Furthermore is there any way to read Installation and Configuration document:-

Ubuntu Server Guide
[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

while working on the server to config it rather than running 2 PCs side by side with one PC reading document.

TIA

B.R.
satimis

---

### Post by Kateikyoushi on 2006-10-17
Maybe you could use links (if it is avable) to read the guide from another terminal.

---

### Post by satimis on 2006-10-17
Hi Kateikyoushi,

Tks for your advice.

> Maybe you could use links (if it is avable) to read the guide from another terminal.
You meant on another console?  But .html doc needs X-window.  The server is not yet setup and connected to Internet.

I have no idea whether the LAMP server includes X-window which is not recommended for server because of creating a security hole.  The document is available on .pdf format as well which also requires X-window.

Tks


B.R.
satimis

---

### Post by Jussi Kukkonen on 2006-10-17
links is a text mode browser, no X needed. Reading simple web pages with it (or w3m, since that comes with the basic install, I'm not sure about links) is ok.

But internet is required (unless you copy the file on a USB stick/floppy/CD)...

---

### Post by joff13 on 2006-10-17
```
sudo passwd root
```
enter your password end after the password you want for rot

---

### Post by satimis on 2006-10-18
> **joff13 said:**
> ```
sudo passwd root
```
enter your password end after the password you want for rotNoted with tks.

B.R.
satimis

---

