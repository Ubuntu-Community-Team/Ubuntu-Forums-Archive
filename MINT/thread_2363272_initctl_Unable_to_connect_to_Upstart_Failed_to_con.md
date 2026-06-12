---
title: "initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstar"
date: 2017-06-08
forum: MINT
---

### Post by mulcahy911 on 2017-06-08
I boot up to the login screen fine. Enter username and pass, login then receive the following error message.

[https://pastebin.com/vNsb72BF](https://pastebin.com/vNsb72BF)
<script src="https://pastebin.com/embed_js/vNsb72BF"></script>

Any ideas on what to do?

Forgot to mention I'm using the latest version of Ubuntu, fully updated.

---

### Post by howefield on 2017-06-08
What's the output of 

```
cat /etc/*-release
```

---

### Post by mulcahy911 on 2017-06-08
Output was: No such file or directory

---

### Post by howefield on 2017-06-08
> **mulcahy911 said:**
> No such file of directory

Sure you didn't make a typo, can you copy/paste the terminal input/output back here ?

---

### Post by mulcahy911 on 2017-06-08
Sorry was a typo

```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18
DISTRIB_CODENAME Sarah
Name="Linux Mint"
VERSION="18 (Sarah)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 18"
VERSION_ID="18"
HOME_URL:"http://www.linuxmint.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/linuxmint"
UBUNTU_CODENAME=xenial
```

---

### Post by howefield on 2017-06-08
Ok, thanks for that, thread moved to the "*MINT*" forum where those who know it better can respond.

---

