---
title: "Chrome installation problem"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by bacchus1903 on 2012-09-22
Hi 

I new to Linux, I try to install Chrome browser (the ubuntu version) and I have the following message:
Cannot install 'libatk1.0-0:i386'

Can you please give me a idea for solution


Thanks in advance

Jules:KS

---

### Post by raja.genupula on 2012-09-23
```
sudo dpkg -r libatk1.0-0:i386
sudo apt-get update
sudo apt-get install -f 
```

try them one by one .

---

### Post by vasa1 on 2012-09-23
> **bacchus1903 said:**
> ... I try to install Chrome browser (the ubuntu version) ...
From where did you try to install it?
Did you try from [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
You will get the latest version from there. Also, the set-up procedure will add a ppa for you that ensures that you will receive all updates to the browser in a prompt manner.

---

### Post by bacchus1903 on 2012-09-23
Thanks

The link for Chrome works very well, I dont understand why my first link
found was not working

:lolflag:

---

### Post by vasa1 on 2012-09-23
> **bacchus1903 said:**
> ...I dont understand why my first link
found was not working
... 
If you would be kind enough to post the link that gave you the error someone may be able to explain why it didn't work.

---

