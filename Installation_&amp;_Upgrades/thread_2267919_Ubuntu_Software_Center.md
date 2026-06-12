---
title: "Ubuntu Software Center"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by yomen-tohmaz on 2015-03-04
Hey everyone I don't know why this is happening but everytime I open Ubuntu Software Center I get this error.

"New software can't be installed, because there is a problem with the software currently installed.  Do you want to repair this problem?"

I click repair but that doesn't work.  I followed another guide on how to  fix this but that didn't work either.  Also I'm using Ubuntu 14.04.

Thanks for any help.

Yomen Tohmaz

---

### Post by bapoumba on 2015-03-05
Hello,

please open a terminal and paste the outputs to these commands :
```
cat -n /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

```

In case you are not familiar with the terminal, you will be prompted for your password after the first command, you wont see any feedback while typing it. That is normal.

---

