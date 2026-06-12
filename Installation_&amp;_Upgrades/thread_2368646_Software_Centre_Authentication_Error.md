---
title: "Software Centre Authentication Error"
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by frustrateduser2 on 2017-08-13
Forgive me if this is a simple fix but i'm incredibly new to linux and ubuntu in general. I have just installed xfce and have installed the ubuntu software center for ease of downloading stuff rather than using apt-get as most files seem to be easier to install that way. However whenever I try and install stuff i get an authentication error saying I don't have permission. Any suggestions?

---

### Post by oldos2er on 2017-08-13
Which version of Ubuntu (or Xubuntu?) are you using?

---

### Post by frustrateduser2 on 2017-08-13
> **oldos2er said:**
> Which version of Ubuntu (or Xubuntu?) are you using?

Hi oldos2er. I'm running Xubuntu Version 4.2

---

### Post by howefield on 2017-08-13
> **frustrateduser2 said:**
> Hi oldos2er. I'm running Xubuntu Version 4.2

What's the output of the terminal command..

```
cat /etc/*-release
```

---

### Post by frustrateduser2 on 2017-08-13
It says the releases is 16.04.3cat /etc/*-releaseDISTRIB_ID=UbuntuDISTRIB_RELEASE=16.04DISTRIB_CODENAME=xenialDISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"NAME="Ubuntu"VERSION="16.04.3 LTS (Xenial Xerus)"ID=ubuntuID_LIKE=debian

---

### Post by frustrateduser2 on 2017-08-13
Have fixed it by running sudo su. and the putting in software-center (in case anyone sees this thread in future)

Thanks for your help guys.

---

### Post by oldos2er on 2017-08-13
You probably should use sudo -H or sudo -i instead of sudo su. sudo -H (or -i) preserves your user's environment when it runs, as opposed to sudo su which uses root's environment. Further explanation here: [https://askubuntu.com/questions/515198/how-to-run-terminal-as-root](https://askubuntu.com/questions/515198/how-to-run-terminal-as-root)

If your question is answered please mark the thread 'Solved' under Thread Tools at the top of the page. Thanks!

---

