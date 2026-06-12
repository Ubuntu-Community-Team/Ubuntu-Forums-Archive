---
title: "[SOLVED] Temporary failure resolving gb.archive.ubuntu.com"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by scbingham on 2013-08-04
Hello All

I keep getting the above error message whenever I try to install or update. I managed to install packages a few hours ago.

Is there anything I can check or change to make sure it's not a problem with my system?

I have a new install of 12.04 server 32 bit.

Any help will be appreciated.

Cheers.

---

### Post by ibjsb4 on 2013-08-04
Please post the output of ..

```
sudo apt-get update
```

---

### Post by scbingham on 2013-08-04
Hi ibjsb4, thanks for responding.

Bit difficult to copy output to laptop, as I cant ssh to server & no gui on server. However, the gist of it is:

Lots of- Err /http://gb.archive.ubuntu.com/ubuntu/dists/etc etc
Lots of- W: Failed to fetch [http://gb.archive.etc](http://gb.archive.etc) etc... Temporary failure resolving security.ubuntu.com & gb.archive.ubuntu.com

---

### Post by scbingham on 2013-08-04
I eventually stumbled across this thread:

[http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem](http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem)

I suggest reading the whole article, as some of the solutions are a bit 'dirty'.

The problem seems to be caused by lock files & missing records for the servers.

Mine seems to be working for the moment but I'm not sure if it's permanent yet. However I'll mark this a solved.

---

